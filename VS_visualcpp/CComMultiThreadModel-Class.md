---
title: "CComMultiThreadModel Class"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
caps.latest.revision: 14
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# CComMultiThreadModel Class
`CComMultiThreadModel` provides thread-safe methods for incrementing and decrementing the value of a variable.  
  
## Syntax  
  
```  
class CComMultiThreadModel  
```  
  
## Members  
  
### Public Typedefs  
  
|Name|Description|  
|----------|-----------------|  
|[CComMultiThreadModel::AutoCriticalSection](../Topic/CComMultiThreadModel::AutoCriticalSection.md)|References class [CComAutoCriticalSection](../VS_visualcpp/CComAutoCriticalSection-Class.md).|  
|[CComMultiThreadModel::CriticalSection](../Topic/CComMultiThreadModel::CriticalSection.md)|References class [CComCriticalSection](../VS_visualcpp/CComCriticalSection-Class.md).|  
|[CComMultiThreadModel::ThreadModelNoCS](../Topic/CComMultiThreadModel::ThreadModelNoCS.md)|References class [CComMultiThreadModelNoCS](../VS_visualcpp/CComMultiThreadModelNoCS-Class.md).|  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CComMultiThreadModel::Decrement](../Topic/CComMultiThreadModel::Decrement.md)|(Static) Decrements the value of the specified variable in a thread-safe manner.|  
|[CComMultiThreadModel::Increment](../Topic/CComMultiThreadModel::Increment.md)|(Static) Increments the value of the specified variable in a thread-safe manner.|  
  
## Remarks  
 Typically, you use `CComMultiThreadModel` through one of two `typedef` names, either [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) or [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md). The class referenced by each `typedef` depends on the threading model used, as shown in the following table:  
  
|typedef|Single threading|Apartment threading|Free threading|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S= `CComSingleThreadModel`; M= `CComMultiThreadModel`  
  
 `CComMultiThreadModel` itself defines three `typedef` names. `AutoCriticalSection` and `CriticalSection` reference classes that provide methods for obtaining and releasing ownership of a critical section. `ThreadModelNoCS` references class [CComMultiThreadModelNoCS](../VS_visualcpp/CComMultiThreadModelNoCS-Class.md).  
  
## Requirements  
 **Header:** atlbase.h  
  
##  <a name="ccommultithreadmodel__autocriticalsection"></a>  CComMultiThreadModel::AutoCriticalSection  
 When using `CComMultiThreadModel`, the `typedef` name `AutoCriticalSection` references class [CComAutoCriticalSection](../VS_visualcpp/CComAutoCriticalSection-Class.md), which provides methods for obtaining and releasing ownership of a critical section object.  
  
```  
typedef CComAutoCriticalSection AutoCriticalSection;  
```  
  
### Remarks  
 [CComSingleThreadModel](../VS_visualcpp/CComSingleThreadModel-Class.md) and [CComMultiThreadModelNoCS](../VS_visualcpp/CComMultiThreadModelNoCS-Class.md) also contain definitions for `AutoCriticalSection`. The following table shows the relationship between the threading model class and the critical section class referenced by `AutoCriticalSection`:  
  
|Class defined in|Class referenced|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 In addition to `AutoCriticalSection`, you can use the `typedef` name [CriticalSection](../Topic/CComMultiThreadModel::CriticalSection.md). You should not specify `AutoCriticalSection` in global objects or static class members if you want to eliminate the CRT startup code.  
  
