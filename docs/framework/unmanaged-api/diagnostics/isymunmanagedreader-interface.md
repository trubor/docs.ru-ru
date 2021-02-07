---
description: 'Дополнительные сведения о: Интерфейс ISymUnmanagedReader'
title: Интерфейс ISymUnmanagedReader
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
ms.openlocfilehash: bad4fdbac3bf6f03fa0db79ce54a5b0ca897028f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763804"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="a9cab-103">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="a9cab-103">ISymUnmanagedReader Interface</span></span>

<span data-ttu-id="a9cab-104">Представляет средство чтения символов, которое предоставляет доступ к документам, методам и переменным в хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="a9cab-104">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9cab-105">Методы</span><span class="sxs-lookup"><span data-stu-id="a9cab-105">Methods</span></span>  
  
|<span data-ttu-id="a9cab-106">Метод</span><span class="sxs-lookup"><span data-stu-id="a9cab-106">Method</span></span>|<span data-ttu-id="a9cab-107">Описание</span><span class="sxs-lookup"><span data-stu-id="a9cab-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9cab-108">Метод GetDocument</span><span class="sxs-lookup"><span data-stu-id="a9cab-108">GetDocument Method</span></span>](isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="a9cab-109">Находит документ.</span><span class="sxs-lookup"><span data-stu-id="a9cab-109">Finds a document.</span></span>|  
|[<span data-ttu-id="a9cab-110">Метод GetDocuments</span><span class="sxs-lookup"><span data-stu-id="a9cab-110">GetDocuments Method</span></span>](isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="a9cab-111">Возвращает массив всех документов, определенных в хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="a9cab-111">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="a9cab-112">Метод GetDocumentVersion</span><span class="sxs-lookup"><span data-stu-id="a9cab-112">GetDocumentVersion Method</span></span>](isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="a9cab-113">Возвращает указанную версию указанного документа.</span><span class="sxs-lookup"><span data-stu-id="a9cab-113">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="a9cab-114">Метод GetGlobalVariables</span><span class="sxs-lookup"><span data-stu-id="a9cab-114">GetGlobalVariables Method</span></span>](isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="a9cab-115">Возвращает все глобальные переменные.</span><span class="sxs-lookup"><span data-stu-id="a9cab-115">Returns all global variables.</span></span>|  
|[<span data-ttu-id="a9cab-116">Метод GetMethod</span><span class="sxs-lookup"><span data-stu-id="a9cab-116">GetMethod Method</span></span>](isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="a9cab-117">Возвращает метод чтения символов по заданному токену метода.</span><span class="sxs-lookup"><span data-stu-id="a9cab-117">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="a9cab-118">Метод GetMethodByVersion</span><span class="sxs-lookup"><span data-stu-id="a9cab-118">GetMethodByVersion Method</span></span>](isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="a9cab-119">Возвращает метод чтения символов по заданному маркеру метода и номеру версии для редактирования и копирования.</span><span class="sxs-lookup"><span data-stu-id="a9cab-119">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="a9cab-120">Метод GetMethodFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="a9cab-120">GetMethodFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="a9cab-121">Возвращает метод, содержащий точку останова в заданной позиции в документе.</span><span class="sxs-lookup"><span data-stu-id="a9cab-121">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="a9cab-122">Метод GetMethodsFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="a9cab-122">GetMethodsFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="a9cab-123">Возвращает массив методов, каждый из которых содержит точку останова в заданной позиции в документе.</span><span class="sxs-lookup"><span data-stu-id="a9cab-123">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="a9cab-124">Метод GetMethodVersion</span><span class="sxs-lookup"><span data-stu-id="a9cab-124">GetMethodVersion Method</span></span>](isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="a9cab-125">Возвращает версию метода.</span><span class="sxs-lookup"><span data-stu-id="a9cab-125">Gets the method version.</span></span>|  
|[<span data-ttu-id="a9cab-126">Метод GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="a9cab-126">GetNamespaces Method</span></span>](isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="a9cab-127">Возвращает пространства имен, определенные в глобальной области в этом хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="a9cab-127">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="a9cab-128">Метод GetSymAttribute</span><span class="sxs-lookup"><span data-stu-id="a9cab-128">GetSymAttribute Method</span></span>](isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="a9cab-129">Возвращает настраиваемый атрибут на основе его имени.</span><span class="sxs-lookup"><span data-stu-id="a9cab-129">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="a9cab-130">Метод GetSymbolStoreFileName</span><span class="sxs-lookup"><span data-stu-id="a9cab-130">GetSymbolStoreFileName Method</span></span>](isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="a9cab-131">Предоставляет имя файла на диске для хранилища символов.</span><span class="sxs-lookup"><span data-stu-id="a9cab-131">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="a9cab-132">Метод GetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="a9cab-132">GetUserEntryPoint Method</span></span>](isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="a9cab-133">Возвращает метод, указанный в качестве точки входа пользователя для модуля, если он есть.</span><span class="sxs-lookup"><span data-stu-id="a9cab-133">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="a9cab-134">Метод GetVariables</span><span class="sxs-lookup"><span data-stu-id="a9cab-134">GetVariables Method</span></span>](isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="a9cab-135">Возвращает нелокальную переменную с учетом ее родителя и имени.</span><span class="sxs-lookup"><span data-stu-id="a9cab-135">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="a9cab-136">Метод Initialize</span><span class="sxs-lookup"><span data-stu-id="a9cab-136">Initialize Method</span></span>](isymunmanagedreader-initialize-method.md)|<span data-ttu-id="a9cab-137">Инициализирует средство чтения символов с помощью интерфейса средства импорта метаданных, с которым будет связан этот модуль чтения, вместе с именем файла модуля.</span><span class="sxs-lookup"><span data-stu-id="a9cab-137">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="a9cab-138">Метод ReplaceSymbolStore</span><span class="sxs-lookup"><span data-stu-id="a9cab-138">ReplaceSymbolStore Method</span></span>](isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="a9cab-139">Заменяет имеющееся хранилище символов разностным хранилищем символов.</span><span class="sxs-lookup"><span data-stu-id="a9cab-139">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="a9cab-140">Метод UpdateSymbolStore</span><span class="sxs-lookup"><span data-stu-id="a9cab-140">UpdateSymbolStore Method</span></span>](isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="a9cab-141">Обновляет существующее хранилище символов разностным хранилищем символов.</span><span class="sxs-lookup"><span data-stu-id="a9cab-141">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9cab-142">Требования</span><span class="sxs-lookup"><span data-stu-id="a9cab-142">Requirements</span></span>  

 <span data-ttu-id="a9cab-143">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="a9cab-143">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9cab-144">См. также</span><span class="sxs-lookup"><span data-stu-id="a9cab-144">See also</span></span>

- [<span data-ttu-id="a9cab-145">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="a9cab-145">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="a9cab-146">Интерфейс ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="a9cab-146">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
