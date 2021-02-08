---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameTokenFromAssembly'
title: Метод ICLRStrongName::StrongNameTokenFromAssembly
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
ms.openlocfilehash: 520d327767f91763f8f2b3efea098c7c2790939e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781822"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="cf6fd-103">Метод ICLRStrongName::StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="cf6fd-103">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>

<span data-ttu-id="cf6fd-104">Создает маркер строгого имени из указанного файла сборки.</span><span class="sxs-lookup"><span data-stu-id="cf6fd-104">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf6fd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cf6fd-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf6fd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cf6fd-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="cf6fd-107">окне Путь к переносимому исполняемому файлу (PE) для сборки.</span><span class="sxs-lookup"><span data-stu-id="cf6fd-107">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="cf6fd-108">заполняет Возвращенный маркер строгого имени.</span><span class="sxs-lookup"><span data-stu-id="cf6fd-108">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="cf6fd-109">заполняет Размер (в байтах) маркера строгого имени.</span><span class="sxs-lookup"><span data-stu-id="cf6fd-109">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf6fd-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cf6fd-110">Return Value</span></span>  

 <span data-ttu-id="cf6fd-111">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="cf6fd-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf6fd-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="cf6fd-112">Remarks</span></span>  

 <span data-ttu-id="cf6fd-113">Маркер строгого имени — это сокращенная форма открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="cf6fd-113">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="cf6fd-114">Маркер представляет собой 64-разрядный хэш, созданный из открытого ключа, используемого для подписания сборки.</span><span class="sxs-lookup"><span data-stu-id="cf6fd-114">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="cf6fd-115">Токен является частью строгого имени сборки и может быть считан из метаданных сборки.</span><span class="sxs-lookup"><span data-stu-id="cf6fd-115">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="cf6fd-116">После создания маркера следует вызвать метод [метод iclrstrongname:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) , чтобы освободить выделенную память.</span><span class="sxs-lookup"><span data-stu-id="cf6fd-116">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf6fd-117">Требования</span><span class="sxs-lookup"><span data-stu-id="cf6fd-117">Requirements</span></span>  

 <span data-ttu-id="cf6fd-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf6fd-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf6fd-119">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="cf6fd-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cf6fd-120">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf6fd-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf6fd-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf6fd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf6fd-122">См. также</span><span class="sxs-lookup"><span data-stu-id="cf6fd-122">See also</span></span>

- [<span data-ttu-id="cf6fd-123">Метод StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="cf6fd-123">StrongNameTokenFromAssemblyEx Method</span></span>](iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="cf6fd-124">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="cf6fd-124">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
