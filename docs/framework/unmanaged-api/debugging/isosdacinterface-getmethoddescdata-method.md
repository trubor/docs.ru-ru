---
description: 'Дополнительные сведения о методе: ИсосдаЦинтерфаце:: Жетмесоддескдата'
title: 'Метод ИсосдаЦинтерфаце:: Жетмесоддескдата'
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a1284aa4d810ed9d6db7ad3c1b471702b1dad54d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790429"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="a309f-103">Метод ИсосдаЦинтерфаце:: Жетмесоддескдата</span><span class="sxs-lookup"><span data-stu-id="a309f-103">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="a309f-104">Возвращает данные для заданного указателя MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="a309f-104">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a309f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a309f-105">Syntax</span></span>

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="a309f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a309f-106">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="a309f-107">окне Адрес MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="a309f-107">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="a309f-108">окне IP-адрес метода.</span><span class="sxs-lookup"><span data-stu-id="a309f-108">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="a309f-109">заполняет Данные, связанные с MethodDesc, возвращаются из внутренних API-интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="a309f-109">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="a309f-110">заполняет Число восстановленных версий rejit.</span><span class="sxs-lookup"><span data-stu-id="a309f-110">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="a309f-111">заполняет Данные, связанные с возвращенными версиями rejit, возвращенные из внутренних API.</span><span class="sxs-lookup"><span data-stu-id="a309f-111">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="a309f-112">заполняет Число байтов, необходимое для хранения данных, связанных с возвращенными версиями ReJit.</span><span class="sxs-lookup"><span data-stu-id="a309f-112">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="a309f-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="a309f-113">Remarks</span></span>

<span data-ttu-id="a309f-114">Предоставленный метод является частью `ISOSDacInterface` интерфейса и соответствует 21-сегменту таблицы виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="a309f-114">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 21st slot of the virtual method table.</span></span> <span data-ttu-id="a309f-115">Чтобы иметь возможность использовать их, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) необходимо определить как 64-разрядное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="a309f-115">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="a309f-116">Требования</span><span class="sxs-lookup"><span data-stu-id="a309f-116">Requirements</span></span>

<span data-ttu-id="a309f-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a309f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a309f-118">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="a309f-118">**Header:** None</span></span>  
<span data-ttu-id="a309f-119">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="a309f-119">**Library:** None</span></span>  
<span data-ttu-id="a309f-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a309f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a309f-121">См. также</span><span class="sxs-lookup"><span data-stu-id="a309f-121">See also</span></span>

- [<span data-ttu-id="a309f-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="a309f-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="a309f-123">Интерфейс ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="a309f-123">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
