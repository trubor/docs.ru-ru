---
description: 'Дополнительные сведения о методе: метод isymunmanagedasyncmethodpropertieswriter::D Ефинекатчхандлерилоффсет'
title: Метод ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: fcb2c6efa7ea83252a46a9b08cdfa7b2c14f09d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737796"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="87d91-103">Метод ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="87d91-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>

<span data-ttu-id="87d91-104">Задает смещение IL для обработчика catch, созданного компилятором, который создает оболочку для асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="87d91-104">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="87d91-105">Смещение IL созданного блока catch используется отладчиком для управления перехватом, как если бы он был непользовательским кодом, даже если он может возникнуть в методе пользовательского кода.</span><span class="sxs-lookup"><span data-stu-id="87d91-105">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="87d91-106">В частности, он используется в ответ на событие исключения **катчхандлерфаунд** .</span><span class="sxs-lookup"><span data-stu-id="87d91-106">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87d91-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="87d91-107">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87d91-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="87d91-108">Parameters</span></span>  
  
|<span data-ttu-id="87d91-109">Параметр</span><span class="sxs-lookup"><span data-stu-id="87d91-109">Parameter</span></span>|<span data-ttu-id="87d91-110">Описание</span><span class="sxs-lookup"><span data-stu-id="87d91-110">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="87d91-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="87d91-111">Return Value</span></span>  

 <span data-ttu-id="87d91-112">Возвращает `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="87d91-112">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87d91-113">Требования</span><span class="sxs-lookup"><span data-stu-id="87d91-113">Requirements</span></span>  

 <span data-ttu-id="87d91-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="87d91-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d91-115">См. также</span><span class="sxs-lookup"><span data-stu-id="87d91-115">See also</span></span>

- [<span data-ttu-id="87d91-116">Интерфейс ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="87d91-116">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
