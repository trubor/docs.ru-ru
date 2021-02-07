---
description: Дополнительные сведения о функции _AxlGetIssuerPublicKeyHash
title: Функция _AxlGetIssuerPublicKeyHash
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
topic_type:
- apiref
ms.openlocfilehash: 586a072b33376a2fdade119fe3db0f48addfa3f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747365"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="2c40a-103">\_Функция Акслжетиссуерпубликкэйхаш</span><span class="sxs-lookup"><span data-stu-id="2c40a-103">\_AxlGetIssuerPublicKeyHash Function</span></span>

<span data-ttu-id="2c40a-104">Получает хэш SHA-1 открытого ключа, связанного с закрытым ключом, который используется для подписания указанного сертификата.</span><span class="sxs-lookup"><span data-stu-id="2c40a-104">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>

## <a name="syntax"></a><span data-ttu-id="2c40a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2c40a-105">Syntax</span></span>

```cpp
HRESULT _AxlGetIssuerPublicKeyHash (
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,
    [out] LPWSTR                *ppwszPublicKeyHash
);
```

## <a name="parameters"></a><span data-ttu-id="2c40a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2c40a-106">Parameters</span></span>

 `pChainContext`\
 <span data-ttu-id="2c40a-107">[в] Большой двоичный объект открытого ключа CSP.</span><span class="sxs-lookup"><span data-stu-id="2c40a-107">[in] The CSP public key blob.</span></span> <span data-ttu-id="2c40a-108">См. структуру [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="2c40a-108">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `ppwszPublicKeyHash`\
 <span data-ttu-id="2c40a-109">[из] Указатель на WCHAR \* для получения шестнадцатеричного кодированного маркера открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="2c40a-109">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>

## <a name="return-value"></a><span data-ttu-id="2c40a-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2c40a-110">Return Value</span></span>

 <span data-ttu-id="2c40a-111">`S_OK`, если функция выполняется успешно. В противном случае — `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="2c40a-111">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>

## <a name="requirements"></a><span data-ttu-id="2c40a-112">Требования</span><span class="sxs-lookup"><span data-stu-id="2c40a-112">Requirements</span></span>

<span data-ttu-id="2c40a-113">**Сборка**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="2c40a-113">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="2c40a-114">См. также</span><span class="sxs-lookup"><span data-stu-id="2c40a-114">See also</span></span>

- [<span data-ttu-id="2c40a-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2c40a-115">Authenticode</span></span>](index.md)
