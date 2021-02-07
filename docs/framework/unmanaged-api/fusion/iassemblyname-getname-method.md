---
description: 'Дополнительные сведения о методе IAssemblyName:: Name'
title: Метод IAssemblyName::GetName
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
ms.openlocfilehash: 04cd6258c2fc60c9fc40e1e4b731e5c04a8d3112
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760749"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="e8aba-103">Метод IAssemblyName::GetName</span><span class="sxs-lookup"><span data-stu-id="e8aba-103">IAssemblyName::GetName Method</span></span>

<span data-ttu-id="e8aba-104">Возвращает простое незашифрованное имя сборки, на которую ссылается этот объект [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e8aba-104">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8aba-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e8aba-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8aba-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e8aba-106">Parameters</span></span>  

 `lpcwBuffer`  
 <span data-ttu-id="e8aba-107">[вход, выход] Размер `pwzName` в расширенных символах, включая символ конца null.</span><span class="sxs-lookup"><span data-stu-id="e8aba-107">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="e8aba-108">заполняет Буфер для хранения имени сборки, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="e8aba-108">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8aba-109">Требования</span><span class="sxs-lookup"><span data-stu-id="e8aba-109">Requirements</span></span>  

 <span data-ttu-id="e8aba-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8aba-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8aba-111">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e8aba-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e8aba-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8aba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8aba-113">См. также</span><span class="sxs-lookup"><span data-stu-id="e8aba-113">See also</span></span>

- [<span data-ttu-id="e8aba-114">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="e8aba-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
