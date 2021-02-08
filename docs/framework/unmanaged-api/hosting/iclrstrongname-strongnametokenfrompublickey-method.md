---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameTokenFromPublicKey'
title: Метод ICLRStrongName::StrongNameTokenFromPublicKey
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: de245b151e5ca016a00793a8901c0fd990a3f804
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789749"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="081f7-103">Метод ICLRStrongName::StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="081f7-103">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>

<span data-ttu-id="081f7-104">Возвращает маркер, представляющий открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="081f7-104">Gets a token that represents a public key.</span></span> <span data-ttu-id="081f7-105">Маркер строгого имени — это сокращенная форма открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="081f7-105">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="081f7-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="081f7-106">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="081f7-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="081f7-107">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="081f7-108">окне Структура типа [публиккэйблоб](../strong-naming/publickeyblob-structure.md) , содержащая открытую часть пары ключей, используемую для создания подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="081f7-108">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="081f7-109">окне Размер (в байтах) `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="081f7-109">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="081f7-110">заполняет Маркер строгого имени, соответствующий переданному ключу `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="081f7-110">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="081f7-111">Среда CLR выделяет память, в которую возвращается маркер.</span><span class="sxs-lookup"><span data-stu-id="081f7-111">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="081f7-112">Вызывающий объект должен освободить эту память с помощью метода [метод iclrstrongname:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="081f7-112">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="081f7-113">заполняет Размер возвращенного маркера строгого имени в байтах.</span><span class="sxs-lookup"><span data-stu-id="081f7-113">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="081f7-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="081f7-114">Return Value</span></span>  

 <span data-ttu-id="081f7-115">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="081f7-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="081f7-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="081f7-116">Remarks</span></span>  

 <span data-ttu-id="081f7-117">Маркер строгого имени — это сокращенная форма открытого ключа, используемая для экономии места при хранении ключевых сведений в метаданных.</span><span class="sxs-lookup"><span data-stu-id="081f7-117">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="081f7-118">В частности, маркеры строгого имени используются в ссылках на сборки для ссылки на зависимую сборку.</span><span class="sxs-lookup"><span data-stu-id="081f7-118">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="081f7-119">Требования</span><span class="sxs-lookup"><span data-stu-id="081f7-119">Requirements</span></span>  

 <span data-ttu-id="081f7-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="081f7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="081f7-121">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="081f7-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="081f7-122">**Библиотека:** Включается в качестве ресурса в mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="081f7-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="081f7-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="081f7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="081f7-124">См. также</span><span class="sxs-lookup"><span data-stu-id="081f7-124">See also</span></span>

- [<span data-ttu-id="081f7-125">Метод StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="081f7-125">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="081f7-126">Структура PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="081f7-126">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="081f7-127">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="081f7-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
