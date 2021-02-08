---
description: Дополнительные сведения о функции Цертверифяусентикоделиценсе
title: Функция CertVerifyAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
topic_type:
- apiref
ms.openlocfilehash: 0174223a4c1b984bf2d5d957219a85230fef8d0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772852"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="6c5df-103">Функция CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="6c5df-103">CertVerifyAuthenticodeLicense Function</span></span>

<span data-ttu-id="6c5df-104">Проверяет правильность лицензии Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="6c5df-104">Verifies the validity of an Authenticode XrML license.</span></span>

## <a name="syntax"></a><span data-ttu-id="6c5df-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6c5df-105">Syntax</span></span>

```cpp
HRESULT CertVerifyAuthenticodeLicense (
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,
    [in]   OPTIONAL DWORD                     dwFlags,
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo
);
```

## <a name="parameters"></a><span data-ttu-id="6c5df-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6c5df-106">Parameters</span></span>

 `pLicenseBlob`\
 <span data-ttu-id="6c5df-107">[в] Лицензия Authenticode XrML должна быть проверена.</span><span class="sxs-lookup"><span data-stu-id="6c5df-107">[in] The Authenticode XrML license to be verified.</span></span>

 <span data-ttu-id="6c5df-108">См. структуру [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="6c5df-108">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `dwFlags`\
 <span data-ttu-id="6c5df-109">[в] Необязательно.</span><span class="sxs-lookup"><span data-stu-id="6c5df-109">[in] Optional.</span></span> <span data-ttu-id="6c5df-110">Комбинация следующих значений:</span><span class="sxs-lookup"><span data-stu-id="6c5df-110">A combination of following values:</span></span>

- <span data-ttu-id="6c5df-111">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="6c5df-111">AXL_REVOCATION_NO_CHECK</span></span>

- <span data-ttu-id="6c5df-112">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="6c5df-112">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>

- <span data-ttu-id="6c5df-113">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="6c5df-113">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>

- <span data-ttu-id="6c5df-114">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="6c5df-114">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>

- <span data-ttu-id="6c5df-115">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="6c5df-115">AXL_LIFETIME_SIGNING</span></span>

- <span data-ttu-id="6c5df-116">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="6c5df-116">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>

 `pSignerInfo`\
 <span data-ttu-id="6c5df-117">[из] Для получения сведений о подписавшем.</span><span class="sxs-lookup"><span data-stu-id="6c5df-117">[out] To receive the signer's information.</span></span> <span data-ttu-id="6c5df-118">Если лицензия не подписана, переменной `dwError` присваивается значение TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="6c5df-118">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="6c5df-119">Он отвечает за освобождение ресурсов с помощью функции [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) после использования.</span><span class="sxs-lookup"><span data-stu-id="6c5df-119">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) function after use.</span></span>

 <span data-ttu-id="6c5df-120">См. раздел [структура AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="6c5df-120">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](axl-authenticode-signer-info-structure.md).</span></span>

 `pTimestamperInfo`\
 <span data-ttu-id="6c5df-121">[из] Для получения сведений об отметке времени (если есть).</span><span class="sxs-lookup"><span data-stu-id="6c5df-121">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="6c5df-122">Если отметки времени для лицензии не установлены, переменной `dwError` присваивается значение TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="6c5df-122">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="6c5df-123">Он отвечает за освобождение ресурсов с помощью функции [цертфриаусентикодетиместамперинфо](certfreeauthenticodetimestamperinfo-function.md) после использования.</span><span class="sxs-lookup"><span data-stu-id="6c5df-123">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>

 <span data-ttu-id="6c5df-124">См. раздел [структура AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="6c5df-124">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](axl-authenticode-timestamper-info-structure.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="6c5df-125">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6c5df-125">Return Value</span></span>

 <span data-ttu-id="6c5df-126">Возвращает значение `S_OK` в случае успешного выполнения.</span><span class="sxs-lookup"><span data-stu-id="6c5df-126">Returns `S_OK` if successful.</span></span> <span data-ttu-id="6c5df-127">В противном случае возвращается код ошибки.</span><span class="sxs-lookup"><span data-stu-id="6c5df-127">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="6c5df-128">Требования</span><span class="sxs-lookup"><span data-stu-id="6c5df-128">Requirements</span></span>

<span data-ttu-id="6c5df-129">**Сборка**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="6c5df-129">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="6c5df-130">См. также</span><span class="sxs-lookup"><span data-stu-id="6c5df-130">See also</span></span>

- [<span data-ttu-id="6c5df-131">Authenticode</span><span class="sxs-lookup"><span data-stu-id="6c5df-131">Authenticode</span></span>](index.md)
- [<span data-ttu-id="6c5df-132">Метод GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="6c5df-132">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="6c5df-133">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="6c5df-133">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
