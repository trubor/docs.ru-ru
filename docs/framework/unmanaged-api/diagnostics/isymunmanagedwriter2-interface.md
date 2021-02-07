---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedWriter2'
title: Интерфейс ISymUnmanagedWriter2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
ms.openlocfilehash: 228bae40e12376b3b5e8ca3bbd3463ba70a6d67b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761782"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="5f715-103">Интерфейс ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="5f715-103">ISymUnmanagedWriter2 Interface</span></span>

<span data-ttu-id="5f715-104">Представляет средство записи символов и предоставляет методы для определения документов, точек следования, лексических областей и переменных.</span><span class="sxs-lookup"><span data-stu-id="5f715-104">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="5f715-105">Этот интерфейс расширяет интерфейс [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5f715-105">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f715-106">Методы</span><span class="sxs-lookup"><span data-stu-id="5f715-106">Methods</span></span>  
  
|<span data-ttu-id="5f715-107">Метод</span><span class="sxs-lookup"><span data-stu-id="5f715-107">Method</span></span>|<span data-ttu-id="5f715-108">Описание</span><span class="sxs-lookup"><span data-stu-id="5f715-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f715-109">Метод DefineConstant2</span><span class="sxs-lookup"><span data-stu-id="5f715-109">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="5f715-110">Определяет имя для постоянного значения.</span><span class="sxs-lookup"><span data-stu-id="5f715-110">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="5f715-111">Метод DefineGlobalVariable2</span><span class="sxs-lookup"><span data-stu-id="5f715-111">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="5f715-112">Определяет одну глобальную переменную.</span><span class="sxs-lookup"><span data-stu-id="5f715-112">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="5f715-113">Метод DefineLocalVariable2</span><span class="sxs-lookup"><span data-stu-id="5f715-113">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="5f715-114">Определяет одну переменную в текущей лексической области видимости.</span><span class="sxs-lookup"><span data-stu-id="5f715-114">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f715-115">Требования</span><span class="sxs-lookup"><span data-stu-id="5f715-115">Requirements</span></span>  

 <span data-ttu-id="5f715-116">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="5f715-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f715-117">См. также</span><span class="sxs-lookup"><span data-stu-id="5f715-117">See also</span></span>

- [<span data-ttu-id="5f715-118">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="5f715-118">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="5f715-119">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="5f715-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="5f715-120">Интерфейс ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="5f715-120">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
