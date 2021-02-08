---
description: Дополнительные сведения о функции Цертфриаусентикодетиместамперинфо
title: Функция CertFreeAuthenticodeTimestamperInfo
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
topic_type:
- apiref
ms.openlocfilehash: 5234a90ea1d0272a7409b1b0b4def2160b77a513
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772943"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="b1200-103">Функция CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="b1200-103">CertFreeAuthenticodeTimestamperInfo Function</span></span>

<span data-ttu-id="b1200-104">Освобождает ресурсы, выделенные для структуры [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="b1200-104">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1200-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b1200-105">Syntax</span></span>

```cpp
HRESULT CertFreeAuthenticodeTimestamperInfo (
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo
);
```

## <a name="parameters"></a><span data-ttu-id="b1200-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b1200-106">Parameters</span></span>

 `pTimestamperInfo`\
 <span data-ttu-id="b1200-107">[в, из] Информация об отметке времени выпуска.</span><span class="sxs-lookup"><span data-stu-id="b1200-107">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="b1200-108">См. структуру [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="b1200-108">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>

## <a name="return-value"></a><span data-ttu-id="b1200-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b1200-109">Return Value</span></span>

 <span data-ttu-id="b1200-110">`S_OK`, если функция выполняется успешно.</span><span class="sxs-lookup"><span data-stu-id="b1200-110">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="b1200-111">В противном случае возвращается код ошибки.</span><span class="sxs-lookup"><span data-stu-id="b1200-111">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="b1200-112">Требования</span><span class="sxs-lookup"><span data-stu-id="b1200-112">Requirements</span></span>

<span data-ttu-id="b1200-113">**Сборка**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="b1200-113">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="b1200-114">См. также</span><span class="sxs-lookup"><span data-stu-id="b1200-114">See also</span></span>

- [<span data-ttu-id="b1200-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="b1200-115">Authenticode</span></span>](index.md)
