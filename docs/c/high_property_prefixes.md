---
title: "high_property_prefixes"
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
  - "high_property_prefixes"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "high_property_prefixes attribute"
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
caps.latest.revision: 4
ms.author: "corob"
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
# high_property_prefixes
**C++ Specific**  
  
 Specifies alternate prefixes for three property methods.  
  
## Syntax  
  
```  
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### Parameters  
 `GetPrefix`  
 Prefix to be used for the **propget** methods.  
  
 `PutPrefix`  
 Prefix to be used for the **propput** methods.  
  
 `PutRefPrefix`  
 Prefix to be used for the **propputref** methods.  
  
## Remarks  
 By default, high-level error-handling **propget**, **propput**, and **propputref** methods are exposed by member functions named with prefixes **Get**, `Put`, and **PutRef**, respectively.  
  
 **END C++ Specific**  
  
## See Also  
 [#import Attributes](../c/sharpimport-attributes--c---.md)   
 [#import Directive](../c/sharpimport-directive--c---.md)