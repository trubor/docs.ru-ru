---
description: 'Узнайте подробнее о: Authenticode (справочник по неуправляемым интерфейсам API)'
title: Authenticode (справочник по неуправляемым интерфейсам API)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 0a4a9b4ba3cc9a5818896508c80bc31073f514e7
ms.sourcegitcommit: 26721a2260deabb3318cc98af8619306711153cd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2021
ms.locfileid: "105027848"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="4b597-103">Authenticode (справочник по неуправляемым интерфейсам API)</span><span class="sxs-lookup"><span data-stu-id="4b597-103">Authenticode (Unmanaged API Reference)</span></span>

<span data-ttu-id="4b597-104">Поддерживает модуль создания и проверки лицензий Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="4b597-104">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b597-105">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="4b597-105">In This Section</span></span>  

 [<span data-ttu-id="4b597-106">Функция _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="4b597-106">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="4b597-107">Получает хэш SHA-1 открытого ключа, связанного с закрытым ключом, который используется для подписания указанного сертификата.</span><span class="sxs-lookup"><span data-stu-id="4b597-107">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="4b597-108">Функция _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="4b597-108">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="4b597-109">Вычисляет токен открытого ключа строгого имени из формата CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="4b597-109">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="4b597-110">Функция _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="4b597-110">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="4b597-111">Преобразует модули и экспоненту в строгое имя маркера открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="4b597-111">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="4b597-112">Функция CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="4b597-112">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="4b597-113">Освобождает ресурсы, выделенные для структуры AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="4b597-113">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="4b597-114">Функция CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="4b597-114">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="4b597-115">Освобождает ресурсы, выделенные для структуры AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="4b597-115">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="4b597-116">Функция CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="4b597-116">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="4b597-117">Присваивает метки времени лицензии Authenticode XrML, созданной функцией CertCreateAuthenticodeLicense.</span><span class="sxs-lookup"><span data-stu-id="4b597-117">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="4b597-118">Функция CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="4b597-118">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="4b597-119">Проверяет правильность лицензии Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="4b597-119">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="4b597-120">Структура AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="4b597-120">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="4b597-121">Определяет информацию о подписавшем Authenticode.</span><span class="sxs-lookup"><span data-stu-id="4b597-121">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="4b597-122">Структура AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="4b597-122">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="4b597-123">Определяет информацию об отметке времени Authenticode.</span><span class="sxs-lookup"><span data-stu-id="4b597-123">Defines the Authenticode time stamper information.</span></span>  

## <a name="requirements"></a><span data-ttu-id="4b597-124">Требования</span><span class="sxs-lookup"><span data-stu-id="4b597-124">Requirements</span></span>

<span data-ttu-id="4b597-125">**Библиотека**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="4b597-125">**Library**: clr.dll</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4b597-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4b597-126">See also</span></span>

- [<span data-ttu-id="4b597-127">Справочник по неуправляемым API</span><span class="sxs-lookup"><span data-stu-id="4b597-127">Unmanaged API Reference</span></span>](../index.md)
