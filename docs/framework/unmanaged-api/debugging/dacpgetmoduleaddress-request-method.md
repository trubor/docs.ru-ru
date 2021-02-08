---
description: 'Дополнительные сведения о методе: Дакпжетмодулеаддресс:: Request'
title: Метод DacpGetModuleAddress::Request
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4cdec9cf6b9bd818ce1137fb5b2c691532fab94e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801505"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="52102-103">Метод DacpGetModuleAddress::Request</span><span class="sxs-lookup"><span data-stu-id="52102-103">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="52102-104">Выполняет запрос на заполнение структуры из заданной структуры среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="52102-104">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="52102-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="52102-105">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="52102-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="52102-106">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="52102-107">окне Указатель на модуль начальных данных.</span><span class="sxs-lookup"><span data-stu-id="52102-107">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="52102-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="52102-108">Remarks</span></span>

<span data-ttu-id="52102-109">Эта структура находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="52102-109">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="52102-110">Чтобы использовать его, самый простой способ — имитировать реализацию:</span><span class="sxs-lookup"><span data-stu-id="52102-110">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="52102-111">Возвращает значение, полученное от вызова `Request` метода для `IXCLRDataModule*` параметра со следующими параметрами: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="52102-111">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="52102-112">Требования</span><span class="sxs-lookup"><span data-stu-id="52102-112">Requirements</span></span>

<span data-ttu-id="52102-113">**Платформы:** См. [требования к системе](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="52102-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="52102-114">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="52102-114">**Header:** None\</span></span>
<span data-ttu-id="52102-115">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="52102-115">**Library:** None\</span></span>
<span data-ttu-id="52102-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="52102-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="52102-117">См. также</span><span class="sxs-lookup"><span data-stu-id="52102-117">See also</span></span>

- [<span data-ttu-id="52102-118">Отладка</span><span class="sxs-lookup"><span data-stu-id="52102-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="52102-119">Структура Дакпжетмодулеаддресс</span><span class="sxs-lookup"><span data-stu-id="52102-119">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)
