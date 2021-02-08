---
description: 'Узнайте подробнее о: Authenticode (справочник по неуправляемым интерфейсам API)'
title: Authenticode (справочник по неуправляемым интерфейсам API)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: d7a1684fde900bfc01161193d0747b156c6856a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772839"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="360ea-103">Authenticode (справочник по неуправляемым интерфейсам API)</span><span class="sxs-lookup"><span data-stu-id="360ea-103">Authenticode (Unmanaged API Reference)</span></span>

<span data-ttu-id="360ea-104">Поддерживает модуль создания и проверки лицензий Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="360ea-104">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="360ea-105">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="360ea-105">In This Section</span></span>  

 [<span data-ttu-id="360ea-106">Функция _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="360ea-106">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="360ea-107">Получает хэш SHA-1 открытого ключа, связанного с закрытым ключом, который используется для подписания указанного сертификата.</span><span class="sxs-lookup"><span data-stu-id="360ea-107">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="360ea-108">Функция _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="360ea-108">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="360ea-109">Вычисляет токен открытого ключа строгого имени из формата CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="360ea-109">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="360ea-110">Функция _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="360ea-110">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="360ea-111">Преобразует модули и экспоненту в строгое имя маркера открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="360ea-111">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="360ea-112">Функция CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="360ea-112">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="360ea-113">Освобождает ресурсы, выделенные для структуры AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="360ea-113">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="360ea-114">Функция CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="360ea-114">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="360ea-115">Освобождает ресурсы, выделенные для структуры AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="360ea-115">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="360ea-116">Функция CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="360ea-116">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="360ea-117">Присваивает метки времени лицензии Authenticode XrML, созданной функцией CertCreateAuthenticodeLicense.</span><span class="sxs-lookup"><span data-stu-id="360ea-117">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="360ea-118">Функция CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="360ea-118">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="360ea-119">Проверяет правильность лицензии Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="360ea-119">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="360ea-120">Структура AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="360ea-120">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="360ea-121">Определяет информацию о подписавшем Authenticode.</span><span class="sxs-lookup"><span data-stu-id="360ea-121">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="360ea-122">Структура AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="360ea-122">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="360ea-123">Определяет информацию об отметке времени Authenticode.</span><span class="sxs-lookup"><span data-stu-id="360ea-123">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="360ea-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="360ea-124">See also</span></span>

- [<span data-ttu-id="360ea-125">Справочник по неуправляемым API</span><span class="sxs-lookup"><span data-stu-id="360ea-125">Unmanaged API Reference</span></span>](../index.md)
