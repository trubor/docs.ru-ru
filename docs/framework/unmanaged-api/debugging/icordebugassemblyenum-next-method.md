---
description: 'Дополнительные сведения о методе: ICorDebugAssemblyEnum:: Next'
title: Метод ICorDebugAssemblyEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
ms.openlocfilehash: feb77f22ec59fcc0e1b3f5590b7aee4efba13d01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772228"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="57667-103">Метод ICorDebugAssemblyEnum::Next</span><span class="sxs-lookup"><span data-stu-id="57667-103">ICorDebugAssemblyEnum::Next Method</span></span>

<span data-ttu-id="57667-104">Возвращает указанное количество сборок из коллекции, начиная с текущего положения курсора.</span><span class="sxs-lookup"><span data-stu-id="57667-104">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57667-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="57667-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57667-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="57667-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="57667-107">окне Число извлекаемых сборок.</span><span class="sxs-lookup"><span data-stu-id="57667-107">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="57667-108">заполняет Массив указателей, каждый из которых указывает на объект ICorDebugAssembly, представляющий сборку.</span><span class="sxs-lookup"><span data-stu-id="57667-108">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="57667-109">заполняет Указатель на число фактически возвращенных сборок.</span><span class="sxs-lookup"><span data-stu-id="57667-109">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="57667-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="57667-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57667-111">Требования</span><span class="sxs-lookup"><span data-stu-id="57667-111">Requirements</span></span>  

 <span data-ttu-id="57667-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57667-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57667-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57667-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57667-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57667-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57667-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57667-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
