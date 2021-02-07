---
description: 'Дополнительные сведения о: интерфейс IMetaDataDispenserEx'
title: Интерфейс IMetaDataDispenserEx
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: d940ac20eaad4b930ab17fb2d194d3b03bd4cf3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753540"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="0fc98-103">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="0fc98-103">IMetaDataDispenserEx Interface</span></span>

<span data-ttu-id="0fc98-104">Расширяет интерфейс [интерфейса IMetaDataDispenser](imetadatadispenser-interface.md) , чтобы предоставить возможность контролировать работу API метаданных в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="0fc98-104">Extends the [IMetaDataDispenser Interface](imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0fc98-105">Методы</span><span class="sxs-lookup"><span data-stu-id="0fc98-105">Methods</span></span>  
  
|<span data-ttu-id="0fc98-106">Метод</span><span class="sxs-lookup"><span data-stu-id="0fc98-106">Method</span></span>|<span data-ttu-id="0fc98-107">Описание</span><span class="sxs-lookup"><span data-stu-id="0fc98-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0fc98-108">Метод FindAssembly</span><span class="sxs-lookup"><span data-stu-id="0fc98-108">FindAssembly Method</span></span>](imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="0fc98-109">Этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="0fc98-109">This method is not implemented.</span></span> <span data-ttu-id="0fc98-110">При вызове возвращается E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="0fc98-110">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="0fc98-111">Метод FindAssemblyModule</span><span class="sxs-lookup"><span data-stu-id="0fc98-111">FindAssemblyModule Method</span></span>](imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="0fc98-112">Этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="0fc98-112">This method is not implemented.</span></span> <span data-ttu-id="0fc98-113">При вызове возвращается E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="0fc98-113">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="0fc98-114">Метод GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="0fc98-114">GetCORSystemDirectory Method</span></span>](imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="0fc98-115">Возвращает каталог, содержащий текущую среду CLR.</span><span class="sxs-lookup"><span data-stu-id="0fc98-115">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="0fc98-116">Этот метод поддерживается только для использования необработанными отладчиками.</span><span class="sxs-lookup"><span data-stu-id="0fc98-116">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="0fc98-117">Если вызывается из другого компонента, он возвратит E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="0fc98-117">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="0fc98-118">Метод GetOption</span><span class="sxs-lookup"><span data-stu-id="0fc98-118">GetOption Method</span></span>](imetadatadispenserex-getoption-method.md)|<span data-ttu-id="0fc98-119">Возвращает значение указанного параметра для текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="0fc98-119">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="0fc98-120">Параметр определяет, как обрабатываются вызовы к текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="0fc98-120">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="0fc98-121">Метод OpenScopeOnITypeInfo</span><span class="sxs-lookup"><span data-stu-id="0fc98-121">OpenScopeOnITypeInfo Method</span></span>](imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="0fc98-122">Этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="0fc98-122">This method is not implemented.</span></span> <span data-ttu-id="0fc98-123">При вызове возвращается E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="0fc98-123">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="0fc98-124">Метод SetOption</span><span class="sxs-lookup"><span data-stu-id="0fc98-124">SetOption Method</span></span>](imetadatadispenserex-setoption-method.md)|<span data-ttu-id="0fc98-125">Задает для указанного параметра заданное значение для текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="0fc98-125">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="0fc98-126">Параметр определяет, как обрабатываются вызовы к текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="0fc98-126">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0fc98-127">Требования</span><span class="sxs-lookup"><span data-stu-id="0fc98-127">Requirements</span></span>  

 <span data-ttu-id="0fc98-128">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fc98-128">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fc98-129">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="0fc98-129">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0fc98-130">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0fc98-130">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0fc98-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fc98-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc98-132">См. также</span><span class="sxs-lookup"><span data-stu-id="0fc98-132">See also</span></span>

- [<span data-ttu-id="0fc98-133">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="0fc98-133">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="0fc98-134">Интерфейс IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="0fc98-134">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="0fc98-135">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0fc98-135">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0fc98-136">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0fc98-136">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
