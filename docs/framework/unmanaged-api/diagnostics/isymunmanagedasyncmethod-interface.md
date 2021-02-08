---
description: 'Дополнительные сведения о: интерфейс Исимунманажедасинкмесод'
title: Интерфейс ISymUnmanagedAsyncMethod
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: cb3120464224137dfdcff4f13ca4aee82ef4d89e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790273"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="f2de5-103">Интерфейс ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="f2de5-103">ISymUnmanagedAsyncMethod Interface</span></span>

<span data-ttu-id="f2de5-104">Этот интерфейс является дополнением к [интерфейсу метод isymunmanagedasyncmethodpropertieswriter](isymunmanagedasyncmethodpropertieswriter-interface.md)для чтения.</span><span class="sxs-lookup"><span data-stu-id="f2de5-104">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2de5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f2de5-105">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="f2de5-106">Методы</span><span class="sxs-lookup"><span data-stu-id="f2de5-106">Methods</span></span>  

 <span data-ttu-id="f2de5-107">Этот интерфейс содержит следующие методы:</span><span class="sxs-lookup"><span data-stu-id="f2de5-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="f2de5-108">Метод</span><span class="sxs-lookup"><span data-stu-id="f2de5-108">Method</span></span>|<span data-ttu-id="f2de5-109">Описание</span><span class="sxs-lookup"><span data-stu-id="f2de5-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2de5-110">Метод GetAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="f2de5-110">GetAsyncStepInfo Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="f2de5-111">См. раздел [метод дефинеасинкстепинфо](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="f2de5-111">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="f2de5-112">Метод GetAsyncStepInfoCount</span><span class="sxs-lookup"><span data-stu-id="f2de5-112">GetAsyncStepInfoCount Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="f2de5-113">См. раздел [метод дефинеасинкстепинфо](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="f2de5-113">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="f2de5-114">Метод GetCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="f2de5-114">GetCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="f2de5-115">См. раздел [метод DefineCatchHandlerILOffset](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="f2de5-115">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="f2de5-116">Метод GetKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="f2de5-116">GetKickoffMethod Method</span></span>](isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="f2de5-117">См. раздел [метод DefineKickoffMethod](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="f2de5-117">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="f2de5-118">Метод HasCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="f2de5-118">HasCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="f2de5-119">См. раздел [метод DefineCatchHandlerILOffset](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="f2de5-119">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="f2de5-120">Метод IsAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="f2de5-120">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="f2de5-121">Проверяет, имеет ли метод асинхронную информацию.</span><span class="sxs-lookup"><span data-stu-id="f2de5-121">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="f2de5-122">Если этот метод возвращает значение `FALSE` , то он недопустим для вызова любых других методов в этом интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="f2de5-122">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="f2de5-123">`E_UNEXPECTED`В этом случае они будут возвращаться.</span><span class="sxs-lookup"><span data-stu-id="f2de5-123">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2de5-124">Требования</span><span class="sxs-lookup"><span data-stu-id="f2de5-124">Requirements</span></span>  

 <span data-ttu-id="f2de5-125">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="f2de5-125">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2de5-126">См. также</span><span class="sxs-lookup"><span data-stu-id="f2de5-126">See also</span></span>

- [<span data-ttu-id="f2de5-127">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="f2de5-127">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
