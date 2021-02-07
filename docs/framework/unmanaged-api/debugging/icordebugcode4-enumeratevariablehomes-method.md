---
description: 'Дополнительные сведения о методе: ICorDebugCode4:: Енумератевариаблехомес'
title: 'Метод ICorDebugCode4:: Енумератевариаблехомес'
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: 58f5f9063cd22356efd3a77ece9fb43b6b4c1062
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710963"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="85dea-103">Метод ICorDebugCode4:: Енумератевариаблехомес</span><span class="sxs-lookup"><span data-stu-id="85dea-103">ICorDebugCode4::EnumerateVariableHomes Method</span></span>

<span data-ttu-id="85dea-104">Возвращает перечислитель для локальных переменных и аргументов в функции.</span><span class="sxs-lookup"><span data-stu-id="85dea-104">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85dea-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="85dea-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85dea-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="85dea-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="85dea-107">Указатель на адрес объекта интерфейса [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) , который является перечислителем для локальных переменных и аргументов в функции.</span><span class="sxs-lookup"><span data-stu-id="85dea-107">A pointer to the address of an [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85dea-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="85dea-108">Remarks</span></span>  

 <span data-ttu-id="85dea-109">Объект интерфейса [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) является стандартным перечислителем, производным от интерфейса "ICorDebugEnum", который позволяет перечислить объекты [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="85dea-109">The [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="85dea-110">Коллекция может содержать несколько объектов [ICorDebugVariableHome](icordebugvariablehome-interface.md) для одного и того же индекса слота или аргумента, если они имеют разные расположения в разных точках функции.</span><span class="sxs-lookup"><span data-stu-id="85dea-110">The collection may include multiple [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85dea-111">Требования</span><span class="sxs-lookup"><span data-stu-id="85dea-111">Requirements</span></span>  

 <span data-ttu-id="85dea-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85dea-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85dea-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85dea-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85dea-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85dea-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85dea-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85dea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85dea-116">См. также</span><span class="sxs-lookup"><span data-stu-id="85dea-116">See also</span></span>

- [<span data-ttu-id="85dea-117">Интерфейс ICorDebugCode4</span><span class="sxs-lookup"><span data-stu-id="85dea-117">ICorDebugCode4 Interface</span></span>](icordebugcode4-interface.md)
- [<span data-ttu-id="85dea-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="85dea-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
