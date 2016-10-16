---
title: "Compiler Error C2581"
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
ms.topic: error-reference
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
caps.latest.revision: 10
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
# Compiler Error C2581
'type' : static 'operator =' function is illegal  
  
 The assignment (`=`) operator is incorrectly declared as `static`. Assignment operators cannot be `static`. For more information, see [User-Defined Operators (C++/CLI)](../VS_visualcpp/User-Defined-Operators--C---CLI-.md).  
  
## Example  
 The following sample generates C2581.  
  
```  
// C2581.cpp  
// compile with: /clr /c  
ref struct Y {  
   static Y ^ operator = (Y^ me, int i);   // C2581  
   Y^ operator =(int i);   // OK  
};  
```