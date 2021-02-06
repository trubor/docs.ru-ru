---
description: Дополнительные сведения о методе Енумимпорттипес
title: Метод EnumImportTypes
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
ms.openlocfilehash: 39570740f3560f5bfef8ba80b95c0eb2aca41f59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638123"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="e511e-103">Метод EnumImportTypes</span><span class="sxs-lookup"><span data-stu-id="e511e-103">EnumImportTypes Method</span></span>

<span data-ttu-id="e511e-104">Перечисляет каждый тип в каждой области.</span><span class="sxs-lookup"><span data-stu-id="e511e-104">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="e511e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e511e-105">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="e511e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e511e-106">Parameters</span></span>

`hEnum`\
<span data-ttu-id="e511e-107">Обработчик для перечислителя.</span><span class="sxs-lookup"><span data-stu-id="e511e-107">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="e511e-108">Максимальное число извлекаемых типов.</span><span class="sxs-lookup"><span data-stu-id="e511e-108">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="e511e-109">Получает токены типа, не превышающие их `dwMax` .</span><span class="sxs-lookup"><span data-stu-id="e511e-109">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="e511e-110">Получает фактическое число типа в `aTypeDefs` .</span><span class="sxs-lookup"><span data-stu-id="e511e-110">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="e511e-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e511e-111">Return Value</span></span>

<span data-ttu-id="e511e-112">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="e511e-112">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="e511e-113">Требования</span><span class="sxs-lookup"><span data-stu-id="e511e-113">Requirements</span></span>

<span data-ttu-id="e511e-114">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="e511e-114">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="e511e-115">См. также</span><span class="sxs-lookup"><span data-stu-id="e511e-115">See also</span></span>

- [<span data-ttu-id="e511e-116">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="e511e-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e511e-117">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="e511e-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e511e-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="e511e-118">ALink API</span></span>](index.md)
