---
description: 'Дополнительные сведения о методе: ICorDebugEval2:: Невпараметеризедобжект'
title: Метод ICorDebugEval2::NewParameterizedObject
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
ms.openlocfilehash: 2dc746fdada0e79044a1387bd4cb1c11b81d7777
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693685"
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="c0f56-103">Метод ICorDebugEval2::NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="c0f56-103">ICorDebugEval2::NewParameterizedObject Method</span></span>

<span data-ttu-id="c0f56-104">Создает новый объект параметризованного типа и вызывает метод конструктора объекта.</span><span class="sxs-lookup"><span data-stu-id="c0f56-104">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0f56-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c0f56-105">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0f56-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c0f56-106">Parameters</span></span>  

 `pConstructor`  
 <span data-ttu-id="c0f56-107">окне Указатель на объект ICorDebugFunction, представляющий конструктор объекта, для которого создается экземпляр.</span><span class="sxs-lookup"><span data-stu-id="c0f56-107">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="c0f56-108">окне Число переданных аргументов типа.</span><span class="sxs-lookup"><span data-stu-id="c0f56-108">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="c0f56-109">окне Массив указателей, каждый из которых указывает на объект ICorDebugType, представляющий аргумент типа для объекта, для которого создается экземпляр.</span><span class="sxs-lookup"><span data-stu-id="c0f56-109">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="c0f56-110">окне Число аргументов, переданных конструктору.</span><span class="sxs-lookup"><span data-stu-id="c0f56-110">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="c0f56-111">окне Массив указателей, каждый из которых указывает на объект ICorDebugValue, представляющий значение аргумента, передаваемое конструктору.</span><span class="sxs-lookup"><span data-stu-id="c0f56-111">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0f56-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="c0f56-112">Remarks</span></span>  

 <span data-ttu-id="c0f56-113">Конструктор объекта может принимать <xref:System.Type> Параметры.</span><span class="sxs-lookup"><span data-stu-id="c0f56-113">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0f56-114">Требования</span><span class="sxs-lookup"><span data-stu-id="c0f56-114">Requirements</span></span>  

 <span data-ttu-id="c0f56-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0f56-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0f56-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0f56-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0f56-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0f56-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0f56-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0f56-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
