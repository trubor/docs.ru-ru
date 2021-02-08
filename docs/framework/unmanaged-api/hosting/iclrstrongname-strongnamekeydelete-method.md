---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameKeyDelete'
title: Метод ICLRStrongName::StrongNameKeyDelete
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
ms.openlocfilehash: 5b782785921eb24394db53d29a66600a3867b489
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799581"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="dc8c5-103">Метод ICLRStrongName::StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="dc8c5-103">ICLRStrongName::StrongNameKeyDelete Method</span></span>

<span data-ttu-id="dc8c5-104">Удаляет указанный контейнер ключей.</span><span class="sxs-lookup"><span data-stu-id="dc8c5-104">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc8c5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dc8c5-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc8c5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dc8c5-106">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="dc8c5-107">окне Имя удаляемого контейнера ключей.</span><span class="sxs-lookup"><span data-stu-id="dc8c5-107">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc8c5-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dc8c5-108">Return Value</span></span>  

 <span data-ttu-id="dc8c5-109">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="dc8c5-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc8c5-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="dc8c5-110">Remarks</span></span>  

 <span data-ttu-id="dc8c5-111">Используйте метод [метод iclrstrongname:: StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) для импорта пары открытого и закрытого ключей в контейнер.</span><span class="sxs-lookup"><span data-stu-id="dc8c5-111">Use the [ICLRStrongName::StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc8c5-112">Требования</span><span class="sxs-lookup"><span data-stu-id="dc8c5-112">Requirements</span></span>  

 <span data-ttu-id="dc8c5-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc8c5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc8c5-114">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="dc8c5-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dc8c5-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc8c5-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc8c5-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc8c5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc8c5-117">См. также</span><span class="sxs-lookup"><span data-stu-id="dc8c5-117">See also</span></span>

- [<span data-ttu-id="dc8c5-118">Метод StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="dc8c5-118">StrongNameKeyInstall Method</span></span>](iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="dc8c5-119">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="dc8c5-119">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
