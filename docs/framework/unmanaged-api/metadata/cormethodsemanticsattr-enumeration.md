---
title: "CorMethodSemanticsAttr 枚举"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodSemanticsAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodSemanticsAttr
helpviewer_keywords: CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c6dca24aad06b1c07c86cb716f4be344c8458471
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="c2408-102">CorMethodSemanticsAttr 枚举</span><span class="sxs-lookup"><span data-stu-id="c2408-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="c2408-103">包含一些值，用于描述方法和关联属性或事件之间的关系。</span><span class="sxs-lookup"><span data-stu-id="c2408-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2408-104">语法</span><span class="sxs-lookup"><span data-stu-id="c2408-104">Syntax</span></span>  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="c2408-105">成员</span><span class="sxs-lookup"><span data-stu-id="c2408-105">Members</span></span>  
  
|<span data-ttu-id="c2408-106">成员</span><span class="sxs-lookup"><span data-stu-id="c2408-106">Member</span></span>|<span data-ttu-id="c2408-107">描述</span><span class="sxs-lookup"><span data-stu-id="c2408-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="c2408-108">指定的方法是`set`属性访问器。</span><span class="sxs-lookup"><span data-stu-id="c2408-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="c2408-109">指定的方法是`get`属性访问器。</span><span class="sxs-lookup"><span data-stu-id="c2408-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="c2408-110">指定该方法具有一个属性或事件之外此处定义的关系。</span><span class="sxs-lookup"><span data-stu-id="c2408-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="c2408-111">指定该方法将添加事件处理程序方法。</span><span class="sxs-lookup"><span data-stu-id="c2408-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="c2408-112">指定该方法中删除事件处理程序方法。</span><span class="sxs-lookup"><span data-stu-id="c2408-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="c2408-113">指定该方法将引发事件。</span><span class="sxs-lookup"><span data-stu-id="c2408-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2408-114">要求</span><span class="sxs-lookup"><span data-stu-id="c2408-114">Requirements</span></span>  
 <span data-ttu-id="c2408-115">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2408-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2408-116">**标头：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c2408-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c2408-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2408-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2408-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2408-118">See Also</span></span>  
 [<span data-ttu-id="c2408-119">元数据枚举</span><span class="sxs-lookup"><span data-stu-id="c2408-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)