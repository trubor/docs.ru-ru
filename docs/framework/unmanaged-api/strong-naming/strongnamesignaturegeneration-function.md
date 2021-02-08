---
description: Дополнительные сведения о функции StrongNameSignatureGeneration
title: Функция StrongNameSignatureGeneration
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
ms.openlocfilehash: 6f5a164e73af743cdd13390c60d00d553e5e0312
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798905"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="82554-103">Функция StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="82554-103">StrongNameSignatureGeneration Function</span></span>

<span data-ttu-id="82554-104">Создает подпись строгого имени для указанной сборки.</span><span class="sxs-lookup"><span data-stu-id="82554-104">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="82554-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="82554-105">This function has been deprecated.</span></span> <span data-ttu-id="82554-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) .</span><span class="sxs-lookup"><span data-stu-id="82554-106">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82554-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="82554-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82554-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="82554-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="82554-109">окне Путь к файлу, содержащему манифест сборки, для которой будет создана подпись строгого имени.</span><span class="sxs-lookup"><span data-stu-id="82554-109">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="82554-110">окне Имя контейнера ключей, содержащего пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="82554-110">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="82554-111">Если `pbKeyBlob` параметр имеет значение null, `wszKeyContainer` необходимо указать допустимый контейнер в поставщике служб шифрования (CSP).</span><span class="sxs-lookup"><span data-stu-id="82554-111">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="82554-112">В этом случае для подписания файла используется пара ключей, хранящаяся в контейнере.</span><span class="sxs-lookup"><span data-stu-id="82554-112">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="82554-113">Если значение не равно `pbKeyBlob` null, предполагается, что пара ключей содержится в большом двоичном объекте Key (BLOB).</span><span class="sxs-lookup"><span data-stu-id="82554-113">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="82554-114">Ключи должны состоять из 1024-разрядных ключей подписывания Ривест-Шамир-Адельман (RSA).</span><span class="sxs-lookup"><span data-stu-id="82554-114">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="82554-115">В настоящее время не поддерживаются никакие другие типы ключей.</span><span class="sxs-lookup"><span data-stu-id="82554-115">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="82554-116">окне Указатель на пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="82554-116">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="82554-117">Эта пара имеет формат, созданный `CryptExportKey` функцией Win32.</span><span class="sxs-lookup"><span data-stu-id="82554-117">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="82554-118">Если аргумент `pbKeyBlob` имеет значение null, предполагается, что контейнер ключей, заданный параметром, `wszKeyContainer` содержит пару ключей.</span><span class="sxs-lookup"><span data-stu-id="82554-118">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="82554-119">окне Размер (в байтах) `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="82554-119">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="82554-120">заполняет Указатель на расположение, в которое среда CLR возвращает подпись.</span><span class="sxs-lookup"><span data-stu-id="82554-120">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="82554-121">Если `ppbSignatureBlob` параметр имеет значение null, среда выполнения сохраняет подпись в файле, указанном параметром `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="82554-121">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="82554-122">Если значение не равно `ppbSignatureBlob` null, среда CLR выделяет пространство, в которое возвращается подпись.</span><span class="sxs-lookup"><span data-stu-id="82554-122">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="82554-123">Вызывающий объект должен освободить это пространство с помощью функции [StrongNameFreeBuffer](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="82554-123">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="82554-124">заполняет Размер возвращенной сигнатуры в байтах.</span><span class="sxs-lookup"><span data-stu-id="82554-124">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82554-125">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="82554-125">Return Value</span></span>  

 <span data-ttu-id="82554-126">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="82554-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82554-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="82554-127">Remarks</span></span>  

 <span data-ttu-id="82554-128">Укажите значение NULL для `wszFilePath` , чтобы вычислить размер подписи без создания подписи.</span><span class="sxs-lookup"><span data-stu-id="82554-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="82554-129">Подпись может храниться непосредственно в файле или возвращаться вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="82554-129">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="82554-130">Если `StrongNameSignatureGeneration` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="82554-130">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82554-131">Требования</span><span class="sxs-lookup"><span data-stu-id="82554-131">Requirements</span></span>  

 <span data-ttu-id="82554-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82554-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82554-133">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="82554-133">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="82554-134">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82554-134">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82554-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82554-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82554-136">См. также</span><span class="sxs-lookup"><span data-stu-id="82554-136">See also</span></span>

- [<span data-ttu-id="82554-137">Метод StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="82554-137">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="82554-138">Метод StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="82554-138">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="82554-139">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="82554-139">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
