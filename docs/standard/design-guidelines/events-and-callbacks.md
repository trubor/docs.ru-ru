---
description: 'Узнайте подробнее о: События и обратные вызовы'
title: События и обратные вызовы
ms.date: 10/22/2008
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: 8a9049808ec0f7a490889ab1f17c4d8b8e8bd2b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642153"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="b27ef-103">События и обратные вызовы</span><span class="sxs-lookup"><span data-stu-id="b27ef-103">Events and Callbacks</span></span>

<span data-ttu-id="b27ef-104">Обратные вызовы — это точки расширяемости, позволяющие платформе выполнять обратный вызов пользовательского кода через делегат.</span><span class="sxs-lookup"><span data-stu-id="b27ef-104">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="b27ef-105">Обычно эти делегаты передаются в платформу с помощью параметра метода.</span><span class="sxs-lookup"><span data-stu-id="b27ef-105">These delegates are usually passed to the framework through a parameter of a method.</span></span>

 <span data-ttu-id="b27ef-106">События представляют собой особый случай обратных вызовов, которые поддерживают удобный и единообразный синтаксис для предоставления делегата (обработчика событий).</span><span class="sxs-lookup"><span data-stu-id="b27ef-106">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="b27ef-107">К тому же, завершение операторов и конструкторы Visual Studio помогают использовать интерфейсы API на основе событий.</span><span class="sxs-lookup"><span data-stu-id="b27ef-107">In addition, Visual Studio's statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="b27ef-108">(См. статью [Разработка событий](event.md).)</span><span class="sxs-lookup"><span data-stu-id="b27ef-108">(See [Event Design](event.md).)</span></span>

 <span data-ttu-id="b27ef-109">✔️ РАССМОТРИТЕ возможность использования обратных вызовов, чтобы разрешить пользователям предоставлять пользовательский код, который будет выполняться платформой.</span><span class="sxs-lookup"><span data-stu-id="b27ef-109">✔️ CONSIDER using callbacks to allow users to provide custom code to be executed by the framework.</span></span>

 <span data-ttu-id="b27ef-110">✔️ РАССМОТРИТЕ возможность использования событий, чтобы разрешить пользователям настраивать поведение платформы без необходимости понимания объектно-ориентированного проектирования.</span><span class="sxs-lookup"><span data-stu-id="b27ef-110">✔️ CONSIDER using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>

 <span data-ttu-id="b27ef-111">✔️ОТДАВАЙТЕ ПРЕДПОЧТЕНИЕ событиям, а не простым обратным вызовам, так как они более понятны для большинства разработчиков и интегрированы с возможностью завершения операторов Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b27ef-111">✔️ DO prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>

 <span data-ttu-id="b27ef-112">❌ ИЗБЕГАЙТЕ использования обратных вызовов в интерфейсах API, зависящих от производительности.</span><span class="sxs-lookup"><span data-stu-id="b27ef-112">❌ AVOID using callbacks in performance-sensitive APIs.</span></span>

 <span data-ttu-id="b27ef-113">✔️ При определении API с обратными вызовами вместо пользовательских делегатов используйте новые типы `Func<...>`, `Action<...>` или `Expression<...>`.</span><span class="sxs-lookup"><span data-stu-id="b27ef-113">✔️ DO use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>

 <span data-ttu-id="b27ef-114">`Func<...>` и `Action<...>` представляют универсальные методы-делегаты.</span><span class="sxs-lookup"><span data-stu-id="b27ef-114">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="b27ef-115">`Expression<...>` представляет определения функций, которые можно скомпилировать и впоследствии вызвать во время выполнения. Их также можно сериализовать и передать в удаленные процессы.</span><span class="sxs-lookup"><span data-stu-id="b27ef-115">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>

 <span data-ttu-id="b27ef-116">✔️ ИЗМЕРЯЙТЕ и изучайте влияние на производительность при использовании `Expression<...>` вместо делегатов `Func<...>` и `Action<...>`.</span><span class="sxs-lookup"><span data-stu-id="b27ef-116">✔️ DO measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>

 <span data-ttu-id="b27ef-117">Типы `Expression<...>` в большинстве случаев логически эквивалентны делегатам `Func<...>` и `Action<...>`.</span><span class="sxs-lookup"><span data-stu-id="b27ef-117">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="b27ef-118">Основное различие между ними заключается в том, что делегаты предназначены для использования в сценариях локальных процессов, а выражения предназначены для случаев, когда целесообразно и возможно оценить выражение в удаленном процессе или на компьютере.</span><span class="sxs-lookup"><span data-stu-id="b27ef-118">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it's beneficial and possible to evaluate the expression in a remote process or machine.</span></span>

 <span data-ttu-id="b27ef-119">✔️ ПОЙМИТЕ, что вызвав делегат, вы выполняете произвольный код, который может повлиять на безопасность, корректность работы и совместимость.</span><span class="sxs-lookup"><span data-stu-id="b27ef-119">✔️ DO understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>

 <span data-ttu-id="b27ef-120">*Фрагменты: &copy; Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="b27ef-120">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b27ef-121">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="b27ef-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b27ef-122">См. также</span><span class="sxs-lookup"><span data-stu-id="b27ef-122">See also</span></span>

- [<span data-ttu-id="b27ef-123">Разработка с обеспечением расширяемости</span><span class="sxs-lookup"><span data-stu-id="b27ef-123">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="b27ef-124">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="b27ef-124">Framework Design Guidelines</span></span>](index.md)
