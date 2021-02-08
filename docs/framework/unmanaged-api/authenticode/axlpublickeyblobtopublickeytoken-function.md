---
description: Дополнительные сведения о функции _AxlPublicKeyBlobToPublicKeyToken
title: Функция _AxlPublicKeyBlobToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
topic_type:
- apiref
ms.openlocfilehash: df0b484bad64051eb892d4898a6c90777cc2d5cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781939"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="200be-103">\_Функция Акслпубликкэйблобтопубликкэйтокен</span><span class="sxs-lookup"><span data-stu-id="200be-103">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>

<span data-ttu-id="200be-104">Вычисляет токен открытого ключа строгого имени из формата CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="200be-104">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>

## <a name="syntax"></a><span data-ttu-id="200be-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="200be-105">Syntax</span></span>

```cpp
HRESULT _AxlPublicKeyBlobToPublicKeyToken (
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,
    [out] LPWSTR                 *ppwszPublicKeyToken
);
```

## <a name="parameters"></a><span data-ttu-id="200be-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="200be-106">Parameters</span></span>

 `pCspPublicKeyBlob`\
 <span data-ttu-id="200be-107">[в] Большой двоичный объект открытого ключа CSP.</span><span class="sxs-lookup"><span data-stu-id="200be-107">[in] The CSP public key blob.</span></span>

 `ppwszPublicKeyHash`\
 <span data-ttu-id="200be-108">[из] Указатель на WCHAR \* для получения шестнадцатеричного кодированного хэша открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="200be-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>

## <a name="return-value"></a><span data-ttu-id="200be-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="200be-109">Return Value</span></span>

 <span data-ttu-id="200be-110">`S_OK`, если функция выполняется успешно. В противном случае — `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="200be-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>

## <a name="requirements"></a><span data-ttu-id="200be-111">Требования</span><span class="sxs-lookup"><span data-stu-id="200be-111">Requirements</span></span>

<span data-ttu-id="200be-112">**Сборка**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="200be-112">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="200be-113">См. также</span><span class="sxs-lookup"><span data-stu-id="200be-113">See also</span></span>

- [<span data-ttu-id="200be-114">Authenticode</span><span class="sxs-lookup"><span data-stu-id="200be-114">Authenticode</span></span>](index.md)
