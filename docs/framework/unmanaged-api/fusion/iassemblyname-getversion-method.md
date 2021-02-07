---
description: 'Дополнительные сведения о методе IAssemblyName:: метода Version'
title: Метод IAssemblyName::GetVersion
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
ms.openlocfilehash: 3339dda6a0b4f083655ece7bef86b080a8fcf5c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760723"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="75271-103">Метод IAssemblyName::GetVersion</span><span class="sxs-lookup"><span data-stu-id="75271-103">IAssemblyName::GetVersion Method</span></span>

<span data-ttu-id="75271-104">Возвращает сведения о версии для сборки, на которую ссылается этот объект [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="75271-104">Gets the version information for the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75271-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="75271-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75271-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="75271-106">Parameters</span></span>  

 `pdwVersionHi`  
 <span data-ttu-id="75271-107">заполняет Старшие 32 бит версии.</span><span class="sxs-lookup"><span data-stu-id="75271-107">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="75271-108">заполняет Младшие 32 разрядов версии.</span><span class="sxs-lookup"><span data-stu-id="75271-108">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75271-109">Требования</span><span class="sxs-lookup"><span data-stu-id="75271-109">Requirements</span></span>  

 <span data-ttu-id="75271-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75271-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75271-111">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="75271-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="75271-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75271-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75271-113">См. также</span><span class="sxs-lookup"><span data-stu-id="75271-113">See also</span></span>

- [<span data-ttu-id="75271-114">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="75271-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
