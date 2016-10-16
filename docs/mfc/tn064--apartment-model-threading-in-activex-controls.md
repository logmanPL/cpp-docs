---
title: "TN064: Apartment-Model Threading in ActiveX Controls"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "vc.controls.activex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE controls, container support"
  - "containers [C++], multithreaded"
  - "TN064"
  - "multithread container"
  - "apartment model threading"
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
caps.latest.revision: 7
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# TN064: Apartment-Model Threading in ActiveX Controls
> [!NOTE]
>  The following technical note has not been updated since it was first included in the online documentation. As a result, some procedures and topics might be out of date or incorrect. For the latest information, it is recommended that you search for the topic of interest in the online documentation index.  
  
 This technical note explains how to enable apartment-model threading in an ActiveX control. Note that apartment-model threading is only supported in Visual C++ versions 4.2 or later.  
  
## What Is Apartment-Model Threading?  
 The apartment model is an approach to supporting embedded objects, such as ActiveX controls, within a multithreaded container application. Although the application may have multiple threads, each instance of an embedded object will be assigned to one "apartment," which will execute on only one thread. In other words, all calls into an instance of a control will happen on the same thread.  
  
 However, different instances of the same type of control may be assigned to different apartments. So, if multiple instances of a control share any data in common (for example, static or global data), then access to this shared data will need to be protected by a synchronization object, such as a critical section.  
  
 For complete details on the apartment threading model, please see [Processes and Threads](http://msdn.microsoft.com/library/windows/desktop/ms684841) in the *OLE Programmer's Reference*.  
  
## Why Support Apartment-Model Threading?  
 Controls that support apartment-model threading can be used in multithreaded container applications that also support the apartment model. If you do not enable apartment-model threading, you will limit the potential set of containers in which your control could be used.  
  
 Enabling apartment-model threading is easy for most controls, particularly if they have little or no shared data.  
  
## Protecting Shared Data  
 If your control uses shared data, such as a static member variable, access to that data should be protected with a critical section to prevent more than one thread from modifying the data at the same time. To set up a critical section for this purpose, declare a static member variable of class `CCriticalSection` in your control's class. Use the `Lock` and **Unlock** member functions of this critical section object wherever your code accesses the shared data.  
  
 Consider, for example, a control class that needs to maintain a string that is shared by all instances. This string can be maintained in a static member variable and protected by a critical section. The control's class declaration would contain the following:  
  
```  
class CSampleCtrl : public COleControl  
{  
    ...  
    static CString _strShared;  
    static CCriticalSection _critSect;  
};  
```  
  
 The implementation for the class would include definitions for these variables:  
  
```  
int CString CSampleCtrl::_strShared;  
CCriticalSection CSampleCtrl::_critSect;  
```  
  
 Access to the `_strShared` static member can then be protected by the critical section:  
  
```  
void CSampleCtrl::SomeMethod()  
{  
    _critSect.Lock();  
    if (_strShared.Empty())  
        _strShared = "<text>";  
    _critSect.Unlock();  
    ...  
}  
```  
  
## Registering an Apartment-Model-Aware Control  
 Controls that support apartment-model threading should indicate this capability in the registry, by adding the named value "ThreadingModel" with a value of "Apartment" in their class ID registry entry under the *class id*\\**InprocServer32** key. To cause this key to be automatically registered for your control, pass the `afxRegApartmentThreading` flag in the sixth parameter to `AfxOleRegisterControlClass`:  
  
```  
BOOL CSampleCtrl::CSampleCtrlFactory::UpdateRegistry(BOOL bRegister)  
{  
    if (bRegister)  
        return AfxOleRegisterControlClass(  
            AfxGetInstanceHandle(),  
            m_clsid,  
            m_lpszProgID,  
            IDS_SAMPLE,  
            IDB_SAMPLE,  
            afxRegApartmentThreading,  
            _dwSampleOleMisc,  
            _tlid,  
            _wVerMajor,  
            _wVerMinor);  
    else  
        return AfxOleUnregisterClass(m_clsid, m_lpszProgID);  
}  
```  
  
 If your control project was generated by ControlWizard in Visual C++ version 4.1 or later, this flag will already be present in your code. No changes are necessary to register the threading model.  
  
 If your project was generated by an earlier version of ControlWizard, your existing code will have a Boolean value as the sixth parameter. If the existing parameter is TRUE, change it to `afxRegInsertable | afxRegApartmentThreading`. If the existing parameter is FALSE, change it to `afxRegApartmentThreading`.  
  
 If your control does not follow the rules for apartment-model threading, you must not pass `afxRegApartmentThreading` in this parameter.  
  
## See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)