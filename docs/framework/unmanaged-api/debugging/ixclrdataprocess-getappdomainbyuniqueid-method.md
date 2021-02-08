---
description: 'Дополнительные сведения о методе: Иксклрдатапроцесс:: Жетаппдомаинбюникуеид'
title: 'Метод Иксклрдатапроцесс:: Жетаппдомаинбюникуеид'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7087362efbb810fcb6e1b6f7eb9f23c54c38fade
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800673"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="813c4-103">Метод Иксклрдатапроцесс:: Жетаппдомаинбюникуеид</span><span class="sxs-lookup"><span data-stu-id="813c4-103">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="813c4-104">Получает `AppDomain` в процессе на основе его уникального идентификатора.</span><span class="sxs-lookup"><span data-stu-id="813c4-104">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="813c4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="813c4-105">Syntax</span></span>

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="813c4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="813c4-106">Parameters</span></span>

`id`\
<span data-ttu-id="813c4-107">окне Уникальный идентификатор домена приложения</span><span class="sxs-lookup"><span data-stu-id="813c4-107">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="813c4-108">заполняет AppDomain</span><span class="sxs-lookup"><span data-stu-id="813c4-108">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="813c4-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="813c4-109">Remarks</span></span>

<span data-ttu-id="813c4-110">Предоставленный метод является частью `IXCLRDataProcess` интерфейса и соответствует слоту 20 таблицы виртуальных методов.</span><span class="sxs-lookup"><span data-stu-id="813c4-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="813c4-111">`IXCLRDataAppDomain*`Возвращаемый объект используется для взаимодействия с другими API.</span><span class="sxs-lookup"><span data-stu-id="813c4-111">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="813c4-112">Требования</span><span class="sxs-lookup"><span data-stu-id="813c4-112">Requirements</span></span>

<span data-ttu-id="813c4-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="813c4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="813c4-114">**Заголовок:** Нет **библиотеки:** нет **платформа .NET Framework версий:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="813c4-114">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="813c4-115">См. также</span><span class="sxs-lookup"><span data-stu-id="813c4-115">See also</span></span>

- [<span data-ttu-id="813c4-116">Отладка</span><span class="sxs-lookup"><span data-stu-id="813c4-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="813c4-117">Интерфейс IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="813c4-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
