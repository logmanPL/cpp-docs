---
title: "Compiler Options Macros"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compiler options, macros"
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
caps.latest.revision: 13
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
# Compiler Options Macros
These macros control specific compiler features.  
  
|||  
|-|-|  
|[_ATL_ALL_WARNINGS](../Topic/_ATL_ALL_WARNINGS.md)|A symbol which enables errors in projects converted from previous versions of ATL.|  
|[_ATL_APARTMENT_THREADED](../Topic/_ATL_APARTMENT_THREADED.md)|Define if one or more of your objects use apartment threading.|  
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](../Topic/_ATL_CSTRING_EXPLICIT_CONSTRUCTORS.md)|Makes certain `CString` constructors explicit, preventing any unintentional conversions.|  
|[_ATL_ENABLE_PTM_WARNING](../Topic/_ATL_ENABLE_PTM_WARNING.md)|Define this macro in order to use C++ standard compliant syntax, which generates the C4867 compiler error when a non standard syntax is used to initialize a pointer to a member function.|  
|[_ATL_FREE_THREADED](../Topic/_ATL_FREE_THREADED.md)|Define if one or more of your objects use free or neutral threading.|  
|[_ATL_MULTI_THREADED](../Topic/_ATL_MULTI_THREADED.md)|A symbol that indicates the project will have objects that are marked as Both, Free or Neutral. The macro [_ATL_FREE_THREADED](../Topic/_ATL_FREE_THREADED.md) should be used instead.|  
|[_ATL_NO_AUTOMATIC_NAMESPACE](../Topic/_ATL_NO_AUTOMATIC_NAMESPACE.md)|A symbol which prevents the default use of namespace as ATL.|  
|[_ATL_NO_COM_SUPPORT](../Topic/_ATL_NO_COM_SUPPORT.md)|A symbol which prevents COM-related code from being compiled with your project.|  
|[ATL_NO_VTABLE](../Topic/ATL_NO_VTABLE.md)|A symbol that prevents the vtable pointer from being initialized in the class's constructor and destructor.|  
|[ATL_NOINLINE](../Topic/ATL_NOINLINE.md)|A symbol that indicates a function should not be inlined.|  
|[_ATL_SINGLE_THREADED](../Topic/_ATL_SINGLE_THREADED.md)|Define if all of your objects use the single threading model.|  
  
##  <a name="_atl_all_warnings"></a>  _ATL_ALL_WARNINGS  
 A symbol which enables errors in projects converted from previous versions of ATL.  
  
```
#define _ATL_ALL_WARNINGS
```  
  
### Remarks  
 Before Visual C++ .NET 2002, ATL disabled a lot of warnings and left them disabled so that they never showed up in user code. Specifically:  
  
-   C4127 conditional expression is constant  
  
-   C4786 'identifier' : identifier was truncated to 'number' characters in the debug information  
  
-   C4201 nonstandard extension used : nameless struct/union  
  
-   C4103 'filename' : used #pragma pack to change alignment  
  
-   C4291 'declaration' : no matching operator delete found; memory will not be freed if initialization throws an exception  
  
-   C4268 'identifier' : 'const' static/global data initialized with compiler generated default constructor fills the object with zeros  
  
