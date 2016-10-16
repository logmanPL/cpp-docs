---
title: "Project Build Error PRJ0003"
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
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
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
# Project Build Error PRJ0003
Error spawning 'command line'.  
  
 A command, ***command line***, which was formed from input in the **Property Pages** dialog box, returned an error code but no information will appear in the Output window.  
  
 Possible reasons for this error:  
  
-   Your project depends on ATL Server. Beginning with Visual Studio 2008, ATL Server is no longer included as part of Visual Studio, but has been released as a shared-source project at CodePlex. To download the ATL Server source code and tools, go to [http://go.microsoft.com/fwlink/?LinkID=81979](http://go.microsoft.com/fwlink/?LinkID=81979).  
  
-   Low system resources. Close some applications to resolve this.  
  
-   Insufficient security privileges. Verify that you have sufficient security privileges.  
  
-   The executable paths specified in [VC++ Directories](assetId:///e027448b-c811-4c3d-8531-4325ad3f6e02) do not include the path for the tool that you are attempting to run.  
  
-   For makefile projects, you are missing a command to run on either **Build Command Line** or **Rebuild Command Line**.  
  
## See Also  
 [Project Build Errors and Warnings (PRJxxxx)](../VS_visualcpp/Project-Build-Errors-and-Warnings--PRJxxxx-.md)