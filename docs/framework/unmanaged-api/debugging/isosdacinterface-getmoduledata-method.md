---
description: 'Дополнительные сведения о методе: ИсосдаЦинтерфаце:: Жетмодуледата'
title: 'Метод ИсосдаЦинтерфаце:: Жетмодуледата'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c01f55d55d5ee9082dee4b3adb3022bb17807aa2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790390"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="26184-103">Метод ИсосдаЦинтерфаце:: Жетмодуледата</span><span class="sxs-lookup"><span data-stu-id="26184-103">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="26184-104">Извлекает данные, соответствующие модулю, загруженному по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="26184-104">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="26184-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="26184-105">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="26184-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="26184-106">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="26184-107">окне Адрес модуля, для которого нужно получить сведения.</span><span class="sxs-lookup"><span data-stu-id="26184-107">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="26184-108">заполняет [Структура дакпмодуледата](dacpmoduledata-structure.md) для хранения сведений о загруженном модуле.</span><span class="sxs-lookup"><span data-stu-id="26184-108">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="26184-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="26184-109">Remarks</span></span>

<span data-ttu-id="26184-110">Предоставленный метод является частью `ISOSDacInterface` интерфейса и соответствует слоту 14 таблицы виртуальных методов.</span><span class="sxs-lookup"><span data-stu-id="26184-110">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="26184-111">Требования</span><span class="sxs-lookup"><span data-stu-id="26184-111">Requirements</span></span>

<span data-ttu-id="26184-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26184-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="26184-113">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="26184-113">**Header:** None</span></span>  
<span data-ttu-id="26184-114">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="26184-114">**Library:** None</span></span>  
<span data-ttu-id="26184-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="26184-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="26184-116">См. также</span><span class="sxs-lookup"><span data-stu-id="26184-116">See also</span></span>

- [<span data-ttu-id="26184-117">Отладка</span><span class="sxs-lookup"><span data-stu-id="26184-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="26184-118">Интерфейс ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="26184-118">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
