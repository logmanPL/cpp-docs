---
title: "Debug Routines"
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
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
caps.latest.revision: 11
manager: ghogen
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - ru-ru
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - pl-pl
  - pt-br
  - tr-tr
---
# Debug Routines
The debug version of the C run-time library supplies many diagnostic services that make debugging programs easier and allow developers to:  
  
-   Step directly into run-time functions during debugging  
  
-   Resolve assertions, errors, and exceptions  
  
-   Trace heap allocations and prevent memory leaks  
  
-   Report debug messages to the user  
  
 To use these routines, the [_DEBUG](../VS_visualcpp/_DEBUG.md) flag must be defined. All of these routines do nothing in a retail build of an application. For more information on how to use the new debug routines, see [CRT Debugging Techniques](../Topic/CRT%20Debugging%20Techniques.md).  
  
### Debug Versions of the C Run-Time Library Routines  
  
|Routine|Use|.NET Framework equivalent|  
|-------------|---------|-------------------------------|  
|[_ASSERT](../VS_visualcpp/_ASSERT--_ASSERTE--_ASSERT_EXPR-Macros.md)|Evaluate an expression and generates a debug report when the result is FALSE|[System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[_ASSERTE](../VS_visualcpp/_ASSERT--_ASSERTE--_ASSERT_EXPR-Macros.md)|Similar to `_ASSERT`, but includes the failed expression in the generated report|[System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[_CrtCheckMemory](../VS_visualcpp/_CrtCheckMemory.md)|Confirm the integrity of the memory blocks allocated on the debug heap|[System::Diagnostics::PerformanceCounter](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)|  
|[_CrtDbgBreak](../VS_visualcpp/_CrtDbgBreak.md)|Sets a break point.|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtDbgReport, _CrtDbgReportW](../VS_visualcpp/_CrtDbgReport--_CrtDbgReportW.md)|Generate a debug report with a user message and send the report to three possible destinations|[System::Diagnostics::Debug::Write](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.write.aspx), [System::Diagnostics::Debug::Writeline](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writeline.aspx), [System::Diagnostics::Debug::WriteIf](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writeif.aspx), [System::Diagnostics::Debug::WriteLineIf](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writelineif.aspx)|  
|[_CrtDoForAllClientObjects](../VS_visualcpp/_CrtDoForAllClientObjects.md)|Call an application-supplied function for all `_CLIENT_BLOCK` types on the heap|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtDumpMemoryLeaks](../VS_visualcpp/_CrtDumpMemoryLeaks.md)|Dump all of the memory blocks on the debug heap when a significant memory leak has occurred|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtIsMemoryBlock](../VS_visualcpp/_CrtIsMemoryBlock.md)|Verify that a specified memory block is located within the local heap and that it has a valid debug heap block type identifier|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtIsValidHeapPointer](../VS_visualcpp/_CrtIsValidHeapPointer.md)|Verifies that a specified pointer is in the local heap|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtIsValidPointer](../VS_visualcpp/_CrtIsValidPointer.md)|Verify that a specified memory range is valid for reading and writing|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtMemCheckpoint](../VS_visualcpp/_CrtMemCheckpoint.md)|Obtain the current state of the debug heap and store it in an application-supplied `_CrtMemState` structure|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtMemDifference](../VS_visualcpp/_CrtMemDifference.md)|Compare two memory states for significant differences and return the results|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtMemDumpAllObjectsSince](../VS_visualcpp/_CrtMemDumpAllObjectsSince.md)|Dump information about objects on the heap since a specified checkpoint was taken or from the start of program execution|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtMemDumpStatistics](../VS_visualcpp/_CrtMemDumpStatistics.md)|Dump the debug header information for a specified memory state in a user-readable form|[System::Diagnostics::PerformanceCounter](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)|  
|[_CrtReportBlockType](../VS_visualcpp/_CrtReportBlockType.md)|Returns the block type/subtype associated with a given debug heap block pointer.|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtSetAllocHook](../VS_visualcpp/_CrtSetAllocHook.md)|Install a client-defined allocation function by hooking it into the C run-time debug memory allocation process|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtSetBreakAlloc](../VS_visualcpp/_CrtSetBreakAlloc.md)|Set a breakpoint on a specified object allocation order number|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtSetDbgFlag](../VS_visualcpp/_CrtSetDbgFlag.md)|Retrieve or modify the state of the `_crtDbgFlag` flag to control the allocation behavior of the debug heap manager|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtSetDumpClient](../VS_visualcpp/_CrtSetDumpClient.md)|Install an application-defined function that is called every time a debug dump function is called to dump `_CLIENT_BLOCK` type memory blocks|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtSetReportFile](../VS_visualcpp/_CrtSetReportFile.md)|Identify the file or stream to be used as a destination for a specific report type by `_CrtDbgReport`|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtSetReportHook](../VS_visualcpp/_CrtSetReportHook.md)|Install a client-defined reporting function by hooking it into the C run-time debug reporting process|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtSetReportHook2, _CrtSetReportHookW2](../VS_visualcpp/_CrtSetReportHook2--_CrtSetReportHookW2.md)|Installs or uninstalls a client-defined reporting function by hooking it into the C run-time debug reporting process.|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_CrtSetReportMode](../VS_visualcpp/_CrtSetReportMode.md)|Specify the general destination(s) for a specific report type generated by `_CrtDbgReport`|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_RPT&#91;0,1,2,3,4&#93;](../VS_visualcpp/_RPT--_RPTF--_RPTW--_RPTFW-Macros.md)|Track the application's progress by generating a debug report by calling `_CrtDbgReport` with a format string and a variable number of arguments. Provides no source file and line number information.|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_RPTF&#91;0,1,2,3,4&#93;](../VS_visualcpp/_RPT--_RPTF--_RPTW--_RPTFW-Macros.md)|Similar to the `_RPTn` macros, but provides the source file name and line number where the report request originated|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_calloc_dbg](../VS_visualcpp/_calloc_dbg.md)|Allocate a specified number of memory blocks on the heap with additional space for a debugging header and overwrite buffers|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_expand_dbg](../VS_visualcpp/_expand_dbg.md)|Resize a specified block of memory on the heap by expanding or contracting the block|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_free_dbg](../VS_visualcpp/_free_dbg.md)|Free a block of memory on the heap|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_fullpath_dbg, _wfullpath_dbg](../VS_visualcpp/_fullpath_dbg--_wfullpath_dbg.md)|Create an absolute or full path name for the specified relative path name, using [_malloc_dbg](../VS_visualcpp/_malloc_dbg.md) to allocate memory.|[System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[_getcwd_dbg, _wgetcwd_dbg](../VS_visualcpp/_getcwd_dbg--_wgetcwd_dbg.md)|Get the current working directory, using [_malloc_dbg](../VS_visualcpp/_malloc_dbg.md) to allocate memory.|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_malloc_dbg](../VS_visualcpp/_malloc_dbg.md)|Allocate a block of memory on the heap with additional space for a debugging header and overwrite buffers|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_msize_dbg](../VS_visualcpp/_msize_dbg.md)|Calculate the size of a block of memory on the heap|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_realloc_dbg](../VS_visualcpp/_realloc_dbg.md)|Reallocate a specified block of memory on the heap by moving and/or resizing the block|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[_strdup_dbg, _wcsdup_dbg](../VS_visualcpp/_strdup_dbg--_wcsdup_dbg.md)|Duplicates a string, using [_malloc_dbg](../VS_visualcpp/_malloc_dbg.md) to allocate memory.|[System::String::Clone](https://msdn.microsoft.com/en-us/library/system.string.clone.aspx)|  
|[_tempnam_dbg, _wtempnam_dbg](../VS_visualcpp/_tempnam_dbg--_wtempnam_dbg.md)|Generate names you can use to create temporary files, using [_malloc_dbg](../VS_visualcpp/_malloc_dbg.md) to allocate memory.|Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
  
 The debug routines can be used to step through the source code for most of the other C run-time routines during the debugging process. However, Microsoft considers some technology to be proprietary and, therefore, does not provide the source code for these routines. Most of these routines belong to either the exception handling or floating-point processing groups, but a few others are included as well. The following table lists these routines.  
  
