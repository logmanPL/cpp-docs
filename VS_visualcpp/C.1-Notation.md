---
title: "C.1 Notation"
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
ms.topic: article
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
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
# C.1 Notation
The grammar rules consist of the name for a non-terminal, followed by a colon, followed by replacement alternatives on separate lines.  
  
 The syntactic expression termopt indicates that the term is optional within the replacement.  
  
 The syntactic expression *term*optseq is equivalent to *term-seq*opt with the following additional rules:  
  
 *term-seq* :  
  
 *term*  
  
 *term-seq term*  
  
 *term-seq* , *term*