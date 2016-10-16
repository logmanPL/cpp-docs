---
title: "Current Time: Automation Classes"
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
  - "time, setting current"
  - "current time, COleDateTime object"
  - "procedures, getting current time"
  - "Automation classes, current time"
  - "time, getting current"
ms.assetid: cc967f17-1189-4cf3-85f9-1969462d5f72
caps.latest.revision: 8
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
# Current Time: Automation Classes
The following procedure shows how to create a `COleDateTime` object and initialize it with the current time.  
  
#### To get the current time  
  
1.  Create a `COleDateTime` object.  
  
2.  Call `GetCurrentTime`.  
  
     [!code[NVC_ATLMFC_Utilities#177](../atl/codesnippet/CPP/current-time--automation-classes_1.cpp)]  
  
## See Also  
 [Date and Time: Automation Support](../atl/date-and-time--automation-support.md)