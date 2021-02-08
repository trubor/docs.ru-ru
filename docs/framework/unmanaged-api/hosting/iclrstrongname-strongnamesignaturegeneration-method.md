---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameSignatureGeneration'
title: Метод ICLRStrongName::StrongNameSignatureGeneration
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: ea8a6a9ea1e85af9d4e78cc950a02dbbc6815e4c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781887"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="9152a-103">Метод ICLRStrongName::StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="9152a-103">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>

<span data-ttu-id="9152a-104">Создает подпись строгого имени для указанной сборки.</span><span class="sxs-lookup"><span data-stu-id="9152a-104">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9152a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9152a-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9152a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9152a-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="9152a-107">окне Путь к файлу, содержащему манифест сборки, для которой будет создана подпись строгого имени.</span><span class="sxs-lookup"><span data-stu-id="9152a-107">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="9152a-108">окне Имя контейнера ключей, содержащего пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="9152a-108">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="9152a-109">Если `pbKeyBlob` параметр имеет значение null, `wszKeyContainer` необходимо указать допустимый контейнер в поставщике служб шифрования (CSP).</span><span class="sxs-lookup"><span data-stu-id="9152a-109">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="9152a-110">В этом случае для подписания файла используется пара ключей, хранящаяся в контейнере.</span><span class="sxs-lookup"><span data-stu-id="9152a-110">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="9152a-111">Если значение не равно `pbKeyBlob` null, предполагается, что пара ключей содержится в большом двоичном объекте Key (BLOB).</span><span class="sxs-lookup"><span data-stu-id="9152a-111">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="9152a-112">Ключи должны состоять из 1024-разрядных ключей подписывания Ривест-Шамир-Адельман (RSA).</span><span class="sxs-lookup"><span data-stu-id="9152a-112">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="9152a-113">В настоящее время не поддерживаются никакие другие типы ключей.</span><span class="sxs-lookup"><span data-stu-id="9152a-113">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="9152a-114">окне Указатель на пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="9152a-114">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="9152a-115">Эта пара имеет формат, созданный `CryptExportKey` функцией Win32.</span><span class="sxs-lookup"><span data-stu-id="9152a-115">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="9152a-116">Если аргумент `pbKeyBlob` имеет значение null, предполагается, что контейнер ключей, заданный параметром, `wszKeyContainer` содержит пару ключей.</span><span class="sxs-lookup"><span data-stu-id="9152a-116">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="9152a-117">окне Размер (в байтах) `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="9152a-117">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="9152a-118">заполняет Указатель на расположение, в которое среда CLR возвращает подпись.</span><span class="sxs-lookup"><span data-stu-id="9152a-118">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="9152a-119">Если `ppbSignatureBlob` параметр имеет значение null, среда выполнения сохраняет подпись в файле, указанном параметром `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="9152a-119">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="9152a-120">Если значение не равно `ppbSignatureBlob` null, среда CLR выделяет пространство, в которое возвращается подпись.</span><span class="sxs-lookup"><span data-stu-id="9152a-120">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="9152a-121">Вызывающий объект должен освободить это пространство с помощью метода [метод iclrstrongname:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9152a-121">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="9152a-122">заполняет Размер возвращенной сигнатуры в байтах.</span><span class="sxs-lookup"><span data-stu-id="9152a-122">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9152a-123">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9152a-123">Return Value</span></span>  

 <span data-ttu-id="9152a-124">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="9152a-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9152a-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="9152a-125">Remarks</span></span>  

 <span data-ttu-id="9152a-126">Укажите значение NULL для `wszFilePath` , чтобы вычислить размер подписи без создания подписи.</span><span class="sxs-lookup"><span data-stu-id="9152a-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="9152a-127">Подпись может храниться непосредственно в файле или возвращаться вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="9152a-127">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9152a-128">Требования</span><span class="sxs-lookup"><span data-stu-id="9152a-128">Requirements</span></span>  

 <span data-ttu-id="9152a-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9152a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9152a-130">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="9152a-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9152a-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9152a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9152a-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9152a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9152a-133">См. также</span><span class="sxs-lookup"><span data-stu-id="9152a-133">See also</span></span>

- [<span data-ttu-id="9152a-134">Метод StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="9152a-134">StrongNameSignatureGenerationEx Method</span></span>](iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="9152a-135">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9152a-135">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
