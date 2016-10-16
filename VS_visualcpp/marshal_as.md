---
title: "marshal_as"
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
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
caps.latest.revision: 17
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
# marshal_as
This method converts data between native and managed environments.  
  
## Syntax  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### Parameters  
 [in] `input`  
 The value that you want to marshal to a `To_Type` variable.  
  
## Return Value  
 A variable of type `To_Type` that is the converted value of `input`.  
  
## Remarks  
 This method is a simplified way to convert data between native and managed types. To determine what data types are supported, see [Overview of Marshaling in C++](../VS_visualcpp/Overview-of-Marshaling-in-C--.md). Some data conversions require a context. You can convert those data types by using the [marshal_context Class](../VS_visualcpp/marshal_context-Class.md).  
  
 If you try to marshal a pair of data types that are not supported, `marshal_as` will generate an error [C4996](../VS_visualcpp/Compiler-Warning--level-3--C4996.md) at compile time. Read the message supplied with this error for more information. The `C4996` error can be generated for more than just deprecated functions. One example of this is trying to marshal a pair of data types that are not supported.  
  
 The marshaling library consists of several header files. Any conversion requires only one file, but you can include additional files if you need to for other conversions. To see which conversions are associated with which files, look in the table in `Marshaling Overview`. Regardless of what conversion you want to do, the namespace requirement is always in effect.  
  
## Example  
 This example marshals from a `const char*` to a `System::String` variable type.  
  
```  
// marshal_as_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   const char* message = "Test String to Marshal";  
   String^ result;  
   result = marshal_as<String^>( message );  
   return 0;  
}  
```  
  
## Requirements  
 **Header file:** <msclr\marshal.h>, <msclr\marshal_windows.h>, <msclr\marshal_cppstd.h>, or <msclr\marshal_atl.h>  
  
 **Namespace:** msclr::interop  
  
## See Also  
 [Overview of Marshaling in C++](../VS_visualcpp/Overview-of-Marshaling-in-C--.md)   
 [marshal_context Class](../VS_visualcpp/marshal_context-Class.md)