---
title: "QualifierSet_Delete 函数 （非托管 API 参考）"
description: "QualifierSet_Delete 函数按名称删除限定符。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Delete
helpviewer_keywords: QualifierSet_Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9245fc0ee109837249f1f3df400385c117a2f2d7
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetdelete-function"></a><span data-ttu-id="a0068-103">QualifierSet_Delete 函数</span><span class="sxs-lookup"><span data-stu-id="a0068-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="a0068-104">按名称删除指定的限定符。</span><span class="sxs-lookup"><span data-stu-id="a0068-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a0068-105">语法</span><span class="sxs-lookup"><span data-stu-id="a0068-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="a0068-106">参数</span><span class="sxs-lookup"><span data-stu-id="a0068-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a0068-107">[in]未使用此参数。</span><span class="sxs-lookup"><span data-stu-id="a0068-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="a0068-108">[in]指向的指针[IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)实例。</span><span class="sxs-lookup"><span data-stu-id="a0068-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="a0068-109">[in]要删除的限定符的名称。</span><span class="sxs-lookup"><span data-stu-id="a0068-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="a0068-110">返回值</span><span class="sxs-lookup"><span data-stu-id="a0068-110">Return value</span></span>

<span data-ttu-id="a0068-111">此函数返回以下值中定义*WbemCli.h*标头文件，或者你可以定义它们常量作为在代码中：</span><span class="sxs-lookup"><span data-stu-id="a0068-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a0068-112">返回的常量</span><span class="sxs-lookup"><span data-stu-id="a0068-112">Constant</span></span>  |<span data-ttu-id="a0068-113">值</span><span class="sxs-lookup"><span data-stu-id="a0068-113">Value</span></span>  |<span data-ttu-id="a0068-114">描述</span><span class="sxs-lookup"><span data-stu-id="a0068-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a0068-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a0068-115">0x80041008</span></span> | <span data-ttu-id="a0068-116">`wszName`参数无效。</span><span class="sxs-lookup"><span data-stu-id="a0068-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="a0068-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="a0068-117">0x80041016</span></span> | <span data-ttu-id="a0068-118">删除此限定符是非法的。</span><span class="sxs-lookup"><span data-stu-id="a0068-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="a0068-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a0068-119">0x80041002</span></span> | <span data-ttu-id="a0068-120">找不到指定的限定符。</span><span class="sxs-lookup"><span data-stu-id="a0068-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a0068-121">0</span><span class="sxs-lookup"><span data-stu-id="a0068-121">0</span></span> | <span data-ttu-id="a0068-122">函数调用成功。</span><span class="sxs-lookup"><span data-stu-id="a0068-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="a0068-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="a0068-123">0x40002</span></span> | <span data-ttu-id="a0068-124">本地重写已删除并从父对象的原始限定符已恢复作用域。</span><span class="sxs-lookup"><span data-stu-id="a0068-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a0068-125">备注</span><span class="sxs-lookup"><span data-stu-id="a0068-125">Remarks</span></span>

<span data-ttu-id="a0068-126">此函数包装对的调用[IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="a0068-126">This function wraps a call to the [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="a0068-127">由于限定符传播规则，而特定限定符可能已继承自另一个对象和仅在当前类或实例中重写。</span><span class="sxs-lookup"><span data-stu-id="a0068-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="a0068-128">在这种情况下，`QualifierSet_Delete`方法将限定符重置为其原始的继承值。</span><span class="sxs-lookup"><span data-stu-id="a0068-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="a0068-129">函数将在此情况下返回状态代码`WBEM_S_RESET_TO_DEFAULT`。</span><span class="sxs-lookup"><span data-stu-id="a0068-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="a0068-130">要求</span><span class="sxs-lookup"><span data-stu-id="a0068-130">Requirements</span></span>  
 <span data-ttu-id="a0068-131">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0068-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0068-132">**标头：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a0068-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a0068-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a0068-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0068-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="a0068-134">See also</span></span>  
[<span data-ttu-id="a0068-135">WMI 和性能计数器 （非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="a0068-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)