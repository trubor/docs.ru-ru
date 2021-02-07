---
description: 'Дополнительные сведения о: структура Публиккэйблоб'
title: Структура PublicKeyBlob
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
ms.openlocfilehash: 94c1ea3d5a41bbb8941658e87f97cd6d6336187a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736494"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="afcc1-103">Структура PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="afcc1-103">PublicKeyBlob Structure</span></span>

<span data-ttu-id="afcc1-104">Представляет в двоичном формате открытый ключ пары открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="afcc1-104">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afcc1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="afcc1-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a><span data-ttu-id="afcc1-106">Члены</span><span class="sxs-lookup"><span data-stu-id="afcc1-106">Members</span></span>  
  
|<span data-ttu-id="afcc1-107">Член</span><span class="sxs-lookup"><span data-stu-id="afcc1-107">Member</span></span>|<span data-ttu-id="afcc1-108">Описание</span><span class="sxs-lookup"><span data-stu-id="afcc1-108">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="afcc1-109">Идентификатор для алгоритма подписи (типа `ALG_ID` , как определено в винкрипт. h) открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="afcc1-109">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="afcc1-110">Идентификатор для хэш-алгоритма (типа `ALG_ID` , как определено в винкрипт. h) открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="afcc1-110">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="afcc1-111">Длина ключа в байтах.</span><span class="sxs-lookup"><span data-stu-id="afcc1-111">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="afcc1-112">Массив байтов переменной длины, который содержит значение ключа в формате, возвращенном CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="afcc1-112">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afcc1-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="afcc1-113">Remarks</span></span>  

 <span data-ttu-id="afcc1-114">`PublicKeyBlob`Структура используется [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)и другими функциями строгого имени для представления открытого ключа пары открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="afcc1-114">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afcc1-115">Требования</span><span class="sxs-lookup"><span data-stu-id="afcc1-115">Requirements</span></span>  

 <span data-ttu-id="afcc1-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afcc1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afcc1-117">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="afcc1-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="afcc1-118">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="afcc1-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="afcc1-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afcc1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afcc1-120">См. также</span><span class="sxs-lookup"><span data-stu-id="afcc1-120">See also</span></span>

- [<span data-ttu-id="afcc1-121">Функция StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="afcc1-121">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="afcc1-122">Функция StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="afcc1-122">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