### Example  
 The following code is modeled after [CComObjectRootEx](../VS_visualcpp/CComObjectRootEx-Class.md), and demonstrates `AutoCriticalSection` being used in a threading environment.  
  
 [!CODE [NVC_ATL_COM#36](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_COM#36)]  
  
 The following tables show the results of the `InternalAddRef` and `Lock` methods, depending on the **ThreadModel** template parameter and the threading model used by the application:  
  
### ThreadModel = CComObjectThreadModel  
  
|Method|Single or Apartment Threading|Free Threading|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|The increment is not thread-safe.|The increment is thread-safe.|  
|`Lock`|Does nothing; there is no critical section to lock.|The critical section is locked.|  
  
### ThreadModel = CComObjectThreadModel::ThreadModelNoCS  
  
|Method|Single or Apartment Threading|Free Threading|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|The increment is not thread-safe.|The increment is thread-safe.|  
|`Lock`|Does nothing; there is no critical section to lock.|Does nothing; there is no critical section to lock.|  
  
##  <a name="ccommultithreadmodel__criticalsection"></a>  CComMultiThreadModel::CriticalSection  
 When using `CComMultiThreadModel`, the `typedef` name `CriticalSection` references class [CComCriticalSection](../VS_visualcpp/CComCriticalSection-Class.md), which provides methods for obtaining and releasing ownership of a critical section object.  
  
```  
typedef CComCriticalSection CriticalSection;  
```  
  
### Remarks  
 [CComSingleThreadModel](../VS_visualcpp/CComSingleThreadModel-Class.md) and [CComMultiThreadModelNoCS](../VS_visualcpp/CComMultiThreadModelNoCS-Class.md) also contain definitions for `CriticalSection`. The following table shows the relationship between the threading model class and the critical section class referenced by `CriticalSection`:  
  
|Class defined in|Class referenced|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 In addition to `CriticalSection`, you can use the `typedef` name [AutoCriticalSection](../Topic/CComMultiThreadModel::AutoCriticalSection.md). You should not specify `AutoCriticalSection` in global objects or static class members if you want to eliminate the CRT startup code.  
  
### Example  
 See [CComMultiThreadModel::AutoCriticalSection](../Topic/CComMultiThreadModel::AutoCriticalSection.md).  
  
##  <a name="ccommultithreadmodel__decrement"></a>  CComMultiThreadModel::Decrement  
 This static function calls the Win32 function [InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580), which decrements the value of the variable pointed to by `p`.  
  
```  
static ULONG WINAPI Decrement(    LPLONG p ) throw ();  
```  
  
### Parameters  
 `p`  
 [in] Pointer to the variable to be decremented.  
  
### Return Value  
 If the result of the decrement is 0, then `Decrement` returns 0. If the result of the decrement is nonzero, the return value is also nonzero but may not equal the result of the decrement.  
  
### Remarks  
 **InterlockedDecrement** prevents more than one thread from simultaneously using this variable.  
  
##  <a name="ccommultithreadmodel__increment"></a>  CComMultiThreadModel::Increment  
 This static function calls the Win32 function [InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614), which increments the value of the variable pointed to by `p`.  
  
```  
static ULONG WINAPI Increment(    LPLONG p ) throw ();  
```  
  
### Parameters  
 `p`  
 [in] Pointer to the variable to be incremented.  
  
### Return Value  
 If the result of the increment is 0, then **Increment** returns 0. If the result of the increment is nonzero, the return value is also nonzero but may not equal the result of the increment.  
  
### Remarks  
 **InterlockedIncrement** prevents more than one thread from simultaneously using this variable.  
  
##  <a name="ccommultithreadmodel__threadmodelnocs"></a>  CComMultiThreadModel::ThreadModelNoCS  
 When using `CComMultiThreadModel`, the `typedef` name `ThreadModelNoCS` references class [CComMultiThreadModelNoCS](../VS_visualcpp/CComMultiThreadModelNoCS-Class.md).  
  
```  
typedef CComMultiThreadModelNoCS ThreadModelNoCS;  
```  
  
### Remarks  
 `CComMultiThreadModelNoCS` provides thread-safe methods for incrementing and decrementing a variable; however, it does not provide a critical section.  
  
 [CComSingleThreadModel](../VS_visualcpp/CComSingleThreadModel-Class.md) and `CComMultiThreadModelNoCS` also contain definitions for `ThreadModelNoCS`. The following table shows the relationship between the threading model class and the class referenced by `ThreadModelNoCS`:  
  
|Class defined in|Class referenced|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### Example  
 See [CComMultiThreadModel::AutoCriticalSection](../Topic/CComMultiThreadModel::AutoCriticalSection.md).  
  
## See Also  
 [CComSingleThreadModel Class](../VS_visualcpp/CComSingleThreadModel-Class.md)   
 [CComAutoCriticalSection Class](../VS_visualcpp/CComAutoCriticalSection-Class.md)   
 [CComCriticalSection Class](../VS_visualcpp/CComCriticalSection-Class.md)   
 [Class Overview](../VS_visualcpp/ATL-Class-Overview.md)