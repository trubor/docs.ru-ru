---
description: 'Дополнительные сведения о: Интерфейс IMetaDataEmit2'
title: Интерфейс IMetaDataEmit2
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
ms.openlocfilehash: db1880d64bf3b1e9084d6745251c174788a4afe7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745688"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="a9f1f-103">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a9f1f-103">IMetaDataEmit2 Interface</span></span>

<span data-ttu-id="a9f1f-104">Расширяет интерфейс [IMetaDataEmit](imetadataemit-interface.md) в основном, чтобы обеспечить возможность работы с универсальными типами.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-104">Extends the [IMetaDataEmit](imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9f1f-105">Методы</span><span class="sxs-lookup"><span data-stu-id="a9f1f-105">Methods</span></span>  
  
|<span data-ttu-id="a9f1f-106">Метод</span><span class="sxs-lookup"><span data-stu-id="a9f1f-106">Method</span></span>|<span data-ttu-id="a9f1f-107">Описание</span><span class="sxs-lookup"><span data-stu-id="a9f1f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9f1f-108">Метод DefineGenericParam</span><span class="sxs-lookup"><span data-stu-id="a9f1f-108">DefineGenericParam Method</span></span>](imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="a9f1f-109">Создает определение для параметра универсального типа и получает маркер для этого параметра универсального типа.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-109">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="a9f1f-110">Метод DefineMethodSpec</span><span class="sxs-lookup"><span data-stu-id="a9f1f-110">DefineMethodSpec Method</span></span>](imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="a9f1f-111">Создает универсальный экземпляр метода и получает маркер для определения.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-111">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="a9f1f-112">Метод GetDeltaSaveSize</span><span class="sxs-lookup"><span data-stu-id="a9f1f-112">GetDeltaSaveSize Method</span></span>](imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="a9f1f-113">Возвращает значение, указывающее разницу в размере данных, необходимых для выражения изменений в текущем сеансе "изменить и продолжить".</span><span class="sxs-lookup"><span data-stu-id="a9f1f-113">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="a9f1f-114">Метод ResetENCLog</span><span class="sxs-lookup"><span data-stu-id="a9f1f-114">ResetENCLog Method</span></span>](imetadataemit2-resetenclog-method.md)|<span data-ttu-id="a9f1f-115">Сбрасывает журнал изменения и продолжения и запускает новый сеанс.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-115">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="a9f1f-116">Метод SaveDelta</span><span class="sxs-lookup"><span data-stu-id="a9f1f-116">SaveDelta Method</span></span>](imetadataemit2-savedelta-method.md)|<span data-ttu-id="a9f1f-117">Сохраняет изменения из текущего сеанса "изменить и продолжить" в указанный файл.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-117">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="a9f1f-118">Метод SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="a9f1f-118">SaveDeltaToMemory Method</span></span>](imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="a9f1f-119">Сохраняет изменения из текущего сеанса "изменить и продолжить" в память.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-119">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="a9f1f-120">Метод SaveDeltaToStream</span><span class="sxs-lookup"><span data-stu-id="a9f1f-120">SaveDeltaToStream Method</span></span>](imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="a9f1f-121">Сохраняет изменения из текущего сеанса "изменить и продолжить" в указанный поток.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-121">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="a9f1f-122">Метод SetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="a9f1f-122">SetGenericParamProps Method</span></span>](imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="a9f1f-123">Задает значения свойств для определения универсального параметра, на которое ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="a9f1f-123">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9f1f-124">Требования</span><span class="sxs-lookup"><span data-stu-id="a9f1f-124">Requirements</span></span>  

 <span data-ttu-id="a9f1f-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9f1f-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9f1f-126">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a9f1f-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9f1f-127">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9f1f-127">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9f1f-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9f1f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f1f-129">См. также</span><span class="sxs-lookup"><span data-stu-id="a9f1f-129">See also</span></span>

- [<span data-ttu-id="a9f1f-130">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="a9f1f-130">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="a9f1f-131">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a9f1f-131">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
