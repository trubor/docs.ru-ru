---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameGetPublicKey'
title: Метод ICLRStrongName::StrongNameGetPublicKey
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: 7be64e145f1e26a1260e2b23fd9fe5f97e289478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799607"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="20cf3-103">Метод ICLRStrongName::StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="20cf3-103">ICLRStrongName::StrongNameGetPublicKey Method</span></span>

<span data-ttu-id="20cf3-104">Возвращает открытый ключ из пары открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="20cf3-104">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="20cf3-105">Пара ключей может быть задана как имя контейнера ключей в поставщике служб шифрования (CSP) или как необработанная коллекция байтов.</span><span class="sxs-lookup"><span data-stu-id="20cf3-105">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20cf3-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="20cf3-106">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20cf3-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="20cf3-107">Parameters</span></span>  

 `szKeyContainer`  
 <span data-ttu-id="20cf3-108">окне Имя контейнера ключей, содержащего пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="20cf3-108">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="20cf3-109">Если `pbKeyBlob` значение равно null, `szKeyContainer` необходимо указать допустимый контейнер в CSP.</span><span class="sxs-lookup"><span data-stu-id="20cf3-109">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="20cf3-110">В этом случае метод [метод iclrstrongname:: StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md) извлекает открытый ключ из пары ключей, хранящейся в контейнере.</span><span class="sxs-lookup"><span data-stu-id="20cf3-110">In this case, the [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="20cf3-111">Если значение не равно `pbKeyBlob` null, предполагается, что пара ключей содержится в большом двоичном объекте Key (BLOB).</span><span class="sxs-lookup"><span data-stu-id="20cf3-111">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="20cf3-112">Ключи должны состоять из 1024-разрядных ключей подписывания Ривест-Шамир-Адельман (RSA).</span><span class="sxs-lookup"><span data-stu-id="20cf3-112">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="20cf3-113">В настоящее время не поддерживаются никакие другие типы ключей.</span><span class="sxs-lookup"><span data-stu-id="20cf3-113">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="20cf3-114">окне Указатель на пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="20cf3-114">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="20cf3-115">Эта пара имеет формат, созданный `CryptExportKey` функцией Win32.</span><span class="sxs-lookup"><span data-stu-id="20cf3-115">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="20cf3-116">Если аргумент `pbKeyBlob` имеет значение null, предполагается, что контейнер ключей, заданный параметром, `szKeyContainer` содержит пару ключей.</span><span class="sxs-lookup"><span data-stu-id="20cf3-116">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="20cf3-117">окне Размер (в байтах) `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="20cf3-117">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="20cf3-118">заполняет Возвращенный большой двоичный объект открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="20cf3-118">[out] The returned public key BLOB.</span></span> <span data-ttu-id="20cf3-119">`ppbPublicKeyBlob`Параметр выделяется средой CLR и возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="20cf3-119">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="20cf3-120">Вызывающий объект должен освободить память с помощью метода [метод iclrstrongname:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="20cf3-120">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="20cf3-121">заполняет Размер возвращенного большого двоичного объекта открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="20cf3-121">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20cf3-122">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="20cf3-122">Return Value</span></span>  

 <span data-ttu-id="20cf3-123">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="20cf3-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20cf3-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="20cf3-124">Remarks</span></span>  

 <span data-ttu-id="20cf3-125">Открытый ключ содержится в структуре [публиккэйблоб](../strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="20cf3-125">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20cf3-126">Требования</span><span class="sxs-lookup"><span data-stu-id="20cf3-126">Requirements</span></span>  

 <span data-ttu-id="20cf3-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20cf3-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20cf3-128">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="20cf3-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="20cf3-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20cf3-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20cf3-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20cf3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20cf3-131">См. также</span><span class="sxs-lookup"><span data-stu-id="20cf3-131">See also</span></span>

- [<span data-ttu-id="20cf3-132">Метод StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="20cf3-132">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="20cf3-133">Структура PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="20cf3-133">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="20cf3-134">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="20cf3-134">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