-   C4702 unreachable code  
  
 In projects converted from previous versions, these warnings are still disabled by the libraries headers.  
  
 By adding the following line to the stdafx.h file before including libraries headers, this behavior can be changed.  
  
 [!code[NVC_ATL_Utilities#97](../atl/codesnippet/CPP/compiler-options-macros_1.h)]  
  
 If this `#define` is added, the ATL headers are careful to preserve the state of these warnings so that they are not disabled globally (or if the user explicitly disables individual warnings, not to enable them).  
  
 New projects generated with Visual C++ .NET 2002 will have this `#define` set in stdafx.h by default.  
  
##  <a name="_atl_apartment_threaded"></a>  _ATL_APARTMENT_THREADED  
 Define if one or more of your objects use apartment threading.  
  
```
_ATL_APARTMENT_THREADED
```  
  
### Remarks  
 Specifies apartment threading. See [Specifying the Project's Threading Model](../atl/specifying-the-threading-model-for-a-project--atl-.md) for other threading options, and [Options, ATL Simple Object Wizard](../atl/options--atl-simple-object-wizard.md) for a description of the threading models available for an ATL object.  
  
##  <a name="_atl_cstring_explicit_constructors"></a>  _ATL_CSTRING_EXPLICIT_CONSTRUCTORS  
 Makes certain `CString` constructors explicit, preventing any unintentional conversions.  
  
```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```  
  
### Remarks  
 When this is defined, all CString constructors that take a single parameter are compiled with the explicit keyword, which prevents implicit conversions of input arguments. This means for example, that when _UNICODE is defined, if you attempt use a char* string as a CString constructor argument, a compiler error will result. Use this macro in situations where you need to prevent implicit conversions between narrow and wide string types.  
  
 By using the _T macro on all constructor string arguments, you can define _ATL_CSTRING_EXPLICIT_CONSTRUCTORS and avoid compile errors regardless of whether _UNICODE is defined.  
  
##  <a name="_atl_enable_ptm_warning"></a>  _ATL_ENABLE_PTM_WARNING  
 Define this macro in order to force the use of ANSI C++ standard-compliant syntax for pointer to member functions. Using this macro will cause the C4867 compiler error to be generated when non-standard syntax is used to initialize a pointer to a member function.  
  
```
#define _ATL_ENABLE_PTM_WARNING
```  
  
### Remarks  
 The ATL and MFC libraries have been changed to match the Visual C++ compiler's improved standard C++ compliance. According to the ANSI C++ standard, the syntax of a pointer to a class member function should be `&CMyClass::MyFunc`.  
  
 When [_ATL_ENABLE_PTM_WARNING](../Topic/_ATL_ENABLE_PTM_WARNING.md) is not defined (the default case), ATL/MFC disables the C4867 error in macro maps (notably message maps) so that code that was created in earlier versions can continue to build as before. If you define **_ATL_ENABLE_PTM_WARNING**, your code should be C++ standard compliant.  
  
 However, the non-standard form has been deprecated, so you need to move existing code to C++ standard compliant syntax. For example, the following:  
  
 [!code[NVC_MFCListView#14](../atl/codesnippet/CPP/compiler-options-macros_2.cpp)]  
  
 Should be changed to:  
  
 [!code[NVC_MFCListView#11](../atl/codesnippet/CPP/compiler-options-macros_3.cpp)]  
  
 Note that for map macros that add the '&' character, you should not add it again in your code.  
  
##  <a name="_atl_free_threaded"></a>  _ATL_FREE_THREADED  
 Define if one or more of your objects use free or neutral threading.  
  
```
_ATL_FREE_THREADED
```  
  
### Remarks  
 Specifies free threading. Free threading is equivalent to a multithread apartment model. See [Specifying the Project's Threading Model](../atl/specifying-the-threading-model-for-a-project--atl-.md) for other threading options, and [Options, ATL Simple Object Wizard](../atl/options--atl-simple-object-wizard.md) for a description of the threading models available for an ATL object.  
  
##  <a name="_atl_multi_threaded"></a>  _ATL_MULTI_THREADED  
 A symbol that indicates the project will have objects that are marked as Both, Free or Neutral.  
  
```
_ATL_MULTI_THREADED
```  
  
### Remarks  
 If this symbol is defined, ATL will pull in code that will correctly synchronize access to global data. New code should use the equivalent macro [_ATL_FREE_THREADED](../Topic/_ATL_FREE_THREADED.md) instead.  
  
##  <a name="_atl_no_automatic_namespace"></a>  _ATL_NO_AUTOMATIC_NAMESPACE  
 A symbol which prevents the default use of namespace as ATL.  
  
```
_ATL_NO_AUTOMATIC_NAMESPACE
```  
  
### Remarks  
 If this symbol is not defined, including atlbase.h will perform **using namespace ATL** by default, which may lead to naming conflicts. To prevent this, define this symbol.  
  
##  <a name="_atl_no_com_support"></a>  _ATL_NO_COM_SUPPORT  
 A symbol which prevents COM-related code from being compiled with your project.  
  
```
_ATL_NO_COM_SUPPORT
```  
  
##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE  
 A symbol that prevents the vtable pointer from being initialized in the class's constructor and destructor.  
  
```
ATL_NO_VTABLE
```  
  
### Remarks  
 If the vtable pointer is prevented from being initialized in the class's constructor and destructor, the linker can eliminate the vtable and all of the functions to which it points. Expands to **__declspec(novtable)**.  
  
### Example  
 [!code[NVC_ATL_COM#53](../atl/codesnippet/CPP/compiler-options-macros_4.h)]  
  
##  <a name="atl_noinline"></a>  ATL_NOINLINE  
 A symbol that indicates a function should not be inlined.  
  
```
    ATL_NOINLINE  inline
    myfunction
  {
...
 }
```  
  
### Parameters  
 *myfunction*  
 The function that should not be inlined.  
  
### Remarks  
 Use this symbol if you want to ensure a function does not get inlined by the compiler, even though it must be declared as inline so that it can be placed in a header file. Expands to **__declspec(noinline)**.  
  
##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED  
 Define if all of your objects use the single threading model  
  
```
_ATL_SINGLE_THREADED
```  
  
### Remarks  
 Specifies that the object always runs in the primary COM thread. See [Specifying the Project's Threading Model](../atl/specifying-the-threading-model-for-a-project--atl-.md) for other threading options, and [Options, ATL Simple Object Wizard](../atl/options--atl-simple-object-wizard.md) for a description of the threading models available for an ATL object.  
  
## See Also  
 [Macros](../atl/atl-macros.md)
