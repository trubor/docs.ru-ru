---
description: 'Дополнительные сведения о методе: Иксклрдатамодуле:: Request'
title: 'Метод Иксклрдатамодуле:: Request'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 96f4153c58a228cfb22a5cd25a53b6e60fc4dfd1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800738"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="76d92-103">Метод Иксклрдатамодуле:: Request</span><span class="sxs-lookup"><span data-stu-id="76d92-103">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="76d92-104">Запросы на заполнение буфера данными модуля.</span><span class="sxs-lookup"><span data-stu-id="76d92-104">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="76d92-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="76d92-105">Syntax</span></span>

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="76d92-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="76d92-106">Parameters</span></span>

`reqCode`\
<span data-ttu-id="76d92-107">окне Тип запроса для отправки.</span><span class="sxs-lookup"><span data-stu-id="76d92-107">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="76d92-108">[in] размер входного буфера, который должен быть передан.</span><span class="sxs-lookup"><span data-stu-id="76d92-108">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="76d92-109">[in, size_is (Инбуфферсизе)] Указатель буфера для необработанных данных, отправляемых в запросе.</span><span class="sxs-lookup"><span data-stu-id="76d92-109">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="76d92-110">окне Размер выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="76d92-110">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="76d92-111">[out, size_is (Аутбуфферсизе)] Указатель буфера, используемый для хранения ответа на запрос.</span><span class="sxs-lookup"><span data-stu-id="76d92-111">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="76d92-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="76d92-112">Remarks</span></span>

<span data-ttu-id="76d92-113">Предоставленный метод является частью `IXCLRDataModule` интерфейса и соответствует слоту 37th таблицы виртуальных методов.</span><span class="sxs-lookup"><span data-stu-id="76d92-113">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 37th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="76d92-114">Требования</span><span class="sxs-lookup"><span data-stu-id="76d92-114">Requirements</span></span>

<span data-ttu-id="76d92-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76d92-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="76d92-116">**Заголовок:** Нет **библиотеки:** нет **платформа .NET Framework версий:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="76d92-116">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="76d92-117">См. также</span><span class="sxs-lookup"><span data-stu-id="76d92-117">See also</span></span>

- [<span data-ttu-id="76d92-118">Отладка</span><span class="sxs-lookup"><span data-stu-id="76d92-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="76d92-119">Интерфейс IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="76d92-119">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
