---
title: "replace_copy_if (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: ["cpp-windows"]
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: ["cliext::replace_copy_if"]
dev_langs: ["C++"]
helpviewer_keywords: ["replace_copy_if function [STL/CLR]"]
ms.assetid: 60edf9b8-34e6-4d94-a611-363ef7b7fb80
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
ms.workload: ["cplusplus", "dotnet"]
---
# replace_copy_if (STL/CLR)
Examines each element in a source range and replaces it if it satisfies a specified predicate while copying the result into a new destination range.  
  
## Syntax  
  
```  
template<class _InIt, class _OutIt, class _Pr, class _Ty> inline  
    _OutIt replace_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred, const _Ty% _Val);  
```  
  
## Remarks  
 This function behaves the same as the C++ Standard Library function `replace_copy_if`. For more information, see [replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if).  
  
## Requirements  
 **Header:** \<cliext/algorithm>  
  
 **Namespace:** cliext  
  
## See Also  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)