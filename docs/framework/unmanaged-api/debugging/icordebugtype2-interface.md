---
description: 'Дополнительные сведения о: интерфейс ICorDebugType2'
title: Интерфейс ICorDebugType2
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
ms.openlocfilehash: 8691cf294e835bef0f5a0ac694110f73577fb5d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800873"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="a8fc4-103">Интерфейс ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="a8fc4-103">ICorDebugType2 Interface</span></span>

<span data-ttu-id="a8fc4-104">Расширяет интерфейс ICorDebugType для получения идентификатора типа базового типа или сложного (определяемого пользователем) типа.</span><span class="sxs-lookup"><span data-stu-id="a8fc4-104">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8fc4-105">Методы</span><span class="sxs-lookup"><span data-stu-id="a8fc4-105">Methods</span></span>  
  
|<span data-ttu-id="a8fc4-106">Метод</span><span class="sxs-lookup"><span data-stu-id="a8fc4-106">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="a8fc4-107">Метод GetTypeID</span><span class="sxs-lookup"><span data-stu-id="a8fc4-107">GetTypeID Method</span></span>](icordebugtype2-gettypeid-method.md)|<span data-ttu-id="a8fc4-108">Возвращает [COR_TYPEID](cor-typeid-structure.md) для этого типа.</span><span class="sxs-lookup"><span data-stu-id="a8fc4-108">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8fc4-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="a8fc4-109">Remarks</span></span>  

 <span data-ttu-id="a8fc4-110">Этот интерфейс является логическим расширением интерфейса ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="a8fc4-110">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8fc4-111">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="a8fc4-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8fc4-112">Пример</span><span class="sxs-lookup"><span data-stu-id="a8fc4-112">Example</span></span>  

 <span data-ttu-id="a8fc4-113">В следующем фрагменте кода показано использование метода [ICorDebugType2:: typeid](icordebugtype2-gettypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a8fc4-113">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="a8fc4-114">Требования</span><span class="sxs-lookup"><span data-stu-id="a8fc4-114">Requirements</span></span>  

 <span data-ttu-id="a8fc4-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8fc4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8fc4-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8fc4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8fc4-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8fc4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8fc4-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8fc4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8fc4-119">См. также</span><span class="sxs-lookup"><span data-stu-id="a8fc4-119">See also</span></span>

- [<span data-ttu-id="a8fc4-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="a8fc4-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
