---
title: "Input and Output, Manifest Tool, Configuration Properties, &lt;Projectname&gt; Property Pages Dialog Box"
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
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
caps.latest.revision: 13
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
# Input and Output, Manifest Tool, Configuration Properties, &lt;Projectname&gt; Property Pages Dialog Box
Use this dialog box to specify input and output options for [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 To access this property page dialog box, open the property pages for your project or your property sheet. Expand the **Manifest Tool** node under **Configuration Properties**, and then select **Input and Output**.  
  
## UIElement List  
 **Additional Manifest Files**  
 Uses the **/manifest** option to specify the full paths of additional manifest files that the manifest tool will process or merge. Full paths are delimited by a semicolon.  
  
 **Input Resource Manifests**  
 Uses the **/inputresource** option to specify the full path of a resource of type RT_MANIFEST, to input into the manifest tool. The path can be followed by the specified resource ID. For example:  
  
 `dll_with_manifest.dll;#1`  
  
 The resource ID is optional and defaults to CREATEPROCESS_MANIFEST_RESOURCE_ID in winuser.h.  
  
 **Embed Manifest**  
 **Yes** specifies that the project system will embed the application manifest file into the assembly.  
  
 **No** specifies that the project system will create the application manifest file as a stand-alone file.  
  
 **Output Manifest File**  
 Specifies the name of the output manifest file. This property is optional when only one manifest file is operated upon by the manifest tool.  
  
 **Manifest Resource File**  
 Specifies the output resources files used to embed the manifest into the project output.  
  
 **Generate Catalog Files**  
 Uses the **/makecdfs** option to specify that the manifest tool will generate catalog definition files (.cdf files), which are used to make catalogs.  
  
 **Generate Manifest From ManagedAssembly**  
 Generates a manifest from a managed assembly. (**-managedassemblyname:***file*).  
  
 **Suppress Dependency Element**  
 Used with the **-managedassembly** option. This tag suppresses the generation of dependency elements in the final manifest.  
  
 **Generate Category Tags**  
 Used with the **-managedassembly** option. This tag causes the category tags to be generated.  
  
 **Enable DPI Awareness**  
 Specifies whether the application is DPI-aware. By default, the setting is **Yes** for MFC projects and **No** otherwise because only MFC projects have built in DPI awareness. You can override the setting to **Yes** if you add code to handle different DPI settings. Your application might appear fuzzy or small if you set it as DPI-aware when it is not.  
  
## See Also  
 [ClickOnce Application Manifest](../Topic/ClickOnce%20Application%20Manifest.md)   
 [Manifest Tool Property Pages](../VS_visualcpp/Manifest-Tool-Property-Pages.md)   
 [How to: Open Project Property Pages](../Topic/How%20to:%20Open%20Project%20Property%20Pages.md)   
 [How to: Edit Project Property Sheets](../Topic/How%20to:%20Edit%20Project%20Property%20Sheets.md)