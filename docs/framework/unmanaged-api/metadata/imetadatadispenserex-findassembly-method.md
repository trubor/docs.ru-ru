---
description: 'Дополнительные сведения о методе: IMetaDataDispenserEx:: Финдассембли'
title: Метод IMetaDataDispenserEx::FindAssembly
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type:
- apiref
ms.openlocfilehash: 6bed016e9235281b42f5a3231ef2aff284b6cc3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753605"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="7e3ca-103">Метод IMetaDataDispenserEx::FindAssembly</span><span class="sxs-lookup"><span data-stu-id="7e3ca-103">IMetaDataDispenserEx::FindAssembly Method</span></span>

<span data-ttu-id="7e3ca-104">Этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="7e3ca-104">This method is not implemented.</span></span> <span data-ttu-id="7e3ca-105">При вызове возвращается E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="7e3ca-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e3ca-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7e3ca-106">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e3ca-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="7e3ca-107">Parameters</span></span>  

 `szAppBase`  
 <span data-ttu-id="7e3ca-108">[in] Не используется.</span><span class="sxs-lookup"><span data-stu-id="7e3ca-108">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="7e3ca-109">[in] Не используется.</span><span class="sxs-lookup"><span data-stu-id="7e3ca-109">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="7e3ca-110">[in] Не используется.</span><span class="sxs-lookup"><span data-stu-id="7e3ca-110">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="7e3ca-111">окне Найденная сборка.</span><span class="sxs-lookup"><span data-stu-id="7e3ca-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="7e3ca-112">заполняет Простое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="7e3ca-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="7e3ca-113">окне Размер (в байтах) `szName` .</span><span class="sxs-lookup"><span data-stu-id="7e3ca-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="7e3ca-114">заполняет Число символов, фактически возвращаемых в `szName` .</span><span class="sxs-lookup"><span data-stu-id="7e3ca-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e3ca-115">Требования</span><span class="sxs-lookup"><span data-stu-id="7e3ca-115">Requirements</span></span>  

 <span data-ttu-id="7e3ca-116">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e3ca-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e3ca-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="7e3ca-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e3ca-118">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e3ca-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7e3ca-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e3ca-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e3ca-120">См. также</span><span class="sxs-lookup"><span data-stu-id="7e3ca-120">See also</span></span>

- [<span data-ttu-id="7e3ca-121">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="7e3ca-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="7e3ca-122">Интерфейс IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="7e3ca-122">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
