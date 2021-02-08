---
description: Дополнительные сведения о функции CertFreeAuthenticodeSignerInfo
title: Функция CertFreeAuthenticodeSignerInfo
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
topic_type:
- apiref
ms.openlocfilehash: 6e8a97e8fee37d885c7d32102ed8cc7654992223
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772982"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="73eaf-103">Функция CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="73eaf-103">CertFreeAuthenticodeSignerInfo Function</span></span>

<span data-ttu-id="73eaf-104">Освобождает ресурсы, выделенные для структуры [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="73eaf-104">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="73eaf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="73eaf-105">Syntax</span></span>

```cpp
HRESULT CertFreeAuthenticodeSignerInfo (
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);
```

## <a name="parameters"></a><span data-ttu-id="73eaf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="73eaf-106">Parameters</span></span>

 `pSignerInfo`\
 <span data-ttu-id="73eaf-107">[в, из] Информация о подписавшем, которую необходимо указывать.</span><span class="sxs-lookup"><span data-stu-id="73eaf-107">[in, out] Signer information to be released.</span></span> <span data-ttu-id="73eaf-108">См. структуру [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="73eaf-108">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>

## <a name="return-value"></a><span data-ttu-id="73eaf-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="73eaf-109">Return Value</span></span>

 <span data-ttu-id="73eaf-110">`S_OK`, если функция выполняется успешно.</span><span class="sxs-lookup"><span data-stu-id="73eaf-110">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="73eaf-111">В противном случае возвращается код ошибки.</span><span class="sxs-lookup"><span data-stu-id="73eaf-111">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="73eaf-112">Требования</span><span class="sxs-lookup"><span data-stu-id="73eaf-112">Requirements</span></span>

<span data-ttu-id="73eaf-113">**Сборка**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="73eaf-113">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="73eaf-114">См. также</span><span class="sxs-lookup"><span data-stu-id="73eaf-114">See also</span></span>

- [<span data-ttu-id="73eaf-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="73eaf-115">Authenticode</span></span>](index.md)
