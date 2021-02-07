---
description: Дополнительные сведения о функции StrongNameGetPublicKey
title: Функция StrongNameGetPublicKey
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
ms.openlocfilehash: c94ffdd20e83b03da27b2f44ebbc279cfd8b8afc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670576"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="d9932-103">Функция StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="d9932-103">StrongNameGetPublicKey Function</span></span>

<span data-ttu-id="d9932-104">Получает открытый ключ из пары закрытого и открытого ключей.</span><span class="sxs-lookup"><span data-stu-id="d9932-104">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="d9932-105">Пара ключей может быть задана как имя контейнера ключей в поставщике служб шифрования (CSP) или как необработанная коллекция байтов.</span><span class="sxs-lookup"><span data-stu-id="d9932-105">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="d9932-106">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="d9932-106">This function has been deprecated.</span></span> <span data-ttu-id="d9932-107">Используйте вместо этого метод [метод iclrstrongname:: StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d9932-107">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9932-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9932-108">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9932-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="d9932-109">Parameters</span></span>  

 `szKeyContainer`  
 <span data-ttu-id="d9932-110">окне Имя контейнера ключей, содержащего пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="d9932-110">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="d9932-111">Если `pbKeyBlob` значение равно null, `szKeyContainer` необходимо указать допустимый контейнер в CSP.</span><span class="sxs-lookup"><span data-stu-id="d9932-111">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="d9932-112">В этом случае `StrongNameGetPublicKey` извлекает открытый ключ из пары ключей, хранящейся в контейнере.</span><span class="sxs-lookup"><span data-stu-id="d9932-112">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="d9932-113">Если значение не равно `pbKeyBlob` null, предполагается, что пара ключей содержится в большом двоичном объекте Key (BLOB).</span><span class="sxs-lookup"><span data-stu-id="d9932-113">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="d9932-114">Ключи должны состоять из 1024-разрядных ключей подписывания Ривест-Шамир-Адельман (RSA).</span><span class="sxs-lookup"><span data-stu-id="d9932-114">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="d9932-115">В настоящее время не поддерживаются никакие другие типы ключей.</span><span class="sxs-lookup"><span data-stu-id="d9932-115">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="d9932-116">окне Указатель на пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="d9932-116">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="d9932-117">Эта пара имеет формат, созданный `CryptExportKey` функцией Win32.</span><span class="sxs-lookup"><span data-stu-id="d9932-117">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="d9932-118">Если аргумент `pbKeyBlob` имеет значение null, предполагается, что контейнер ключей, заданный параметром, `szKeyContainer` содержит пару ключей.</span><span class="sxs-lookup"><span data-stu-id="d9932-118">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="d9932-119">окне Размер (в байтах) `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="d9932-119">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="d9932-120">заполняет Возвращенный большой двоичный объект открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="d9932-120">[out] The returned public key BLOB.</span></span> <span data-ttu-id="d9932-121">`ppbPublicKeyBlob`Параметр выделяется средой CLR и возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="d9932-121">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="d9932-122">Вызывающий объект должен освободить память с помощью функции [StrongNameFreeBuffer](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="d9932-122">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="d9932-123">заполняет Размер возвращенного большого двоичного объекта открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="d9932-123">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9932-124">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d9932-124">Return Value</span></span>  

 <span data-ttu-id="d9932-125">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="d9932-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9932-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="d9932-126">Remarks</span></span>  

 <span data-ttu-id="d9932-127">Открытый ключ содержится в структуре [публиккэйблоб](publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="d9932-127">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="d9932-128">Если `StrongNameGetPublicKey` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="d9932-128">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9932-129">Требования</span><span class="sxs-lookup"><span data-stu-id="d9932-129">Requirements</span></span>  

 <span data-ttu-id="d9932-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9932-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9932-131">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="d9932-131">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d9932-132">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9932-132">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d9932-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9932-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9932-134">См. также</span><span class="sxs-lookup"><span data-stu-id="d9932-134">See also</span></span>

- [<span data-ttu-id="d9932-135">Метод StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="d9932-135">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="d9932-136">Метод StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="d9932-136">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="d9932-137">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="d9932-137">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="d9932-138">Структура PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="d9932-138">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
