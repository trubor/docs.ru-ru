---
description: Дополнительные сведения о функции _AxlRSAKeyValueToPublicKeyToken
title: Функция _AxlRSAKeyValueToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
topic_type:
- apiref
ms.openlocfilehash: 01fc4cdc1d9985375748307ca2d7fff97191c908
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747274"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="98eb5-103">\_Функция Акслрсакэйвалуетопубликкэйтокен</span><span class="sxs-lookup"><span data-stu-id="98eb5-103">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="98eb5-104">Преобразует модули и экспоненту в строгое имя маркера открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="98eb5-104">Converts a Modulus and Exponent to a strong name public key token.</span></span>

## <a name="syntax"></a><span data-ttu-id="98eb5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="98eb5-105">Syntax</span></span>

```cpp
HRESULT _AxlRSAKeyValueToPublicKeyToken (
    [in]  PCRYPT_DATA_BLOB pModulusBlob,
    [in]  PCRYPT_DATA_BLOB pExponentBlob,
    [out] LPWSTR           *ppwszPublicKeyToken
);
```

## <a name="parameters"></a><span data-ttu-id="98eb5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="98eb5-106">Parameters</span></span>

 `pModulusBlob`\
 <span data-ttu-id="98eb5-107">окне Большой двоичный объект модуля в кодировке Base64 (из \<Modulus> элемента).</span><span class="sxs-lookup"><span data-stu-id="98eb5-107">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="98eb5-108">См. структуру [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="98eb5-108">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `pExponentBlob`\
 <span data-ttu-id="98eb5-109">окне Большой двоичный объект экспоненты в кодировке Base64 (из \<Exponent> элемента).</span><span class="sxs-lookup"><span data-stu-id="98eb5-109">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="98eb5-110">См. структуру [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="98eb5-110">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `ppwszPublicKeyToken`\
 <span data-ttu-id="98eb5-111">[из] Указатель на WCHAR \* для получения шестнадцатеричного кодированного маркера открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="98eb5-111">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>

## <a name="return-value"></a><span data-ttu-id="98eb5-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="98eb5-112">Return Value</span></span>

 <span data-ttu-id="98eb5-113">`S_OK`, если функция выполняется успешно.</span><span class="sxs-lookup"><span data-stu-id="98eb5-113">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="98eb5-114">В противном случае возвращается код ошибки.</span><span class="sxs-lookup"><span data-stu-id="98eb5-114">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="98eb5-115">Требования</span><span class="sxs-lookup"><span data-stu-id="98eb5-115">Requirements</span></span>

<span data-ttu-id="98eb5-116">**Сборка**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="98eb5-116">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="98eb5-117">См. также</span><span class="sxs-lookup"><span data-stu-id="98eb5-117">See also</span></span>

- [<span data-ttu-id="98eb5-118">Authenticode</span><span class="sxs-lookup"><span data-stu-id="98eb5-118">Authenticode</span></span>](index.md)
