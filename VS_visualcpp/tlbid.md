---
title: "tlbid"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
  - C
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
caps.latest.revision: 4
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
# tlbid
**C++ Specific**  
  
 Allows for loading libraries other than the primary type library.  
  
## Syntax  
  
```  
tlbid(number)  
```  
  
#### Parameters  
 `number`  
 The number of the type library in `filename`.  
  
## Remarks  
 If multiple type libraries are built into a single DLL, it possible to load libraries other than the primary type library by using `tlbid`.  
  
 For example:  
  
```  
#import <MyResource.dll> tlbid(2)  
```  
  
 is equivalent to:  
  
```  
LoadTypeLib("MyResource.dll\\2");  
```  
  
 **END C++ Specific**  
  
## See Also  
 [#import Attributes](../VS_visualcpp/#import-Attributes--C---.md)   
 [#import Directive](../VS_visualcpp/#import-Directive--C---.md)