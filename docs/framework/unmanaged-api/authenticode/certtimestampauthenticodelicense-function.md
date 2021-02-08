---
description: Дополнительные сведения о функции Церттиместампаусентикоделиценсе
title: Функция CertTimestampAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
topic_type:
- apiref
ms.openlocfilehash: 79b1a924a99a76c18e6434abfed0a90da71eb6f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772923"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="1f099-103">Функция CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="1f099-103">CertTimestampAuthenticodeLicense Function</span></span>

<span data-ttu-id="1f099-104">Отметки времени для лицензии Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="1f099-104">Time-stamps an Authenticode XrML license.</span></span>

## <a name="syntax"></a><span data-ttu-id="1f099-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1f099-105">Syntax</span></span>

```cpp
HRESULT CertTimestampAuthenticodeLicense (
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,
    [in]  LPCWSTR            pwszTimestampURI,
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob
);
```

## <a name="parameters"></a><span data-ttu-id="1f099-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1f099-106">Parameters</span></span>

 `pSignedLicenseBlob`\
 <span data-ttu-id="1f099-107">[в] Подписанная лицензия Authenticode XrML, требующая отметки времени.</span><span class="sxs-lookup"><span data-stu-id="1f099-107">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="1f099-108">См. структуру [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="1f099-108">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `pwszTimestampURI`\
 <span data-ttu-id="1f099-109">[в] URL-адресу сервера отметок времени.</span><span class="sxs-lookup"><span data-stu-id="1f099-109">[in] The time-stamp server's URI.</span></span>

 `pTimestampSignatureBlob`\
 <span data-ttu-id="1f099-110">[из] Указатель на CRYPT_DATA_BLOB для получения подписи с отметкой времени в кодировке base64.</span><span class="sxs-lookup"><span data-stu-id="1f099-110">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="1f099-111">Его можно бесплатно `pTimestampSignatureBlob` -> `pbData` `HepFree()` использовать после использования.</span><span class="sxs-lookup"><span data-stu-id="1f099-111">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="1f099-112">См. структуру [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="1f099-112">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f099-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="1f099-113">Remarks</span></span>

 <span data-ttu-id="1f099-114">Подпись с отметкой времени фактически представляет собой сообщение PKCS #7 SignedData, содержимое которого является двоичной формой SignatureValue из подписи лицензии.</span><span class="sxs-lookup"><span data-stu-id="1f099-114">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="1f099-115">По сути, она действует как подпись, подтверждающая лицензию.</span><span class="sxs-lookup"><span data-stu-id="1f099-115">Basically, this acts as a counter-signature of the license.</span></span>

## <a name="return-value"></a><span data-ttu-id="1f099-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1f099-116">Return Value</span></span>

 <span data-ttu-id="1f099-117">`S_OK`, если функция выполняется успешно.</span><span class="sxs-lookup"><span data-stu-id="1f099-117">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="1f099-118">В противном случае возвращается код ошибки.</span><span class="sxs-lookup"><span data-stu-id="1f099-118">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="1f099-119">Требования</span><span class="sxs-lookup"><span data-stu-id="1f099-119">Requirements</span></span>

<span data-ttu-id="1f099-120">**Сборка**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="1f099-120">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="1f099-121">См. также</span><span class="sxs-lookup"><span data-stu-id="1f099-121">See also</span></span>

- [<span data-ttu-id="1f099-122">Authenticode</span><span class="sxs-lookup"><span data-stu-id="1f099-122">Authenticode</span></span>](index.md)
