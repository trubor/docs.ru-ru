---
description: Дополнительные сведения о методе StrongNameGetPublicKeyEx
title: Метод StrongNameGetPublicKeyEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: bc9d40afc34509f852a0961823e264255125fa16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679307"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="acd36-103">Метод StrongNameGetPublicKeyEx</span><span class="sxs-lookup"><span data-stu-id="acd36-103">StrongNameGetPublicKeyEx Method</span></span>

<span data-ttu-id="acd36-104">Получает открытый ключ из пары открытого и закрытого ключей и задает алгоритм хеширования и алгоритм подписи.</span><span class="sxs-lookup"><span data-stu-id="acd36-104">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acd36-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="acd36-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acd36-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="acd36-106">Parameters</span></span>  

 `pwzKeyContainer`  
 <span data-ttu-id="acd36-107">окне Имя контейнера ключей, содержащего пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="acd36-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="acd36-108">Если `pbKeyBlob` параметр имеет значение null, `szKeyContainer` необходимо указать допустимый контейнер в поставщике служб шифрования (CSP).</span><span class="sxs-lookup"><span data-stu-id="acd36-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="acd36-109">В этом случае `StrongNameGetPublicKeyEx` метод извлекает открытый ключ из пары ключей, хранящихся в контейнере.</span><span class="sxs-lookup"><span data-stu-id="acd36-109">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="acd36-110">Если значение не равно `pbKeyBlob` null, предполагается, что пара ключей содержится в большом двоичном объекте Key (BLOB).</span><span class="sxs-lookup"><span data-stu-id="acd36-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="acd36-111">Ключи должны состоять из 1024-разрядных ключей подписывания Ривест-Шамир-Адельман (RSA).</span><span class="sxs-lookup"><span data-stu-id="acd36-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="acd36-112">В настоящее время не поддерживаются никакие другие типы ключей.</span><span class="sxs-lookup"><span data-stu-id="acd36-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="acd36-113">окне Указатель на пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="acd36-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="acd36-114">Эта пара имеет формат, созданный `CryptExportKey` функцией Win32.</span><span class="sxs-lookup"><span data-stu-id="acd36-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="acd36-115">Если аргумент `pbKeyBlob` имеет значение null, предполагается, что контейнер ключей, заданный параметром, `szKeyContainer` содержит пару ключей.</span><span class="sxs-lookup"><span data-stu-id="acd36-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="acd36-116">окне Размер (в байтах) `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="acd36-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="acd36-117">заполняет Возвращенный большой двоичный объект открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="acd36-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="acd36-118">`ppbPublicKeyBlob`Параметр выделяется средой CLR и возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="acd36-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="acd36-119">Вызывающий объект должен освободить память с помощью метода [метод iclrstrongname:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="acd36-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="acd36-120">заполняет Размер возвращенного большого двоичного объекта открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="acd36-120">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="acd36-121">окне Хэш-алгоритм сборки.</span><span class="sxs-lookup"><span data-stu-id="acd36-121">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="acd36-122">Список допустимых значений см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="acd36-122">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="acd36-123">окне Зарезервировано для будущего использования; по умолчанию принимает значение null.</span><span class="sxs-lookup"><span data-stu-id="acd36-123">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acd36-124">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="acd36-124">Return Value</span></span>  

 <span data-ttu-id="acd36-125">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="acd36-125">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acd36-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="acd36-126">Remarks</span></span>  

 <span data-ttu-id="acd36-127">Открытый ключ содержится в структуре [публиккэйблоб](../strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="acd36-127">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acd36-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="acd36-128">Remarks</span></span>  

 <span data-ttu-id="acd36-129">В следующей таблице показан набор допустимых значений для `uHashAlgId` параметра.</span><span class="sxs-lookup"><span data-stu-id="acd36-129">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="acd36-130">Имя</span><span class="sxs-lookup"><span data-stu-id="acd36-130">Name</span></span>|<span data-ttu-id="acd36-131">Значение</span><span class="sxs-lookup"><span data-stu-id="acd36-131">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="acd36-132">None</span><span class="sxs-lookup"><span data-stu-id="acd36-132">None</span></span>|<span data-ttu-id="acd36-133">0</span><span class="sxs-lookup"><span data-stu-id="acd36-133">0</span></span>|  
|<span data-ttu-id="acd36-134">SHA-1</span><span class="sxs-lookup"><span data-stu-id="acd36-134">SHA-1</span></span>|<span data-ttu-id="acd36-135">0x8004</span><span class="sxs-lookup"><span data-stu-id="acd36-135">0x8004</span></span>|  
|<span data-ttu-id="acd36-136">SHA-256</span><span class="sxs-lookup"><span data-stu-id="acd36-136">SHA-256</span></span>|<span data-ttu-id="acd36-137">0x800c</span><span class="sxs-lookup"><span data-stu-id="acd36-137">0x800c</span></span>|  
|<span data-ttu-id="acd36-138">SHA-384</span><span class="sxs-lookup"><span data-stu-id="acd36-138">SHA-384</span></span>|<span data-ttu-id="acd36-139">0x800d</span><span class="sxs-lookup"><span data-stu-id="acd36-139">0x800d</span></span>|  
|<span data-ttu-id="acd36-140">SHA-512</span><span class="sxs-lookup"><span data-stu-id="acd36-140">SHA-512</span></span>|<span data-ttu-id="acd36-141">0x800e</span><span class="sxs-lookup"><span data-stu-id="acd36-141">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="acd36-142">Требования</span><span class="sxs-lookup"><span data-stu-id="acd36-142">Requirements</span></span>  

 <span data-ttu-id="acd36-143">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acd36-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acd36-144">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="acd36-144">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="acd36-145">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="acd36-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="acd36-146">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acd36-146">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd36-147">См. также</span><span class="sxs-lookup"><span data-stu-id="acd36-147">See also</span></span>

- [<span data-ttu-id="acd36-148">Метод StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="acd36-148">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="acd36-149">Структура PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="acd36-149">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="acd36-150">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="acd36-150">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
- [<span data-ttu-id="acd36-151">Метод StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="acd36-151">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
