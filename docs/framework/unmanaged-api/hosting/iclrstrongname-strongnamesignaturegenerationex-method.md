---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameSignatureGenerationEx'
title: Метод ICLRStrongName::StrongNameSignatureGenerationEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
ms.openlocfilehash: 911f55aa509c25eb0d95d6d2a31c9f715af2080d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781874"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="dd0f7-103">Метод ICLRStrongName::StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="dd0f7-103">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>

<span data-ttu-id="dd0f7-104">Создает подпись строгого имени для указанной сборки в соответствии с заданными флагами.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-104">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd0f7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dd0f7-105">Syntax</span></span>  
  
```cpp
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd0f7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dd0f7-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="dd0f7-107">окне Путь к файлу, содержащему манифест сборки, для которой будет создана подпись строгого имени.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-107">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="dd0f7-108">окне Имя контейнера ключей, содержащего пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-108">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="dd0f7-109">Если `pbKeyBlob` параметр имеет значение null, `wszKeyContainer` необходимо указать допустимый контейнер в поставщике служб шифрования (CSP).</span><span class="sxs-lookup"><span data-stu-id="dd0f7-109">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="dd0f7-110">В этом случае для подписания файла используется пара ключей, хранящаяся в контейнере.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-110">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="dd0f7-111">Если значение не равно `pbKeyBlob` null, предполагается, что пара ключей содержится в большом двоичном объекте Key (BLOB).</span><span class="sxs-lookup"><span data-stu-id="dd0f7-111">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="dd0f7-112">окне Указатель на пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="dd0f7-113">Эта пара имеет формат, созданный `CryptExportKey` функцией Win32.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="dd0f7-114">Если аргумент `pbKeyBlob` имеет значение null, предполагается, что контейнер ключей, заданный параметром, `wszKeyContainer` содержит пару ключей.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-114">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="dd0f7-115">окне Размер (в байтах) `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="dd0f7-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="dd0f7-116">заполняет Указатель на расположение, в которое среда CLR возвращает подпись.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-116">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="dd0f7-117">Если `ppbSignatureBlob` параметр имеет значение null, среда выполнения сохраняет подпись в файле, указанном параметром `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="dd0f7-117">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="dd0f7-118">Если значение не равно `ppbSignatureBlob` null, среда CLR выделяет пространство, в которое возвращается подпись.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-118">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="dd0f7-119">Вызывающий объект должен освободить это пространство с помощью метода [метод iclrstrongname:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dd0f7-119">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="dd0f7-120">заполняет Размер возвращенной сигнатуры в байтах.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-120">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dd0f7-121">окне Одно или несколько из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="dd0f7-121">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="dd0f7-122">`SN_SIGN_ALL_FILES` (0x00000001) — повторное вычисление всех хэшей для связанных модулей.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-122">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="dd0f7-123">`SN_TEST_SIGN` (0x00000002) — Тестовая подпись сборки.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-123">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd0f7-124">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dd0f7-124">Return Value</span></span>  

 <span data-ttu-id="dd0f7-125">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="dd0f7-125">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd0f7-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="dd0f7-126">Remarks</span></span>  

 <span data-ttu-id="dd0f7-127">Укажите значение NULL для `wszFilePath` , чтобы вычислить размер подписи без создания подписи.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="dd0f7-128">Подпись может храниться непосредственно в файле или возвращаться вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-128">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="dd0f7-129">Если `SN_SIGN_ALL_FILES` указан параметр, но открытый ключ не включен (и имеет `pbKeyBlob` `wszFilePath` значение null), хэши для связанных модулей пересчитываются, но сборка не подписывается повторно.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-129">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="dd0f7-130">Если `SN_TEST_SIGN` указан параметр, заголовок среды CLR не изменяется, чтобы указать, что сборка подписана строгим именем.</span><span class="sxs-lookup"><span data-stu-id="dd0f7-130">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd0f7-131">Требования</span><span class="sxs-lookup"><span data-stu-id="dd0f7-131">Requirements</span></span>  

 <span data-ttu-id="dd0f7-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd0f7-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd0f7-133">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="dd0f7-133">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dd0f7-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd0f7-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd0f7-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd0f7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd0f7-136">См. также</span><span class="sxs-lookup"><span data-stu-id="dd0f7-136">See also</span></span>

- [<span data-ttu-id="dd0f7-137">Метод StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="dd0f7-137">StrongNameSignatureGeneration Method</span></span>](iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="dd0f7-138">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="dd0f7-138">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
