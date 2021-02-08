---
description: 'Дополнительные сведения о: интерфейс ICLRStrongName2'
title: Интерфейс ICLRStrongName2
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
ms.openlocfilehash: 7442bd054af735e9f1b75b05feb8724dfa993f73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781796"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="50ccf-103">Интерфейс ICLRStrongName2</span><span class="sxs-lookup"><span data-stu-id="50ccf-103">ICLRStrongName2 Interface</span></span>

<span data-ttu-id="50ccf-104">Предоставляет возможность создания строгих имен с помощью группы SHA-2 алгоритмов безопасных хэширования (SHA-256, SHA-384 и SHA-512).</span><span class="sxs-lookup"><span data-stu-id="50ccf-104">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50ccf-105">Методы</span><span class="sxs-lookup"><span data-stu-id="50ccf-105">Methods</span></span>  
  
|<span data-ttu-id="50ccf-106">Метод</span><span class="sxs-lookup"><span data-stu-id="50ccf-106">Method</span></span>|<span data-ttu-id="50ccf-107">Описание</span><span class="sxs-lookup"><span data-stu-id="50ccf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50ccf-108">Метод StrongNameGetPublicKeyEx</span><span class="sxs-lookup"><span data-stu-id="50ccf-108">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="50ccf-109">Получает открытый ключ из пары открытого и закрытого ключей и задает алгоритм хеширования и алгоритм подписи.</span><span class="sxs-lookup"><span data-stu-id="50ccf-109">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="50ccf-110">Метод StrongNameSignatureVerificationEx2</span><span class="sxs-lookup"><span data-stu-id="50ccf-110">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="50ccf-111">Проверяет подпись сборки со строгим именем и обеспечивает сопоставление ключа ECMA с реальным ключом.</span><span class="sxs-lookup"><span data-stu-id="50ccf-111">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50ccf-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="50ccf-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50ccf-113">Требования</span><span class="sxs-lookup"><span data-stu-id="50ccf-113">Requirements</span></span>  

 <span data-ttu-id="50ccf-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50ccf-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50ccf-115">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="50ccf-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="50ccf-116">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50ccf-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50ccf-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50ccf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
