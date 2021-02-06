---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: Жетклассфромтокен'
title: Метод ICorProfilerInfo::GetClassFromToken
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
ms.openlocfilehash: 0460a9b767f29f108a2b290b848f4cc6b6394ecb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647756"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="90f1a-103">Метод ICorProfilerInfo::GetClassFromToken</span><span class="sxs-lookup"><span data-stu-id="90f1a-103">ICorProfilerInfo::GetClassFromToken Method</span></span>

<span data-ttu-id="90f1a-104">Возвращает идентификатор класса по заданному маркеру метаданных.</span><span class="sxs-lookup"><span data-stu-id="90f1a-104">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="90f1a-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="90f1a-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="90f1a-106">Вместо этого используйте [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) .</span><span class="sxs-lookup"><span data-stu-id="90f1a-106">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90f1a-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="90f1a-107">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90f1a-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="90f1a-108">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="90f1a-109">окне Идентификатор модуля, содержащего класс.</span><span class="sxs-lookup"><span data-stu-id="90f1a-109">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="90f1a-110">окне `mdTypeDef` Токен метаданных, ссылающийся на класс.</span><span class="sxs-lookup"><span data-stu-id="90f1a-110">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="90f1a-111">заполняет Указатель на идентификатор класса.</span><span class="sxs-lookup"><span data-stu-id="90f1a-111">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90f1a-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="90f1a-112">Remarks</span></span>  

 <span data-ttu-id="90f1a-113">Этот метод устарел; Вместо этого используйте `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` для всех типов.</span><span class="sxs-lookup"><span data-stu-id="90f1a-113">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90f1a-114">Требования</span><span class="sxs-lookup"><span data-stu-id="90f1a-114">Requirements</span></span>  

 <span data-ttu-id="90f1a-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90f1a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90f1a-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="90f1a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90f1a-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90f1a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90f1a-118">**Платформа .NET Framework версии:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="90f1a-118">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f1a-119">См. также</span><span class="sxs-lookup"><span data-stu-id="90f1a-119">See also</span></span>

- [<span data-ttu-id="90f1a-120">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="90f1a-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
