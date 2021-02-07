---
description: 'Дополнительные сведения о методе: IMetaDataDispenserEx:: GetCORSystemDirectory'
title: Метод IMetaDataDispenserEx::GetCORSystemDirectory
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
ms.openlocfilehash: 3ceda653e50ba5ad7de5548b78781f48cda41624
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753566"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="eb181-103">Метод IMetaDataDispenserEx::GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="eb181-103">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>

<span data-ttu-id="eb181-104">Возвращает каталог, содержащий текущую среду CLR.</span><span class="sxs-lookup"><span data-stu-id="eb181-104">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="eb181-105">Этот метод поддерживается только для использования необработанными отладчиками.</span><span class="sxs-lookup"><span data-stu-id="eb181-105">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="eb181-106">Если вызывается из другого компонента, он возвратит E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="eb181-106">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb181-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eb181-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb181-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="eb181-108">Parameters</span></span>  

 `szBuffer`  
 <span data-ttu-id="eb181-109">заполняет Буфер для получения имени каталога.</span><span class="sxs-lookup"><span data-stu-id="eb181-109">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="eb181-110">окне Размер (в байтах) `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="eb181-110">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="eb181-111">заполняет Число байтов, фактически возвращаемых в `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="eb181-111">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb181-112">Требования</span><span class="sxs-lookup"><span data-stu-id="eb181-112">Requirements</span></span>  

 <span data-ttu-id="eb181-113">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb181-113">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb181-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="eb181-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eb181-115">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb181-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eb181-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb181-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb181-117">См. также</span><span class="sxs-lookup"><span data-stu-id="eb181-117">See also</span></span>

- [<span data-ttu-id="eb181-118">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="eb181-118">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="eb181-119">Интерфейс IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="eb181-119">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
