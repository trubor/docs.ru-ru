---
description: 'Дополнительные сведения о методе: IMetaDataDispenserEx:: FindAssemblyModule'
title: Метод IMetaDataDispenserEx::FindAssemblyModule
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssemblyModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type:
- apiref
ms.openlocfilehash: 39ea13a2d8f2436e86db513aaa33f990f43d8132
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753579"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="2761b-103">Метод IMetaDataDispenserEx::FindAssemblyModule</span><span class="sxs-lookup"><span data-stu-id="2761b-103">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>

<span data-ttu-id="2761b-104">Этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="2761b-104">This method is not implemented.</span></span> <span data-ttu-id="2761b-105">При вызове возвращается E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="2761b-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2761b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2761b-106">Syntax</span></span>  
  
```cpp  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2761b-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="2761b-107">Parameters</span></span>  

 `szAppBase`  
 <span data-ttu-id="2761b-108">[in] Не используется.</span><span class="sxs-lookup"><span data-stu-id="2761b-108">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="2761b-109">[in] Не используется.</span><span class="sxs-lookup"><span data-stu-id="2761b-109">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="2761b-110">[in] Не используется.</span><span class="sxs-lookup"><span data-stu-id="2761b-110">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="2761b-111">окне Имя модуля.</span><span class="sxs-lookup"><span data-stu-id="2761b-111">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="2761b-112">окне Найденная сборка.</span><span class="sxs-lookup"><span data-stu-id="2761b-112">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="2761b-113">заполняет Простое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="2761b-113">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2761b-114">окне Размер (в байтах) `szName` .</span><span class="sxs-lookup"><span data-stu-id="2761b-114">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="2761b-115">заполняет Число символов, фактически возвращаемых в `szName` .</span><span class="sxs-lookup"><span data-stu-id="2761b-115">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2761b-116">Требования</span><span class="sxs-lookup"><span data-stu-id="2761b-116">Requirements</span></span>  

 <span data-ttu-id="2761b-117">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2761b-117">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2761b-118">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="2761b-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2761b-119">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2761b-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2761b-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2761b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2761b-121">См. также</span><span class="sxs-lookup"><span data-stu-id="2761b-121">See also</span></span>

- [<span data-ttu-id="2761b-122">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="2761b-122">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="2761b-123">Интерфейс IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="2761b-123">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
