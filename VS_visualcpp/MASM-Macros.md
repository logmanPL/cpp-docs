---
title: "MASM Macros"
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
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
caps.latest.revision: 5
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
# MASM Macros
In order to simplify the use of the [Raw Pseudo Operations](../VS_visualcpp/Raw-Pseudo-Operations.md), there are a set of macros, defined in ksamd64.inc, which can be used to create typical procedure prologues and epilogues.  
  
## Remarks  
  
|Macro|Description|  
|-----------|-----------------|  
|alloc_stack(n)|Allocates a stack frame of n bytes (using sub rsp, n), and emits the appropriate unwind information (.allocstack n)|  
|save_reg reg, loc|Saves a nonvolatile register reg on the stack at RSP offset loc, and emits the appropriate unwind information. (.savereg reg, loc)|  
|push_reg reg|Pushes a nonvolatile register reg on the stack, and emits the appropriate unwind information. (.pushreg reg)|  
|rex_push_reg reg|Save a nonvolatile register on the stack using a 2 byte push, and emits the appropriate unwind information (.pushreg reg)  This should be used if the push is the first instruction in the function to ensure that the function is hot-patchable.|  
|save_xmm128 reg, loc|Saves a nonvolatile XMM register reg on the stack at RSP offset loc, and emits the appropriate unwind information (.savexmm128 reg, loc)|  
|set_frame reg, offset|Sets the frame register reg to be the RSP + offset (using a mov, or an lea), and emits the appropriate unwind information (.set_frame reg, offset)|  
|push_eflags|Pushes the eflags with a pushfq instruction, and emits the appropriate unwind information (.alloc_stack 8)|  
  
 Here is a sample function prolog with proper usage of the macros:  
  
```  
SkFrame struct   
Fill    dq ?; fill to 8 mod 16   
SavedRdi dq ?; saved register RDI   
SavedRsi dq ?; saved register RSI   
SkFrame ends  
  
sampleFrame struct  
Filldq?; fill to 8 mod 16  
SavedRdidq?; Saved Register RDI   
SavedRsi  dq?; Saved Register RSI  
sampleFrame ends  
  
sample2 PROC FRAME  
alloc_stack(sizeof sampleFrame)  
save_reg rdi, sampleFrame.SavedRdi  
save_reg rsi, sampleFrame.SavedRsi  
.end_prolog  
  
; function body  
  
mov rsi, sampleFrame.SavedRsi[rsp]  
mov rdi, sampleFrame.SavedRdi[rsp]  
  
; Here’s the official epilog  
  
add rsp, (sizeof sampleFrame)  
ret  
sample2 ENDP  
```  
  
## See Also  
 [Unwind Helpers for MASM](../VS_visualcpp/Unwind-Helpers-for-MASM.md)