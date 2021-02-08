---
description: 'Дополнительные сведения о методе: ITypeName::/AssemblyName'
title: Метод ITypeName::GetAssemblyName
ms.date: 03/30/2017
api_name:
- ITypeName.GetAssemblyName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type:
- apiref
ms.openlocfilehash: c2e84ec2fc7c6a300611643783d61b46c14997ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789350"
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="b0a9b-103">Метод ITypeName::GetAssemblyName</span><span class="sxs-lookup"><span data-stu-id="b0a9b-103">ITypeName::GetAssemblyName Method</span></span>

<span data-ttu-id="b0a9b-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="b0a9b-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0a9b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b0a9b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b0a9b-106">Требования</span><span class="sxs-lookup"><span data-stu-id="b0a9b-106">Requirements</span></span>  

 <span data-ttu-id="b0a9b-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0a9b-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0a9b-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b0a9b-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0a9b-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0a9b-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0a9b-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0a9b-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0a9b-111">См. также</span><span class="sxs-lookup"><span data-stu-id="b0a9b-111">See also</span></span>

- [<span data-ttu-id="b0a9b-112">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="b0a9b-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
