---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameTokenFromAssemblyEx'
title: Метод ICLRStrongName::StrongNameTokenFromAssemblyEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
ms.openlocfilehash: e0a05d2aa0b41c370bde2bbff5367f25a1b13322
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781809"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="54dc6-103">Метод ICLRStrongName::StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="54dc6-103">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>

<span data-ttu-id="54dc6-104">Создает маркер строгого имени из указанного файла сборки и возвращает открытый ключ, который представляет маркер.</span><span class="sxs-lookup"><span data-stu-id="54dc6-104">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54dc6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="54dc6-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54dc6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="54dc6-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="54dc6-107">окне Путь к переносимому исполняемому файлу (PE) для сборки.</span><span class="sxs-lookup"><span data-stu-id="54dc6-107">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="54dc6-108">заполняет Возвращенный маркер строгого имени.</span><span class="sxs-lookup"><span data-stu-id="54dc6-108">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="54dc6-109">заполняет Размер (в байтах) маркера строгого имени.</span><span class="sxs-lookup"><span data-stu-id="54dc6-109">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="54dc6-110">заполняет Возвращаемый открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="54dc6-110">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="54dc6-111">заполняет Размер открытого ключа в байтах.</span><span class="sxs-lookup"><span data-stu-id="54dc6-111">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54dc6-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="54dc6-112">Return Value</span></span>  

 <span data-ttu-id="54dc6-113">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="54dc6-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54dc6-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="54dc6-114">Remarks</span></span>  

 <span data-ttu-id="54dc6-115">Маркер строгого имени — это сокращенная форма открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="54dc6-115">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="54dc6-116">Маркер представляет собой 64-разрядный хэш, созданный из открытого ключа, используемого для подписания сборки.</span><span class="sxs-lookup"><span data-stu-id="54dc6-116">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="54dc6-117">Токен является частью строгого имени сборки и может быть считан из метаданных сборки.</span><span class="sxs-lookup"><span data-stu-id="54dc6-117">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="54dc6-118">После извлечения ключа и создания маркера следует вызвать метод [метод iclrstrongname:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) , чтобы освободить выделенную память.</span><span class="sxs-lookup"><span data-stu-id="54dc6-118">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54dc6-119">Требования</span><span class="sxs-lookup"><span data-stu-id="54dc6-119">Requirements</span></span>  

 <span data-ttu-id="54dc6-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54dc6-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54dc6-121">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="54dc6-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="54dc6-122">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54dc6-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54dc6-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54dc6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54dc6-124">См. также</span><span class="sxs-lookup"><span data-stu-id="54dc6-124">See also</span></span>

- [<span data-ttu-id="54dc6-125">Метод StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="54dc6-125">StrongNameTokenFromAssembly Method</span></span>](iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="54dc6-126">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="54dc6-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
