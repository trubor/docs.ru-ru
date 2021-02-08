---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameKeyInstall'
title: Метод ICLRStrongName::StrongNameKeyInstall
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
ms.openlocfilehash: 8f9e7bfebff555a6430a3970c8ee1c481e341f58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799516"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="52b3b-103">Метод ICLRStrongName::StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="52b3b-103">ICLRStrongName::StrongNameKeyInstall Method</span></span>

<span data-ttu-id="52b3b-104">Импортирует пару открытого и закрытого ключей в контейнер.</span><span class="sxs-lookup"><span data-stu-id="52b3b-104">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52b3b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="52b3b-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52b3b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="52b3b-106">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="52b3b-107">окне Имя контейнера ключей.</span><span class="sxs-lookup"><span data-stu-id="52b3b-107">[in] The name of the key container.</span></span> <span data-ttu-id="52b3b-108">`wszKeyContainer` значение должно быть непустой строкой.</span><span class="sxs-lookup"><span data-stu-id="52b3b-108">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="52b3b-109">окне Пара двоичных ключей.</span><span class="sxs-lookup"><span data-stu-id="52b3b-109">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="52b3b-110">окне Размер (в байтах) `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="52b3b-110">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52b3b-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="52b3b-111">Return Value</span></span>  

 <span data-ttu-id="52b3b-112">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="52b3b-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52b3b-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="52b3b-113">Remarks</span></span>  

 <span data-ttu-id="52b3b-114">Чтобы удалить контейнер ключей, используйте метод [метод iclrstrongname:: StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="52b3b-114">Use the [ICLRStrongName::StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52b3b-115">Требования</span><span class="sxs-lookup"><span data-stu-id="52b3b-115">Requirements</span></span>  

 <span data-ttu-id="52b3b-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52b3b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52b3b-117">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="52b3b-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="52b3b-118">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52b3b-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52b3b-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52b3b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b3b-120">См. также</span><span class="sxs-lookup"><span data-stu-id="52b3b-120">See also</span></span>

- [<span data-ttu-id="52b3b-121">Метод StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="52b3b-121">StrongNameKeyDelete Method</span></span>](iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="52b3b-122">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="52b3b-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
