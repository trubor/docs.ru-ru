---
description: 'Дополнительные сведения о методе: ICorDebugType2:: TypeID'
title: 'Метод ICorDebugType2:: TypeID'
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
ms.openlocfilehash: 8143ede1a11ee5f73c49fc723920f53430339ed0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738108"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="b2e63-103">Метод ICorDebugType2:: TypeID</span><span class="sxs-lookup"><span data-stu-id="b2e63-103">ICorDebugType2::GetTypeID Method</span></span>

<span data-ttu-id="b2e63-104">Возвращает [COR_TYPEID](cor-typeid-structure.md) для этого типа.</span><span class="sxs-lookup"><span data-stu-id="b2e63-104">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2e63-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b2e63-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2e63-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b2e63-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="b2e63-107">заполняет Указатель на [COR_TYPEID](cor-typeid-structure.md) для этого элемента ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="b2e63-107">[out] A pointer to the [COR_TYPEID](cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2e63-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b2e63-108">Return Value</span></span>  

 <span data-ttu-id="b2e63-109">Возвращается значение `S_OK` при успешном выполнении или код ошибки `HRESULT` при сбое.</span><span class="sxs-lookup"><span data-stu-id="b2e63-109">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="b2e63-110">В `HRESULT` число этих кодов входят следующие.</span><span class="sxs-lookup"><span data-stu-id="b2e63-110">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="b2e63-111">Код возврата</span><span class="sxs-lookup"><span data-stu-id="b2e63-111">Return code</span></span>|<span data-ttu-id="b2e63-112">Описание</span><span class="sxs-lookup"><span data-stu-id="b2e63-112">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="b2e63-113">Метод успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="b2e63-113">Method succeeded.</span></span> <span data-ttu-id="b2e63-114">Метод получил допустимый [COR_TYPEID](cor-typeid-structure.md).</span><span class="sxs-lookup"><span data-stu-id="b2e63-114">The method has retrieved a valid [COR_TYPEID](cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="b2e63-115">Тип не был загружен.</span><span class="sxs-lookup"><span data-stu-id="b2e63-115">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="b2e63-116">Этот тип не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="b2e63-116">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2e63-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="b2e63-117">Remarks</span></span>  

 <span data-ttu-id="b2e63-118">Этот метод предоставляет сопоставление из объекта ICorDebugType, представляющего тип, который может быть или не загружен в среду выполнения, в [COR_TYPEID](cor-typeid-structure.md), который служит в качестве непрозрачного маркера, определяющего тип, загруженный в среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="b2e63-118">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="b2e63-119">Если тип, который представляет объект ICorDebugType, еще не загружен, этот метод возвращает `CORDBG_E_CLASS_NOT_LOADED` .</span><span class="sxs-lookup"><span data-stu-id="b2e63-119">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="b2e63-120">Если тип не поддерживается, он возвращает `CORDBG_E_UNSUPPORTED` .</span><span class="sxs-lookup"><span data-stu-id="b2e63-120">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2e63-121">Требования</span><span class="sxs-lookup"><span data-stu-id="b2e63-121">Requirements</span></span>  

 <span data-ttu-id="b2e63-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2e63-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2e63-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2e63-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2e63-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2e63-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2e63-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2e63-125">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e63-126">См. также</span><span class="sxs-lookup"><span data-stu-id="b2e63-126">See also</span></span>

- [<span data-ttu-id="b2e63-127">Интерфейс ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="b2e63-127">ICorDebugType2 Interface</span></span>](icordebugtype2-interface.md)
