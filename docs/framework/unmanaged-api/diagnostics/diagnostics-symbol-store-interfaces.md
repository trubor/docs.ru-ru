---
description: Дополнительные сведения см. в статье Диагностика интерфейсов хранилища символов
title: Интерфейсы хранилища символов диагностики
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: 253a6e5eaa97c91332bca62f8fc47ad2945bf741
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800439"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="c15ae-103">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="c15ae-103">Diagnostics Symbol Store Interfaces</span></span>

<span data-ttu-id="c15ae-104">В этом разделе описываются неуправляемые интерфейсы, позволяющие компилятору создавать символьные сведения для использования отладчиком.</span><span class="sxs-lookup"><span data-stu-id="c15ae-104">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c15ae-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="c15ae-105">In This Section</span></span>  

 [<span data-ttu-id="c15ae-106">Интерфейс IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="c15ae-106">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)  
 <span data-ttu-id="c15ae-107">Предоставляет методы, отображающие текущие сведения о привязке для выполняющегося приложения.</span><span class="sxs-lookup"><span data-stu-id="c15ae-107">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="c15ae-108">Интерфейс IDebugAutoAttach</span><span class="sxs-lookup"><span data-stu-id="c15ae-108">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)  
 <span data-ttu-id="c15ae-109">Определяет интерфейс для автоматического присоединения отладчика, вызываемого сервером.</span><span class="sxs-lookup"><span data-stu-id="c15ae-109">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="c15ae-110">Интерфейс INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="c15ae-110">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)  
 <span data-ttu-id="c15ae-111">Объявляет методы для регистрации и отмены регистрации источника уведомления о соединении.</span><span class="sxs-lookup"><span data-stu-id="c15ae-111">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="c15ae-112">Интерфейс INotifySink2</span><span class="sxs-lookup"><span data-stu-id="c15ae-112">INotifySink2 Interface</span></span>](inotifysink2-interface.md)  
 <span data-ttu-id="c15ae-113">Объявляет методы для уведомления о приемнике.</span><span class="sxs-lookup"><span data-stu-id="c15ae-113">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="c15ae-114">Интерфейс INotifySource2</span><span class="sxs-lookup"><span data-stu-id="c15ae-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)  
 <span data-ttu-id="c15ae-115">Объявляет метод для установки фильтров уведомлений.</span><span class="sxs-lookup"><span data-stu-id="c15ae-115">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="c15ae-116">Интерфейс ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="c15ae-116">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="c15ae-117">Предоставляет сведения для функции "изменить и продолжить".</span><span class="sxs-lookup"><span data-stu-id="c15ae-117">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="c15ae-118">Интерфейс ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="c15ae-118">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="c15ae-119">Этот интерфейс является дополнением к [интерфейсу метод isymunmanagedasyncmethodpropertieswriter](isymunmanagedasyncmethodpropertieswriter-interface.md)для чтения.</span><span class="sxs-lookup"><span data-stu-id="c15ae-119">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="c15ae-120">Интерфейс ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="c15ae-120">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="c15ae-121">Разрешает определение дополнительных сведений о асинхронном методе для каждого символа метода.</span><span class="sxs-lookup"><span data-stu-id="c15ae-121">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="c15ae-122">Должен использовать с открытым методом (то есть между вызовами [метода опенмесод](isymunmanagedwriter-openmethod-method.md)и [методом клосемесод](isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="c15ae-122">Must use with an opened method (that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="c15ae-123">Интерфейс ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="c15ae-123">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)  
 <span data-ttu-id="c15ae-124">Представляет модуль привязки символов для неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="c15ae-124">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="c15ae-125">Интерфейс ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="c15ae-125">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="c15ae-126">Представляет связыватель символов для неуправляемого кода и расширяет `ISymUnmanagedBinder` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="c15ae-126">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="c15ae-127">Интерфейс ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="c15ae-127">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="c15ae-128">Представляет связыватель символов для неуправляемого кода и расширяет `ISymUnmanagedBinder` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="c15ae-128">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="c15ae-129">Интерфейс ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="c15ae-129">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)  
 <span data-ttu-id="c15ae-130">Предоставляет доступ к неуправляемым константам.</span><span class="sxs-lookup"><span data-stu-id="c15ae-130">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="c15ae-131">Интерфейс ISymUnmanagedDispose</span><span class="sxs-lookup"><span data-stu-id="c15ae-131">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)  
 <span data-ttu-id="c15ae-132">Уничтожает неуправляемые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="c15ae-132">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="c15ae-133">Интерфейс ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="c15ae-133">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)  
 <span data-ttu-id="c15ae-134">Представляет документ, на который ссылается хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="c15ae-134">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="c15ae-135">Интерфейс ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="c15ae-135">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="c15ae-136">Предоставляет методы для записи в документ, на который ссылается хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="c15ae-136">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="c15ae-137">Интерфейс ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="c15ae-137">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="c15ae-138">Предоставляет методы для функции "изменить и продолжить".</span><span class="sxs-lookup"><span data-stu-id="c15ae-138">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="c15ae-139">Интерфейс ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="c15ae-139">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)  
 <span data-ttu-id="c15ae-140">Представляет метод в хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="c15ae-140">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="c15ae-141">Интерфейс ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="c15ae-141">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)  
 <span data-ttu-id="c15ae-142">Представляет пространство имен.</span><span class="sxs-lookup"><span data-stu-id="c15ae-142">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="c15ae-143">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="c15ae-143">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)  
 <span data-ttu-id="c15ae-144">Представляет средство чтения символов, которое предоставляет доступ к документам, методам и переменным в хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="c15ae-144">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="c15ae-145">Интерфейс ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="c15ae-145">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)  
 <span data-ttu-id="c15ae-146">Возвращает метод чтения символов по заданному токену метода и номеру версии для редактирования и копирования.</span><span class="sxs-lookup"><span data-stu-id="c15ae-146">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="c15ae-147">Интерфейс ISymUnmanagedReaderSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="c15ae-147">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="c15ae-148">Предоставляет методы, которые получают сведения о поиске символов.</span><span class="sxs-lookup"><span data-stu-id="c15ae-148">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="c15ae-149">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="c15ae-149">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)  
 <span data-ttu-id="c15ae-150">Представляет лексическую область внутри метода.</span><span class="sxs-lookup"><span data-stu-id="c15ae-150">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="c15ae-151">Интерфейс ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="c15ae-151">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)  
 <span data-ttu-id="c15ae-152">Представляет лексическую область внутри метода и расширяет `ISymUnmanagedScope` интерфейс методами, которые получают сведения о константах, определенных в области.</span><span class="sxs-lookup"><span data-stu-id="c15ae-152">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="c15ae-153">Интерфейс ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="c15ae-153">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="c15ae-154">Предоставляет данные сервера-источника для модуля.</span><span class="sxs-lookup"><span data-stu-id="c15ae-154">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="c15ae-155">Интерфейс ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="c15ae-155">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="c15ae-156">Предоставляет методы, получающие сведения о пути поиска.</span><span class="sxs-lookup"><span data-stu-id="c15ae-156">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="c15ae-157">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="c15ae-157">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)  
 <span data-ttu-id="c15ae-158">Представляет переменную, например параметр, локальную переменную или поле.</span><span class="sxs-lookup"><span data-stu-id="c15ae-158">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="c15ae-159">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="c15ae-159">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)  
 <span data-ttu-id="c15ae-160">Представляет средство записи символов и предоставляет методы для определения документов, точек следования, лексических областей и переменных.</span><span class="sxs-lookup"><span data-stu-id="c15ae-160">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="c15ae-161">Интерфейс ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="c15ae-161">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="c15ae-162">Представляет средство записи символов и предоставляет методы для определения документов, точек следования, лексических областей и переменных.</span><span class="sxs-lookup"><span data-stu-id="c15ae-162">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="c15ae-163">Расширяет `ISymUnmanagedWriter` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="c15ae-163">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="c15ae-164">Интерфейс ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="c15ae-164">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="c15ae-165">Представляет средство записи символов и предоставляет методы для определения документов, точек следования, лексических областей и переменных.</span><span class="sxs-lookup"><span data-stu-id="c15ae-165">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="c15ae-166">Расширяет `ISymUnmanagedWriter` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="c15ae-166">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="c15ae-167">Интерфейс ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="c15ae-167">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="c15ae-168">Интерфейс ISymUnmanagedWriter4.</span><span class="sxs-lookup"><span data-stu-id="c15ae-168">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="c15ae-169">Интерфейс ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="c15ae-169">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="c15ae-170">Интерфейс ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="c15ae-170">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c15ae-171">См. также</span><span class="sxs-lookup"><span data-stu-id="c15ae-171">Related Sections</span></span>  

 [<span data-ttu-id="c15ae-172">Перечисления хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="c15ae-172">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="c15ae-173">Структуры хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="c15ae-173">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="c15ae-174">Отладка</span><span class="sxs-lookup"><span data-stu-id="c15ae-174">Debugging</span></span>](../debugging/index.md)
