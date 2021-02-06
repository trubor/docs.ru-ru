---
description: 'Дополнительные сведения о методе "ICorDebugType:: Polybase"'
title: Метод ICorDebugType::GetBase
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
ms.openlocfilehash: 78cd540974b540b704e946f6c723214d72e89ab4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658390"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="06553-103">Метод ICorDebugType::GetBase</span><span class="sxs-lookup"><span data-stu-id="06553-103">ICorDebugType::GetBase Method</span></span>

<span data-ttu-id="06553-104">Возвращает указатель интерфейса на объект ICorDebugType, представляющий базовый тип, если он существует, типа, представленного этим объектом `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="06553-104">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06553-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="06553-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06553-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="06553-106">Parameters</span></span>  

 `pBase`  
 <span data-ttu-id="06553-107">заполняет Указатель на адрес `ICorDebugType` объекта, который представляет базовый тип.</span><span class="sxs-lookup"><span data-stu-id="06553-107">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06553-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="06553-108">Remarks</span></span>  

 <span data-ttu-id="06553-109">Поиск базового типа для типа полезен для реализации общих функциональных возможностей отладчика, таких как вывод всех полей объекта или его родительских классов.</span><span class="sxs-lookup"><span data-stu-id="06553-109">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06553-110">Требования</span><span class="sxs-lookup"><span data-stu-id="06553-110">Requirements</span></span>  

 <span data-ttu-id="06553-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06553-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06553-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06553-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06553-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06553-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06553-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06553-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
