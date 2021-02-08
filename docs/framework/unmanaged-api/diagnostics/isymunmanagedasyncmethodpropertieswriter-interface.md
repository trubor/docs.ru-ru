---
description: 'Дополнительные сведения о: интерфейс метод isymunmanagedasyncmethodpropertieswriter'
title: Интерфейс ISymUnmanagedAsyncMethodPropertiesWriter
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: 4c8b1bc037485e22160af28b59d751859a157499
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790195"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="9ec41-103">Интерфейс ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="9ec41-103">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>

<span data-ttu-id="9ec41-104">Позволяет определить дополнительные сведения о асинхронном методе для каждого символа метода.</span><span class="sxs-lookup"><span data-stu-id="9ec41-104">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="9ec41-105">Всегда используйте с открытым методом. то есть между вызовами [метода опенмесод](isymunmanagedwriter-openmethod-method.md) и [метода клосемесод](isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="9ec41-105">Always use with an opened method; that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec41-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9ec41-106">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="9ec41-107">Методы</span><span class="sxs-lookup"><span data-stu-id="9ec41-107">Methods</span></span>  

 <span data-ttu-id="9ec41-108">Этот интерфейс содержит следующие методы:</span><span class="sxs-lookup"><span data-stu-id="9ec41-108">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="9ec41-109">Метод</span><span class="sxs-lookup"><span data-stu-id="9ec41-109">Method</span></span>|<span data-ttu-id="9ec41-110">Описание</span><span class="sxs-lookup"><span data-stu-id="9ec41-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ec41-111">Метод DefineAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="9ec41-111">DefineAsyncStepInfo Method</span></span>](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="9ec41-112">Определите группу асинхронных операций await в текущем методе.</span><span class="sxs-lookup"><span data-stu-id="9ec41-112">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="9ec41-113">Каждое значение yield Offset соответствует инструкции Return, определяющей потенциальный доход.</span><span class="sxs-lookup"><span data-stu-id="9ec41-113">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="9ec41-114">Каждая `breakpointMethod` / `breakpointOffset` пара определяет, где будет возобновлена асинхронная операция. это может быть другой метод.</span><span class="sxs-lookup"><span data-stu-id="9ec41-114">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="9ec41-115">Метод DefineCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="9ec41-115">DefineCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="9ec41-116">Задает смещение IL для обработчика catch, созданного компилятором, который создает оболочку для асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="9ec41-116">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="9ec41-117">Смещение IL созданного блока catch используется отладчиком для управления перехватом, как если бы он был непользовательским кодом, несмотря на то, что он может произойти в методе пользовательского кода.</span><span class="sxs-lookup"><span data-stu-id="9ec41-117">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="9ec41-118">В частности, он используется в ответ на событие исключения **катчхандлерфаунд** .</span><span class="sxs-lookup"><span data-stu-id="9ec41-118">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="9ec41-119">Метод DefineKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="9ec41-119">DefineKickoffMethod Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="9ec41-120">Задает начальный метод, инициирующий асинхронную операцию.</span><span class="sxs-lookup"><span data-stu-id="9ec41-120">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ec41-121">Требования</span><span class="sxs-lookup"><span data-stu-id="9ec41-121">Requirements</span></span>  

 <span data-ttu-id="9ec41-122">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="9ec41-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec41-123">См. также</span><span class="sxs-lookup"><span data-stu-id="9ec41-123">See also</span></span>

- [<span data-ttu-id="9ec41-124">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="9ec41-124">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
