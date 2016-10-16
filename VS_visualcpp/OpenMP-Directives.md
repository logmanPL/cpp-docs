---
title: "OpenMP Directives"
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
ms.assetid: 0562c263-344c-466d-843e-de830d918940
caps.latest.revision: 7
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
# OpenMP Directives
Provides links to directives used in the OpenMP API.  
  
 Visual C++ supports the following OpenMP directives:  
  
|Directive|Description|  
|---------------|-----------------|  
|[atomic](../VS_visualcpp/atomic.md)|Specifies that a memory location that will be updated atomically.|  
|[barrier](../VS_visualcpp/barrier.md)|Synchronizes all threads in a team; all threads pause at the barrier, until all threads execute the barrier.|  
|[critical](../VS_visualcpp/critical.md)|Specifies that code is only executed on one thread at a time.|  
|[flush](../VS_visualcpp/flush--OpenMP-.md)|Specifies that all threads have the same view of memory for all shared objects.|  
|[for](../VS_visualcpp/for--OpenMP-.md)|Causes the work done in a for loop inside a parallel region to be divided among threads.|  
|[master](../VS_visualcpp/master.md)|Specifies that only the master threadshould execute a section of the program.|  
|[ordered](../VS_visualcpp/ordered--OpenMP-Directives-.md)|Specifies that code under a parallelized for loop should be executed like a sequential loop.|  
|[parallel](../VS_visualcpp/parallel.md)|Defines a parallel region, which is code that will be executed by multiple threads in parallel.|  
|[sections](../VS_visualcpp/sections--OpenMP-.md)|Identifies code sections to be divided among all threads.|  
|[single](../VS_visualcpp/single.md)|Lets you specify that a section of code should be executed on a single thread, not necessarily the master thread.|  
|[threadprivate](../VS_visualcpp/threadprivate.md)|Specifies that a variable is private to a thread.|  
  
## See Also  
 [OpenMP](../VS_visualcpp/OpenMP-in-Visual-C--.md)   
 [Clauses](../VS_visualcpp/OpenMP-Clauses.md)