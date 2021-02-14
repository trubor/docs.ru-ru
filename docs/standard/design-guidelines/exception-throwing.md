---
description: 'Узнайте подробнее о: Создание исключений'
title: Создание исключений
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: b1cf7a4eecc32a9f76ea06c47dd6c16d3afe5470
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642140"
---
# <a name="exception-throwing"></a><span data-ttu-id="ecbb7-103">Создание исключений</span><span class="sxs-lookup"><span data-stu-id="ecbb7-103">Exception Throwing</span></span>

<span data-ttu-id="ecbb7-104">Чтобы использовать рекомендации по созданию исключений, описанных в этом разделе, необходимо хорошо понимать, что такое сбой при выполнении.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-104">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="ecbb7-105">Сбой при выполнении происходит каждый раз, когда элемент не может выполнить действие, для которого он был создан (что предполагает его имя).</span><span class="sxs-lookup"><span data-stu-id="ecbb7-105">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="ecbb7-106">Например, если метод `OpenFile` не может вернуть открытый дескриптор файла вызывающему объекту, это будет считаться сбоем при выполнении.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-106">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>

 <span data-ttu-id="ecbb7-107">Большинство разработчиков хорошо знакомы с использованием исключений для ошибок использования, таких как деление на ноль или пустая ссылка.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-107">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="ecbb7-108">На платформе исключения используются для всех условий ошибок, включая ошибки выполнения.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-108">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>

 <span data-ttu-id="ecbb7-109">❌ НЕ возвращайте коды ошибок.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-109">❌ DO NOT return error codes.</span></span>

 <span data-ttu-id="ecbb7-110">Исключения являются основным средством для ведения отчетов об ошибках на платформах.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-110">Exceptions are the primary means of reporting errors in frameworks.</span></span>

 <span data-ttu-id="ecbb7-111">✔️ НЕ сообщайте о сбоях при выполнении, создавая исключения.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-111">✔️ DO report execution failures by throwing exceptions.</span></span>

 <span data-ttu-id="ecbb7-112">✔️ РАССМОТРИТЕ возможность завершения процесса, вызвав `System.Environment.FailFast` (функция .NET Framework 2.0) вместо создания исключения, если возникает ситуация, когда дальнейшее выполнение кода небезопасно.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-112">✔️ CONSIDER terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>

 <span data-ttu-id="ecbb7-113">❌ НЕ используйте исключения для обычного потока управления, если это возможно.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-113">❌ DO NOT use exceptions for the normal flow of control, if possible.</span></span>

 <span data-ttu-id="ecbb7-114">За исключением системных сбоев и операций с потенциальными состояниями гонки, конструкторы платформы должны разрабатывать интерфейсы API так, чтобы пользователи могли писать код, который не создает исключения.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-114">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="ecbb7-115">Например, можно предоставить способ проверки предусловий перед вызовом элемента, чтобы пользователи могли написать код, который не создает исключения.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-115">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>

 <span data-ttu-id="ecbb7-116">Элемент, используемый для проверки предусловий другого элемента, часто называется тестировщиком (tester), а элемент, который фактически выполняет работу, — исполнителем (doer).</span><span class="sxs-lookup"><span data-stu-id="ecbb7-116">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>

 <span data-ttu-id="ecbb7-117">Бывают случаи, когда шаблон Tester-Doer может иметь неприемлемо низкую производительность.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-117">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="ecbb7-118">В качестве альтернативы вы можете использовать шаблон Try-Parse (дополнительные сведения см. в статье [Исключения и производительность](exceptions-and-performance.md)).</span><span class="sxs-lookup"><span data-stu-id="ecbb7-118">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](exceptions-and-performance.md) for more information).</span></span>

 <span data-ttu-id="ecbb7-119">✔️ ОЦЕНИТЕ влияние создания исключений на производительность.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-119">✔️ CONSIDER the performance implications of throwing exceptions.</span></span> <span data-ttu-id="ecbb7-120">Создание свыше 100 исключений в секунду, скорее всего, заметно повлияет на производительность большинства приложений.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-120">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>

 <span data-ttu-id="ecbb7-121">✔️ ЗАДОКУМЕНТИРУЙТЕ все исключения, созданные открыто вызываемыми элементами из-за нарушения контракта элемента (а не сбоя системы). Рассматривайте их как часть контракта.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-121">✔️ DO document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>

 <span data-ttu-id="ecbb7-122">Исключения, которые являются частью контракта, не должны изменяться при обновлении версии (т. е. не следует изменять тип исключения и добавлять новые исключения).</span><span class="sxs-lookup"><span data-stu-id="ecbb7-122">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>

 <span data-ttu-id="ecbb7-123">❌ НЕ используйте открытые элементы, которые могут создавать либо не создавать исключения, в зависимости от определенного условия.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-123">❌ DO NOT have public members that can either throw or not based on some option.</span></span>

 <span data-ttu-id="ecbb7-124">❌ НЕ используйте открытые элементы, которые возвращают исключения в качестве возвращаемого значения или параметра `out`.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-124">❌ DO NOT have public members that return exceptions as the return value or an `out` parameter.</span></span>

 <span data-ttu-id="ecbb7-125">Если исключения не создаются, а возвращаются из открытых интерфейсов API, многие преимущества создания отчетов об ошибках на основе исключений будут потеряны.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-125">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>

 <span data-ttu-id="ecbb7-126">✔️ Рассмотрите возможность использования методов построителя исключений.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-126">✔️ CONSIDER using exception builder methods.</span></span>

 <span data-ttu-id="ecbb7-127">Обычно создается одно и то же исключение из различных мест.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-127">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="ecbb7-128">Чтобы избежать раздувания кода, используйте вспомогательные методы, которые создают исключения и инициализируют их свойства.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-128">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>

 <span data-ttu-id="ecbb7-129">Кроме того, элементы, которые создают исключения, не являются встроенными.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-129">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="ecbb7-130">Перемещение оператора throw в построитель может привести к встраиванию элемента.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-130">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>

 <span data-ttu-id="ecbb7-131">❌ НЕ создавайте исключения из блоков фильтра исключений.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-131">❌ DO NOT throw exceptions from exception filter blocks.</span></span>

 <span data-ttu-id="ecbb7-132">Если фильтр исключений вызывает исключение, то оно перехватывается средой CLR, а фильтр возвращает значение false.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-132">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="ecbb7-133">Это поведение неотличимо от применения фильтра и явным образом возвращает значение false, поэтому его очень сложно отлаживать.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-133">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>

 <span data-ttu-id="ecbb7-134">❌ ИЗБЕГАЙТЕ явного создания исключений из блоков finally.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-134">❌ AVOID explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="ecbb7-135">Допускаются неявно созданные исключения в результате вызова методов.</span><span class="sxs-lookup"><span data-stu-id="ecbb7-135">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>

 <span data-ttu-id="ecbb7-136">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="ecbb7-136">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ecbb7-137">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="ecbb7-137">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ecbb7-138">См. также</span><span class="sxs-lookup"><span data-stu-id="ecbb7-138">See also</span></span>

- [<span data-ttu-id="ecbb7-139">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="ecbb7-139">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="ecbb7-140">Правила разработки исключений</span><span class="sxs-lookup"><span data-stu-id="ecbb7-140">Design Guidelines for Exceptions</span></span>](exceptions.md)
