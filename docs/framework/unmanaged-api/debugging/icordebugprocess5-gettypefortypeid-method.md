---
description: 'Дополнительные сведения о методе: метод ICorDebugProcess5:: Жеттипефортипеид'
title: Метод ICorDebugProcess5::GetTypeForTypeID
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: a18543b0afc867dc3796264ac1d08a775c73ca59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746377"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="3155b-103">Метод ICorDebugProcess5::GetTypeForTypeID</span><span class="sxs-lookup"><span data-stu-id="3155b-103">ICorDebugProcess5::GetTypeForTypeID Method</span></span>

<span data-ttu-id="3155b-104">Преобразует идентификатор типа в значение ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="3155b-104">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3155b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3155b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3155b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3155b-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="3155b-107">окне Идентификатор типа.</span><span class="sxs-lookup"><span data-stu-id="3155b-107">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="3155b-108">заполняет Указатель на адрес объекта ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="3155b-108">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3155b-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="3155b-109">Remarks</span></span>  

 <span data-ttu-id="3155b-110">В некоторых случаях методы, возвращающие идентификатор типа, могут возвращать `COR_TYPEID` значение null.</span><span class="sxs-lookup"><span data-stu-id="3155b-110">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="3155b-111">Если это значение передается в качестве `id` аргумента, `GetTypeForTypeID` метод завершится ошибкой и вернет значение `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="3155b-111">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3155b-112">Требования</span><span class="sxs-lookup"><span data-stu-id="3155b-112">Requirements</span></span>  

 <span data-ttu-id="3155b-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3155b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3155b-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3155b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3155b-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3155b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3155b-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3155b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3155b-117">См. также</span><span class="sxs-lookup"><span data-stu-id="3155b-117">See also</span></span>

- [<span data-ttu-id="3155b-118">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="3155b-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="3155b-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="3155b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
