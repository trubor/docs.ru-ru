---
description: 'Дополнительные сведения о методе: ИсосдаЦинтерфаце:: Жетмесоддескптрфромип'
title: 'Метод ИсосдаЦинтерфаце:: Жетмесоддескптрфромип'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 8d7c7071b7b3fc520faea71c8d7792317745cfde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790416"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="a6676-103">Метод ИсосдаЦинтерфаце:: Жетмесоддескптрфромип</span><span class="sxs-lookup"><span data-stu-id="a6676-103">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="a6676-104">Получает указатель MethodDesc, соответствующий методу, содержащему указанный адрес собственной инструкции.</span><span class="sxs-lookup"><span data-stu-id="a6676-104">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a6676-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a6676-105">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="a6676-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6676-106">Parameters</span></span>

`ip`\
<span data-ttu-id="a6676-107">окне Адрес в методе во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="a6676-107">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="a6676-108">заполняет Адрес `MethodDesc` для конкретного метода.</span><span class="sxs-lookup"><span data-stu-id="a6676-108">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6676-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="a6676-109">Remarks</span></span>

<span data-ttu-id="a6676-110">Предоставленный метод является частью [ `ISOSDacInterface` интерфейса](isosdacinterface-interface.md) и соответствует слоту 22 таблицы виртуальных методов.</span><span class="sxs-lookup"><span data-stu-id="a6676-110">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 22nd slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6676-111">Требования</span><span class="sxs-lookup"><span data-stu-id="a6676-111">Requirements</span></span>

<span data-ttu-id="a6676-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6676-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a6676-113">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="a6676-113">**Header:** None</span></span>  
<span data-ttu-id="a6676-114">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="a6676-114">**Library:** None</span></span>  
<span data-ttu-id="a6676-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a6676-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a6676-116">См. также</span><span class="sxs-lookup"><span data-stu-id="a6676-116">See also</span></span>

- [<span data-ttu-id="a6676-117">Отладка</span><span class="sxs-lookup"><span data-stu-id="a6676-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="a6676-118">Интерфейс ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="a6676-118">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
