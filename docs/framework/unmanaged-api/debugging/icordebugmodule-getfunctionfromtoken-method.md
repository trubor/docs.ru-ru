---
description: 'Дополнительные сведения о методе: ICorDebugModule:: Жетфунктионфромтокен'
title: Метод ICorDebugModule::GetFunctionFromToken
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
ms.openlocfilehash: d6da43441f3774cff44a6f867c3ccf2a8581ebab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691657"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="44bb4-103">Метод ICorDebugModule::GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="44bb4-103">ICorDebugModule::GetFunctionFromToken Method</span></span>

<span data-ttu-id="44bb4-104">Возвращает функцию, заданную маркером метаданных.</span><span class="sxs-lookup"><span data-stu-id="44bb4-104">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44bb4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="44bb4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44bb4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="44bb4-106">Parameters</span></span>  

 `methodDef`  
 <span data-ttu-id="44bb4-107">окне `mdMethodDef` Токен метаданных, который ссылается на метаданные функции.</span><span class="sxs-lookup"><span data-stu-id="44bb4-107">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="44bb4-108">заполняет Указатель на адрес объекта интерфейса ICorDebugFunction, представляющего функцию.</span><span class="sxs-lookup"><span data-stu-id="44bb4-108">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44bb4-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="44bb4-109">Remarks</span></span>  

 <span data-ttu-id="44bb4-110">`GetFunctionFromToken`Метод возвращает CORDBG_E_FUNCTION_NOT_IL HRESULT, если переданное значение `methodDef` не ссылается на метод языка MSIL.</span><span class="sxs-lookup"><span data-stu-id="44bb4-110">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44bb4-111">Требования</span><span class="sxs-lookup"><span data-stu-id="44bb4-111">Requirements</span></span>  

 <span data-ttu-id="44bb4-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44bb4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44bb4-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44bb4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44bb4-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44bb4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44bb4-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44bb4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
