---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: GetHashFromBlob'
title: Метод ICLRStrongName::GetHashFromBlob
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type:
- apiref
ms.openlocfilehash: 20d03184f57e77741e656575038e426ee37968f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637070"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="46122-103">Метод ICLRStrongName::GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="46122-103">ICLRStrongName::GetHashFromBlob Method</span></span>

<span data-ttu-id="46122-104">Получает хэш сборки по указанному адресу памяти с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="46122-104">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46122-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="46122-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46122-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="46122-106">Parameters</span></span>  

 `pbBlob`  
 <span data-ttu-id="46122-107">окне Указатель на адрес блока памяти, который необходимо хэшировать.</span><span class="sxs-lookup"><span data-stu-id="46122-107">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="46122-108">окне Длина блока памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="46122-108">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="46122-109">[вход, выход] Константа, указывающая хэш-алгоритм.</span><span class="sxs-lookup"><span data-stu-id="46122-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="46122-110">Используйте нуль для алгоритма по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="46122-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="46122-111">заполняет Возвращаемый буфер хэша.</span><span class="sxs-lookup"><span data-stu-id="46122-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="46122-112">окне Запрошенный максимальный размер `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="46122-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="46122-113">заполняет Размер возвращаемого объекта (в байтах) `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="46122-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46122-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="46122-114">Return Value</span></span>  

 <span data-ttu-id="46122-115">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="46122-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46122-116">Требования</span><span class="sxs-lookup"><span data-stu-id="46122-116">Requirements</span></span>  

 <span data-ttu-id="46122-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46122-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46122-118">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="46122-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="46122-119">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="46122-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46122-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46122-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46122-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="46122-121">See also</span></span>

- [<span data-ttu-id="46122-122">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="46122-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
