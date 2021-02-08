---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain2:: Жетфунктионпоинтертипе'
title: Метод ICorDebugAppDomain2::GetFunctionPointerType
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
ms.openlocfilehash: 2b9e10295df40b8e7db82e489fe8a6d28214ff38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772397"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="054a4-103">Метод ICorDebugAppDomain2::GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="054a4-103">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>

<span data-ttu-id="054a4-104">Возвращает указатель на функцию с заданной сигнатурой.</span><span class="sxs-lookup"><span data-stu-id="054a4-104">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="054a4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="054a4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="054a4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="054a4-106">Parameters</span></span>  

 `nTypeArgs`  
 <span data-ttu-id="054a4-107">окне Число аргументов типа для функции.</span><span class="sxs-lookup"><span data-stu-id="054a4-107">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="054a4-108">окне Массив указателей, каждый из которых указывает на объект ICorDebugType, представляющий аргумент типа функции.</span><span class="sxs-lookup"><span data-stu-id="054a4-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="054a4-109">Первый элемент является типом возвращаемого значения; Каждый из остальных элементов является типом параметра.</span><span class="sxs-lookup"><span data-stu-id="054a4-109">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="054a4-110">заполняет Указатель на адрес `ICorDebugType` объекта, который представляет указатель на функцию.</span><span class="sxs-lookup"><span data-stu-id="054a4-110">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="054a4-111">Требования</span><span class="sxs-lookup"><span data-stu-id="054a4-111">Requirements</span></span>  

 <span data-ttu-id="054a4-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="054a4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="054a4-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="054a4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="054a4-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="054a4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="054a4-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="054a4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
