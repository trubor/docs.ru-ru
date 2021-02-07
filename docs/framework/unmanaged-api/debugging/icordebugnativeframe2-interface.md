---
description: 'Дополнительные сведения о: интерфейс ICorDebugNativeFrame2'
title: Интерфейс ICorDebugNativeFrame2
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
ms.openlocfilehash: 9ed0e20bb29bef3b210258956ebecb1ee7a96df8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722351"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="139fa-103">Интерфейс ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="139fa-103">ICorDebugNativeFrame2 Interface</span></span>

<span data-ttu-id="139fa-104">Предоставляет методы, проверяющие для кадров наличие взаимоотношений типа "дочерний-родительский".</span><span class="sxs-lookup"><span data-stu-id="139fa-104">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="139fa-105">Методы</span><span class="sxs-lookup"><span data-stu-id="139fa-105">Methods</span></span>  
  
|<span data-ttu-id="139fa-106">Метод</span><span class="sxs-lookup"><span data-stu-id="139fa-106">Method</span></span>|<span data-ttu-id="139fa-107">Описание</span><span class="sxs-lookup"><span data-stu-id="139fa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="139fa-108">Метод IsChild</span><span class="sxs-lookup"><span data-stu-id="139fa-108">IsChild Method</span></span>](icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="139fa-109">Определяет, является ли текущий кадр дочерним кадром.</span><span class="sxs-lookup"><span data-stu-id="139fa-109">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="139fa-110">Метод IsMatchingParentFrame</span><span class="sxs-lookup"><span data-stu-id="139fa-110">IsMatchingParentFrame Method</span></span>](icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="139fa-111">Определяет, является ли указанный кадр родительским по отношению к текущему кадру.</span><span class="sxs-lookup"><span data-stu-id="139fa-111">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="139fa-112">Метод GetStackParameterSize</span><span class="sxs-lookup"><span data-stu-id="139fa-112">GetStackParameterSize Method</span></span>](icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="139fa-113">Возвращает совокупный размер параметров в стеке в операционных системах x86.</span><span class="sxs-lookup"><span data-stu-id="139fa-113">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="139fa-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="139fa-114">Remarks</span></span>  

 <span data-ttu-id="139fa-115">Этот интерфейс логически расширяет интерфейс "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="139fa-115">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="139fa-116">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="139fa-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="139fa-117">Требования</span><span class="sxs-lookup"><span data-stu-id="139fa-117">Requirements</span></span>  

 <span data-ttu-id="139fa-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="139fa-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="139fa-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="139fa-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="139fa-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="139fa-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="139fa-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="139fa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="139fa-122">См. также</span><span class="sxs-lookup"><span data-stu-id="139fa-122">See also</span></span>

- [<span data-ttu-id="139fa-123">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="139fa-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="139fa-124">Отладка</span><span class="sxs-lookup"><span data-stu-id="139fa-124">Debugging</span></span>](index.md)
