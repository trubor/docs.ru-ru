---
description: 'Дополнительные сведения о: интерфейс Исимунманажедскопе'
title: Интерфейс ISymUnmanagedScope
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
ms.openlocfilehash: f1175656fb49ee16fd1cd676d08f6ebb76f40c6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763271"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="1859a-103">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="1859a-103">ISymUnmanagedScope Interface</span></span>

<span data-ttu-id="1859a-104">Представляет лексическую область внутри метода.</span><span class="sxs-lookup"><span data-stu-id="1859a-104">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1859a-105">Методы</span><span class="sxs-lookup"><span data-stu-id="1859a-105">Methods</span></span>  
  
|<span data-ttu-id="1859a-106">Метод</span><span class="sxs-lookup"><span data-stu-id="1859a-106">Method</span></span>|<span data-ttu-id="1859a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="1859a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1859a-108">Метод GetChildren</span><span class="sxs-lookup"><span data-stu-id="1859a-108">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="1859a-109">Возвращает дочерние элементы этой области.</span><span class="sxs-lookup"><span data-stu-id="1859a-109">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="1859a-110">Метод GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="1859a-110">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="1859a-111">Возвращает конечное смещение для данной области.</span><span class="sxs-lookup"><span data-stu-id="1859a-111">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="1859a-112">Метод GetLocalCount</span><span class="sxs-lookup"><span data-stu-id="1859a-112">GetLocalCount Method</span></span>](isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="1859a-113">Возвращает число локальных переменных, определенных в этой области.</span><span class="sxs-lookup"><span data-stu-id="1859a-113">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="1859a-114">Метод GetLocals</span><span class="sxs-lookup"><span data-stu-id="1859a-114">GetLocals Method</span></span>](isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="1859a-115">Возвращает локальные переменные, определенные в этой области.</span><span class="sxs-lookup"><span data-stu-id="1859a-115">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="1859a-116">Метод GetMethod</span><span class="sxs-lookup"><span data-stu-id="1859a-116">GetMethod Method</span></span>](isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="1859a-117">Возвращает метод, содержащий эту область.</span><span class="sxs-lookup"><span data-stu-id="1859a-117">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="1859a-118">Метод GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="1859a-118">GetNamespaces Method</span></span>](isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="1859a-119">Возвращает пространства имен, используемые в этой области.</span><span class="sxs-lookup"><span data-stu-id="1859a-119">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="1859a-120">Метод GetParent</span><span class="sxs-lookup"><span data-stu-id="1859a-120">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)|<span data-ttu-id="1859a-121">Возвращает родительскую область этой области.</span><span class="sxs-lookup"><span data-stu-id="1859a-121">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="1859a-122">Метод GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="1859a-122">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="1859a-123">Возвращает начальное смещение для этой области.</span><span class="sxs-lookup"><span data-stu-id="1859a-123">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1859a-124">Требования</span><span class="sxs-lookup"><span data-stu-id="1859a-124">Requirements</span></span>  

 <span data-ttu-id="1859a-125">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="1859a-125">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1859a-126">См. также</span><span class="sxs-lookup"><span data-stu-id="1859a-126">See also</span></span>

- [<span data-ttu-id="1859a-127">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="1859a-127">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="1859a-128">Интерфейс ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="1859a-128">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
