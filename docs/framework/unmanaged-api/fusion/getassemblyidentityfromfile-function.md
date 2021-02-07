---
description: Дополнительные сведения о функции Жетассемблидентитифромфиле
title: Функция GetAssemblyIdentityFromFile
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
ms.openlocfilehash: 8832e03182a5652c938404c99115fa8059439d1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761043"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="6356a-103">Функция GetAssemblyIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="6356a-103">GetAssemblyIdentityFromFile Function</span></span>

<span data-ttu-id="6356a-104">Возвращает указатель на `IUnknown` объект с указанным `IID` в сборке по указанному пути к файлу.</span><span class="sxs-lookup"><span data-stu-id="6356a-104">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6356a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6356a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="6356a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6356a-106">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="6356a-107">окне Допустимый путь к запрошенной сборке.</span><span class="sxs-lookup"><span data-stu-id="6356a-107">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="6356a-108">окне `IID` Возвращаемый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="6356a-108">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="6356a-109">заполняет Возвращаемый указатель интерфейса.</span><span class="sxs-lookup"><span data-stu-id="6356a-109">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6356a-110">Требования</span><span class="sxs-lookup"><span data-stu-id="6356a-110">Requirements</span></span>  

 <span data-ttu-id="6356a-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6356a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6356a-112">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="6356a-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6356a-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6356a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6356a-114">См. также</span><span class="sxs-lookup"><span data-stu-id="6356a-114">See also</span></span>

- [<span data-ttu-id="6356a-115">IUnknown</span><span class="sxs-lookup"><span data-stu-id="6356a-115">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="6356a-116">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="6356a-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
