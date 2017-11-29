---
title: "ICorDebugUnmanagedCallback::DebugEvent 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback.DebugEvent
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 008ae1bd1a5774604bf2c0f196352dcf07da6ee7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="95d8f-102">ICorDebugUnmanagedCallback::DebugEvent 方法</span><span class="sxs-lookup"><span data-stu-id="95d8f-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="95d8f-103">通知调试器已激发本机事件。</span><span class="sxs-lookup"><span data-stu-id="95d8f-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95d8f-104">语法</span><span class="sxs-lookup"><span data-stu-id="95d8f-104">Syntax</span></span>  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95d8f-105">参数</span><span class="sxs-lookup"><span data-stu-id="95d8f-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="95d8f-106">[in]本机事件指向的指针。</span><span class="sxs-lookup"><span data-stu-id="95d8f-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="95d8f-107">[in]`true`，如果与托管的进程状态的交互是不可能的非托管的事件发生，直到该调试器将调用后[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); 否则为`false`。</span><span class="sxs-lookup"><span data-stu-id="95d8f-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95d8f-108">备注</span><span class="sxs-lookup"><span data-stu-id="95d8f-108">Remarks</span></span>  
 <span data-ttu-id="95d8f-109">如果正在调试的线程的 Win32 线程，则不要使用调试接口的 Win32 任何成员。</span><span class="sxs-lookup"><span data-stu-id="95d8f-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="95d8f-110">你可以调用`ICorDebugController::Continue`仅 Win32 线程，仅当继续过去的带外事件。</span><span class="sxs-lookup"><span data-stu-id="95d8f-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="95d8f-111">`DebugEvent`回调不会不符合的回调的标准规则。</span><span class="sxs-lookup"><span data-stu-id="95d8f-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="95d8f-112">当调用`DebugEvent`，进程将在原始操作系统调试停止状态。</span><span class="sxs-lookup"><span data-stu-id="95d8f-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="95d8f-113">将不会同步过程。</span><span class="sxs-lookup"><span data-stu-id="95d8f-113">The process will not be synchronized.</span></span> <span data-ttu-id="95d8f-114">它将自动进入时满足对托管代码，这可能会导致其他嵌套的相关信息的请求所需的同步的状态`DebugEvent`回调。</span><span class="sxs-lookup"><span data-stu-id="95d8f-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="95d8f-115">调用[icordebugprocess:: Clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)的过程将继续过程之前忽略异常事件。</span><span class="sxs-lookup"><span data-stu-id="95d8f-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="95d8f-116">调用此方法将工作表上继续请求，而不是 DBG_EXCEPTION_NOT_HANDLED DBG_CONTINUE，并自动清除的带断点和单步执行的异常。</span><span class="sxs-lookup"><span data-stu-id="95d8f-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="95d8f-117">即使正在调试的应用程序看上去已停止和未完成的带内事件已存在时，可以在任何时候，来自带外事件。</span><span class="sxs-lookup"><span data-stu-id="95d8f-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="95d8f-118">在.NET Framework 2.0 版中，调试器应立即跳过的带断点事件。</span><span class="sxs-lookup"><span data-stu-id="95d8f-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="95d8f-119">应使用调试器[icordebugprocess2:: Setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)和[icordebugprocess2:: Clearunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)方法来添加和删除断点。</span><span class="sxs-lookup"><span data-stu-id="95d8f-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="95d8f-120">这些方法将自动跳过任何带的断点。</span><span class="sxs-lookup"><span data-stu-id="95d8f-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="95d8f-121">因此，调度仅的带断点应已在指令流中，如调用 Win32 的原始断点`DebugBreak`函数。</span><span class="sxs-lookup"><span data-stu-id="95d8f-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="95d8f-122">不尝试使用`ICorDebugProcess::ClearCurrentException`， [icordebugprocess:: Getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)， [icordebugprocess:: Setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)，或任何其他成员的[调试 API](../../../../docs/framework/unmanaged-api/debugging/index.md)。</span><span class="sxs-lookup"><span data-stu-id="95d8f-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95d8f-123">要求</span><span class="sxs-lookup"><span data-stu-id="95d8f-123">Requirements</span></span>  
 <span data-ttu-id="95d8f-124">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95d8f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95d8f-125">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95d8f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95d8f-126">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95d8f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95d8f-127">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95d8f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d8f-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="95d8f-128">See Also</span></span>  
 [<span data-ttu-id="95d8f-129">ICorDebugUnmanagedCallback 接口</span><span class="sxs-lookup"><span data-stu-id="95d8f-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)