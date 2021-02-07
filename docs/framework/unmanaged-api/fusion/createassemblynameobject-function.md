---
description: Дополнительные сведения о функции Креатеассемблинамеобжект
title: Функция CreateAssemblyNameObject
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
ms.openlocfilehash: 0eaa74bdb37a098ad58b81658229f8c04259b730
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761191"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="ed969-103">Функция CreateAssemblyNameObject</span><span class="sxs-lookup"><span data-stu-id="ed969-103">CreateAssemblyNameObject Function</span></span>

<span data-ttu-id="ed969-104">Возвращает указатель интерфейса на экземпляр [IAssemblyName](iassemblyname-interface.md) , представляющий уникальный идентификатор сборки с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="ed969-104">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed969-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ed969-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed969-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ed969-106">Parameters</span></span>  

 `ppAssemblyNameObj`  
 <span data-ttu-id="ed969-107">заполняет Возвращаемое значение `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="ed969-107">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="ed969-108">окне Имя сборки, для которой создается новый `IAssemblyName` экземпляр.</span><span class="sxs-lookup"><span data-stu-id="ed969-108">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ed969-109">окне Флаги, передаваемые в конструктор объектов.</span><span class="sxs-lookup"><span data-stu-id="ed969-109">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="ed969-110">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="ed969-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ed969-111">`pvReserved` должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="ed969-111">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed969-112">Требования</span><span class="sxs-lookup"><span data-stu-id="ed969-112">Requirements</span></span>  

 <span data-ttu-id="ed969-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed969-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed969-114">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ed969-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ed969-115">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed969-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed969-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed969-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed969-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ed969-117">See also</span></span>

- [<span data-ttu-id="ed969-118">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="ed969-118">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="ed969-119">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="ed969-119">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