### C Run-Time Routines That Are Not Available in Source Code Form  
  
||||  
|-|-|-|  
|[acos, acosf, acosl](../VS_visualcpp/acos--acosf--acosl.md)|[_fpclass](../VS_visualcpp/_fpclass--_fpclassf.md)|[_nextafter](../VS_visualcpp/nextafter--nextafterf--nextafterl--_nextafter--_nextafterf--nexttoward--nexttowardf--nexttowardl.md)|  
|[asin](../VS_visualcpp/asin--asinf--asinl.md)|[_fpieee_flt](../VS_visualcpp/_fpieee_flt.md)|[pow](../VS_visualcpp/pow--powf--powl.md)|  
|[atan, atan2](../VS_visualcpp/atan--atanf--atanl--atan2--atan2f--atan2l.md)|[_fpreset](../VS_visualcpp/_fpreset.md)|[printf, _printf_l, wprintf, _wprintf_l](../VS_visualcpp/printf--_printf_l--wprintf--_wprintf_l.md), [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../VS_visualcpp/printf_s--_printf_s_l--wprintf_s--_wprintf_s_l.md)*|  
|[_cabs](../VS_visualcpp/_cabs.md)|[frexp](../VS_visualcpp/frexp.md)|[_scalb](../VS_visualcpp/_scalb.md)|  
|[ceil](../VS_visualcpp/ceil--ceilf--ceill.md)|[_hypot](../VS_visualcpp/hypot--hypotf--hypotl--_hypot--_hypotf--_hypotl.md)|[scanf, _scanf_l, wscanf, _wscanf_l](../VS_visualcpp/scanf--_scanf_l--wscanf--_wscanf_l.md), [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../VS_visualcpp/scanf_s--_scanf_s_l--wscanf_s--_wscanf_s_l.md)*|  
|[_chgsign, _chgsignf, _chgsignl](../VS_visualcpp/_chgsign--_chgsignf--_chgsignl.md)|[_isnan](../VS_visualcpp/isnan--_isnan--_isnanf.md)|[setjmp](../VS_visualcpp/setjmp.md)|  
|[_clear87, _clearfp](../VS_visualcpp/_clear87--_clearfp.md)|[_j0](../Topic/Bessel%20Functions:%20_j0,%20_j1,%20_jn.md)|[sin](../VS_visualcpp/sin--sinf--sinl--sinh--sinhf--sinhl.md)|  
|[_control87, _controlfp, \__control87_2](../VS_visualcpp/_control87--_controlfp--__control87_2.md)|[_j1](../Topic/Bessel%20Functions:%20_j0,%20_j1,%20_jn.md)|[sinh](../VS_visualcpp/sin--sinf--sinl--sinh--sinhf--sinhl.md)|  
|[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](../VS_visualcpp/copysign--copysignf--copysignl--_copysign--_copysignf--_copysignl.md)|[_jn](../Topic/Bessel%20Functions:%20_j0,%20_j1,%20_jn.md)|[sqrt](../VS_visualcpp/sqrt--sqrtf--sqrtl.md)|  
|[cos](../VS_visualcpp/cos--cosf--cosl--cosh--coshf--coshl.md)|[ldexp](../VS_visualcpp/ldexp.md)|[_status87, _statusfp](../VS_visualcpp/_status87--_statusfp--_statusfp2.md)|  
|[cosh](../VS_visualcpp/cos--cosf--cosl--cosh--coshf--coshl.md)|[log](../VS_visualcpp/log--logf--log10--log10f.md)|[tan](../VS_visualcpp/tan--tanf--tanl--tanh--tanhf--tanhl.md)|  
|[Exp](../VS_visualcpp/exp--expf.md)|[log10](../VS_visualcpp/log--logf--log10--log10f.md)|[tanh](../VS_visualcpp/tan--tanf--tanl--tanh--tanhf--tanhl.md)|  
|[fabs](../VS_visualcpp/fabs--fabsf--fabsl.md)|[_logb](../VS_visualcpp/logb--logbf--logbl--_logb--_logbf.md)|[_y0](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|  
|[_finite](../VS_visualcpp/_finite--_finitef.md)|[longjmp](../VS_visualcpp/longjmp.md)|[_y1](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|  
|[floor](../VS_visualcpp/floor--floorf--floorl.md)|[_matherr](../VS_visualcpp/_matherr.md)|[_yn](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|  
|[fmod](../VS_visualcpp/fmod--fmodf.md)|[modf](../VS_visualcpp/modf--modff--modfl.md)||  
  
 \*   Although source code is available for most of this routine, it makes an internal call to another routine for which source code is not provided.  
  
 Some C run-time functions and C++ operators behave differently when called from a debug build of an application. (Note that a debug build of an application can be done by either defining the `_DEBUG` flag or by linking with a debug version of the C run-time library.) The behavioral differences usually consist of extra features or information provided by the routine to support the debugging process. The following table lists these routines.  
  
### Routines that Behave Differently in a Debug Build of an Application  
  
|||  
|-|-|  
|C [abort](../VS_visualcpp/abort.md) routine|C++ [delete](../VS_visualcpp/delete-Operator--C---.md) operator|  
|C [assert](../VS_visualcpp/assert-Macro--_assert--_wassert.md) routine|C++ [new](../VS_visualcpp/new-Operator--C---.md) operator|  
  
## See Also  
 [Run-Time Routines by Category](../VS_visualcpp/Run-Time-Routines-by-Category.md)   
 [Run-Time Error Checking](../VS_visualcpp/Run-Time-Error-Checking.md)