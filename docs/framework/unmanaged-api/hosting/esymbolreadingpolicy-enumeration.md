---
description: Дополнительные сведения о перечислении Есимболреадингполици
title: Перечисление ESymbolReadingPolicy
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: e84c31343b589cb6019d88fafc9b94207c5f5892
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785423"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="a86a8-103">Перечисление ESymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="a86a8-103">ESymbolReadingPolicy Enumeration</span></span>

<span data-ttu-id="a86a8-104">Содержит значения, задают политику чтения PDB-файлов.</span><span class="sxs-lookup"><span data-stu-id="a86a8-104">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a86a8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a86a8-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="a86a8-106">Члены</span><span class="sxs-lookup"><span data-stu-id="a86a8-106">Members</span></span>  
  
|<span data-ttu-id="a86a8-107">Член</span><span class="sxs-lookup"><span data-stu-id="a86a8-107">Member</span></span>|<span data-ttu-id="a86a8-108">Описание</span><span class="sxs-lookup"><span data-stu-id="a86a8-108">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="a86a8-109">Указывает, что отладчик всегда должен считывать PDB-файлы.</span><span class="sxs-lookup"><span data-stu-id="a86a8-109">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="a86a8-110">Указывает, что отладчик должен считывать только PDB-файлы, связанные со сборками с полным доверием.</span><span class="sxs-lookup"><span data-stu-id="a86a8-110">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="a86a8-111">Указывает, что отладчик никогда не должен считывать PDB-файлы.</span><span class="sxs-lookup"><span data-stu-id="a86a8-111">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a86a8-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="a86a8-112">Remarks</span></span>  

 <span data-ttu-id="a86a8-113">`ESymbolReadingPolicy`Перечисление используется с методом [ICLRDebugManager:: SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a86a8-113">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a86a8-114">Требования</span><span class="sxs-lookup"><span data-stu-id="a86a8-114">Requirements</span></span>  

 <span data-ttu-id="a86a8-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a86a8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a86a8-116">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a86a8-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a86a8-117">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a86a8-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a86a8-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a86a8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a86a8-119">См. также</span><span class="sxs-lookup"><span data-stu-id="a86a8-119">See also</span></span>

- [<span data-ttu-id="a86a8-120">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="a86a8-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
