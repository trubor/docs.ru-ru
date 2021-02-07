---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedMethod'
title: Интерфейс ISymUnmanagedMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
ms.openlocfilehash: 18f87784a959ddc62415592e51d1971ea10f90bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709962"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="d9520-103">Интерфейс ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="d9520-103">ISymUnmanagedMethod Interface</span></span>

<span data-ttu-id="d9520-104">Представляет метод в хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="d9520-104">Represents a method within the symbol store.</span></span> <span data-ttu-id="d9520-105">Этот интерфейс предоставляет доступ только к атрибутам метода, относящимся к символам, а не к атрибутам, связанным с типом.</span><span class="sxs-lookup"><span data-stu-id="d9520-105">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d9520-106">Методы</span><span class="sxs-lookup"><span data-stu-id="d9520-106">Methods</span></span>  
  
|<span data-ttu-id="d9520-107">Метод</span><span class="sxs-lookup"><span data-stu-id="d9520-107">Method</span></span>|<span data-ttu-id="d9520-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d9520-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d9520-109">Метод GetNamespace</span><span class="sxs-lookup"><span data-stu-id="d9520-109">GetNamespace Method</span></span>](isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="d9520-110">Возвращает пространство имен, в котором определен этот метод.</span><span class="sxs-lookup"><span data-stu-id="d9520-110">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="d9520-111">Метод GetOffset</span><span class="sxs-lookup"><span data-stu-id="d9520-111">GetOffset Method</span></span>](isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="d9520-112">Возвращает смещение в этом методе, соответствующее заданной позиции в документе.</span><span class="sxs-lookup"><span data-stu-id="d9520-112">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="d9520-113">Метод GetParameters</span><span class="sxs-lookup"><span data-stu-id="d9520-113">GetParameters Method</span></span>](isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="d9520-114">Возвращает параметры для этого метода.</span><span class="sxs-lookup"><span data-stu-id="d9520-114">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="d9520-115">Метод GetRanges</span><span class="sxs-lookup"><span data-stu-id="d9520-115">GetRanges Method</span></span>](isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="d9520-116">При наличии позиции в документе возвращает массив пар начального и конечного смещения, соответствующих диапазонам промежуточного языка MSIL, которые находятся в этом методе.</span><span class="sxs-lookup"><span data-stu-id="d9520-116">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="d9520-117">Метод GetRootScope</span><span class="sxs-lookup"><span data-stu-id="d9520-117">GetRootScope Method</span></span>](isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="d9520-118">Возвращает корневую лексическую область внутри этого метода.</span><span class="sxs-lookup"><span data-stu-id="d9520-118">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="d9520-119">Эта область включает весь метод.</span><span class="sxs-lookup"><span data-stu-id="d9520-119">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="d9520-120">Метод GetScopeFromOffset</span><span class="sxs-lookup"><span data-stu-id="d9520-120">GetScopeFromOffset Method</span></span>](isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="d9520-121">Возвращает наиболее окружающую лексическую область внутри этого метода, которая заключает заданное смещение.</span><span class="sxs-lookup"><span data-stu-id="d9520-121">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="d9520-122">Метод GetSequencePointCount</span><span class="sxs-lookup"><span data-stu-id="d9520-122">GetSequencePointCount Method</span></span>](isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="d9520-123">Возвращает число точек следования в этом методе.</span><span class="sxs-lookup"><span data-stu-id="d9520-123">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="d9520-124">Метод GetSequencePoints</span><span class="sxs-lookup"><span data-stu-id="d9520-124">GetSequencePoints Method</span></span>](isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="d9520-125">Возвращает все точки следования в этом методе.</span><span class="sxs-lookup"><span data-stu-id="d9520-125">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="d9520-126">Метод GetSourceStartEnd</span><span class="sxs-lookup"><span data-stu-id="d9520-126">GetSourceStartEnd Method</span></span>](isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="d9520-127">Возвращает начальную и конечную позиции документа для источника данного метода.</span><span class="sxs-lookup"><span data-stu-id="d9520-127">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="d9520-128">Метод GetToken</span><span class="sxs-lookup"><span data-stu-id="d9520-128">GetToken Method</span></span>](isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="d9520-129">Возвращает маркер метаданных для данного метода.</span><span class="sxs-lookup"><span data-stu-id="d9520-129">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9520-130">Требования</span><span class="sxs-lookup"><span data-stu-id="d9520-130">Requirements</span></span>  

 <span data-ttu-id="d9520-131">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="d9520-131">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9520-132">См. также</span><span class="sxs-lookup"><span data-stu-id="d9520-132">See also</span></span>

- [<span data-ttu-id="d9520-133">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="d9520-133">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
