---
description: 'Дополнительные сведения о методе: IAssemblyCache:: Куеряссемблинфо'
title: Метод IAssemblyCache::QueryAssemblyInfo
ms.date: 03/30/2017
api_name:
- IAssemblyCache.QueryAssemblyInfo
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type:
- apiref
ms.openlocfilehash: b3aa0064e24b22cf0af8b4e8d23a8b92d2f1ac34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760918"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="d433f-103">Метод IAssemblyCache::QueryAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="d433f-103">IAssemblyCache::QueryAssemblyInfo Method</span></span>

<span data-ttu-id="d433f-104">Возвращает запрошенные данные о указанной сборке.</span><span class="sxs-lookup"><span data-stu-id="d433f-104">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d433f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d433f-105">Syntax</span></span>  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d433f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d433f-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="d433f-107">окне Флаги, определенные в Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="d433f-107">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="d433f-108">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="d433f-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="d433f-109">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="d433f-109">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
- <span data-ttu-id="d433f-110">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="d433f-110">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="d433f-111">окне Имя сборки, для которой будут получены данные.</span><span class="sxs-lookup"><span data-stu-id="d433f-111">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="d433f-112">[вход, выход] Структура [ASSEMBLY_INFO](assembly-info-structure.md) , содержащая данные о сборке.</span><span class="sxs-lookup"><span data-stu-id="d433f-112">[in, out] An [ASSEMBLY_INFO](assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d433f-113">Требования</span><span class="sxs-lookup"><span data-stu-id="d433f-113">Requirements</span></span>  

 <span data-ttu-id="d433f-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d433f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d433f-115">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d433f-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d433f-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d433f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d433f-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d433f-117">See also</span></span>

- [<span data-ttu-id="d433f-118">Интерфейс IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="d433f-118">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
