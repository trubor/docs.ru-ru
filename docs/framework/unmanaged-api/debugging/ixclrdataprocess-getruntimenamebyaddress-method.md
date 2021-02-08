---
description: 'Дополнительные сведения о методе: Иксклрдатапроцесс:: Жетрунтименамебяддресс'
title: 'Метод Иксклрдатапроцесс:: Жетрунтименамебяддресс'
ms.date: 4/27/2020
api.name:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: tommcdon
ms.author: tommcdon
ms.openlocfilehash: 62d9ae73c216748cc8eb02aedd41cf19f475d071
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800660"
---
# <a name="ixclrdataprocessgetruntimenamebyaddress-method"></a><span data-ttu-id="dcc60-103">Метод Иксклрдатапроцесс:: Жетрунтименамебяддресс</span><span class="sxs-lookup"><span data-stu-id="dcc60-103">IXCLRDataProcess::GetRuntimeNameByAddress Method</span></span>

<span data-ttu-id="dcc60-104">Возвращает имя для заданного адреса.</span><span class="sxs-lookup"><span data-stu-id="dcc60-104">Gets a name for the given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="dcc60-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dcc60-105">Syntax</span></span>

```cpp
HRESULT GetRuntimeNameByAddress(
    [in] CLRDATA_ADDRESS address,
    [in] ULONG32 flags,
    [in] ULONG32 bufLen,
    [out] ULONG32 *nameLen,
    [out, size_is(bufLen)] WCHAR nameBuf[],
    [out] CLRDATA_ADDRESS* displacement
);
```

## <a name="parameters"></a><span data-ttu-id="dcc60-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcc60-106">Parameters</span></span>

`address`\
<span data-ttu-id="dcc60-107">окне `CLRDATA_ADDRESS` Значение, представляющее адрес кода.</span><span class="sxs-lookup"><span data-stu-id="dcc60-107">[in] A `CLRDATA_ADDRESS` value that represents a code address.</span></span>

`flags`\
<span data-ttu-id="dcc60-108">окне Задайте значение "0".</span><span class="sxs-lookup"><span data-stu-id="dcc60-108">[in] Set to '0'.</span></span>

`bufLen`\
<span data-ttu-id="dcc60-109">окне Длина буфера.</span><span class="sxs-lookup"><span data-stu-id="dcc60-109">[in] The length of the buffer.</span></span>

`namLen`\
<span data-ttu-id="dcc60-110">заполняет Указатель на число возвращаемых символов.</span><span class="sxs-lookup"><span data-stu-id="dcc60-110">[out] A pointer to the number of characters returned.</span></span>

`namBuf`\
<span data-ttu-id="dcc60-111">[out, size_is ( `bufLen` )] входной буфер длины `bufLen` , в которой хранится имя среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="dcc60-111">[out, size_is(`bufLen`)] The input buffer of length `bufLen` that stores the runtime name.</span></span>

`displacement`\
<span data-ttu-id="dcc60-112">заполняет `CLRDATA_ADDRESS` Указатель на смещение кода возвращаемого символа.</span><span class="sxs-lookup"><span data-stu-id="dcc60-112">[out] A `CLRDATA_ADDRESS` pointer to the code offset of the returned symbol.</span></span>

## <a name="remarks"></a><span data-ttu-id="dcc60-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="dcc60-113">Remarks</span></span>

<span data-ttu-id="dcc60-114">Предоставленный метод является частью `IXCLRDataProcess` интерфейса и соответствует шестнадцатому слоту таблицы виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="dcc60-114">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 16th slot of the virtual-method table.</span></span>

> [!NOTE]
> <span data-ttu-id="dcc60-115">Если размер буфера не достаточен для имени, этот метод возвращает `S_FALSE` и задает `nameLen` требуемую длину буфера.</span><span class="sxs-lookup"><span data-stu-id="dcc60-115">If the buffer is not large enough for the name, this method returns `S_FALSE` and sets `nameLen` to the required buffer length.</span></span>

## <a name="requirements"></a><span data-ttu-id="dcc60-116">Требования</span><span class="sxs-lookup"><span data-stu-id="dcc60-116">Requirements</span></span>

<span data-ttu-id="dcc60-117">**Платформы:** См. [требования к системе](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="dcc60-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="dcc60-118">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="dcc60-118">**Header:** None\</span></span>
<span data-ttu-id="dcc60-119">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="dcc60-119">**Library:** None\</span></span>
<span data-ttu-id="dcc60-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dcc60-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dcc60-121">См. также</span><span class="sxs-lookup"><span data-stu-id="dcc60-121">See also</span></span>

- [<span data-ttu-id="dcc60-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="dcc60-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="dcc60-123">Интерфейс IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="dcc60-123">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
