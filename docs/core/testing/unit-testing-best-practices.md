---
title: Рекомендации по написанию модульных тестов
description: Ознакомьтесь с рекомендациями по написанию модульных тестов, которые повысят качество и устойчивость кода, для проектов NET Core и .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 56f51cde0e52a9e6a38e5291c81470beee61adef
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678110"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="a282a-103">Рекомендации по модульному тестированию для .NET Core и .NET Standard</span><span class="sxs-lookup"><span data-stu-id="a282a-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="a282a-104">Существует множество преимуществ написания модульных тестов: они помогают с регрессией, предоставляют документацию и способствуют хорошей структуре кода.</span><span class="sxs-lookup"><span data-stu-id="a282a-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="a282a-105">Но трудночитаемые и ненадежные модульные тесты могут негативно отразиться на базе кода.</span><span class="sxs-lookup"><span data-stu-id="a282a-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="a282a-106">В этой статье приведены некоторые рекомендации, касающиеся разработки модульных тестов для проектов .NET Core и .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="a282a-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="a282a-107">В этом руководстве вы получите некоторые практические рекомендации по написанию модульных тестов, чтобы создавать устойчивые и понятные тесты.</span><span class="sxs-lookup"><span data-stu-id="a282a-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="a282a-108">Автор: [Джон Риз (John Reese)](https://reese.dev) с особой благодарностью [Рою Ошерову (Roy Osherove)](https://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="a282a-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](https://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="a282a-109">Почему именно модульные тесты?</span><span class="sxs-lookup"><span data-stu-id="a282a-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="a282a-110">Меньше времени на выполнение функциональных тестов</span><span class="sxs-lookup"><span data-stu-id="a282a-110">Less time performing functional tests</span></span>

<span data-ttu-id="a282a-111">Функциональные тесты требуют большого количества ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a282a-111">Functional tests are expensive.</span></span> <span data-ttu-id="a282a-112">Как правило, приходится открывать приложение и выполнять ряд действий, чтобы проверить ожидаемое поведение.</span><span class="sxs-lookup"><span data-stu-id="a282a-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="a282a-113">Тест-инженеры не всегда знают, что это за действия, и им приходится обращаться к специалистам в этой области.</span><span class="sxs-lookup"><span data-stu-id="a282a-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="a282a-114">Само тестирование может занимать несколько секунд, если это обычные изменения, или несколько минут для более масштабных изменений.</span><span class="sxs-lookup"><span data-stu-id="a282a-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="a282a-115">Наконец, этот процесс необходимо повторять для каждого изменения, внесенного в систему.</span><span class="sxs-lookup"><span data-stu-id="a282a-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="a282a-116">Модульные тесты, с другой стороны, занимают миллисекунды, выполняются простым нажатием кнопки и не обязательно требуют знаний о всей системе в целом.</span><span class="sxs-lookup"><span data-stu-id="a282a-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button, and don't necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="a282a-117">Успешность прохождения теста зависит от средства выполнения теста, а не от пользователя.</span><span class="sxs-lookup"><span data-stu-id="a282a-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="a282a-118">Защита от регрессии</span><span class="sxs-lookup"><span data-stu-id="a282a-118">Protection against regression</span></span>

<span data-ttu-id="a282a-119">Дефекты регрессии вводятся при внесении изменений в приложение.</span><span class="sxs-lookup"><span data-stu-id="a282a-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="a282a-120">Довольно часто тест-инженеры тестируют не только новую функцию, но и функции, существовавшие до этого, чтобы проверить, что эти функции по-прежнему работают должным образом.</span><span class="sxs-lookup"><span data-stu-id="a282a-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="a282a-121">С модульным тестированием можно повторно запускать весь набор тестов после каждой сборки или даже после изменения строки кода.</span><span class="sxs-lookup"><span data-stu-id="a282a-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="a282a-122">Это дает вам уверенность, что ваш новый код не нарушил существующие функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="a282a-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="a282a-123">Исполняемая документация</span><span class="sxs-lookup"><span data-stu-id="a282a-123">Executable documentation</span></span>

<span data-ttu-id="a282a-124">Не всегда очевидно, что делает конкретный метод или как он себя ведет при определенных входных данных.</span><span class="sxs-lookup"><span data-stu-id="a282a-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="a282a-125">Вы можете спросить себя: как поведет себя метод, если я передам ему пустую строку?</span><span class="sxs-lookup"><span data-stu-id="a282a-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="a282a-126">А значение NULL?</span><span class="sxs-lookup"><span data-stu-id="a282a-126">Null?</span></span>

<span data-ttu-id="a282a-127">Если у вас есть набор модульных тестов с понятными именами, каждый тест сможет четко объяснить, какими будут выходные данные для определенных входных данных.</span><span class="sxs-lookup"><span data-stu-id="a282a-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="a282a-128">Кроме того, он сможет проверить, что это действительно работает.</span><span class="sxs-lookup"><span data-stu-id="a282a-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="a282a-129">Менее связанный код</span><span class="sxs-lookup"><span data-stu-id="a282a-129">Less coupled code</span></span>

<span data-ttu-id="a282a-130">Если код тесно связан, он плохо подходит для модульного тестирования.</span><span class="sxs-lookup"><span data-stu-id="a282a-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="a282a-131">Без создания модульных тестов для кода это связывание может быть менее очевидным.</span><span class="sxs-lookup"><span data-stu-id="a282a-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="a282a-132">Когда вы пишете тесты для кода, вы естественным образом разделяете его, иначе его будет сложнее тестировать.</span><span class="sxs-lookup"><span data-stu-id="a282a-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="a282a-133">Характеристики хорошего модульного теста</span><span class="sxs-lookup"><span data-stu-id="a282a-133">Characteristics of a good unit test</span></span>

- <span data-ttu-id="a282a-134">**Быстрый**.</span><span class="sxs-lookup"><span data-stu-id="a282a-134">**Fast**.</span></span> <span data-ttu-id="a282a-135">В хорошо разработанных проектах могут быть тысячи модульных тестов.</span><span class="sxs-lookup"><span data-stu-id="a282a-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="a282a-136">Модульные тесты должны выполняться очень быстро.</span><span class="sxs-lookup"><span data-stu-id="a282a-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="a282a-137">За миллисекунды.</span><span class="sxs-lookup"><span data-stu-id="a282a-137">Milliseconds.</span></span>
- <span data-ttu-id="a282a-138">**Изолированный**.</span><span class="sxs-lookup"><span data-stu-id="a282a-138">**Isolated**.</span></span> <span data-ttu-id="a282a-139">Модульные тесты являются автономными, могут выполняться изолированно и не имеют зависимостей от внешних факторов, таких как файловая система или база данных.</span><span class="sxs-lookup"><span data-stu-id="a282a-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="a282a-140">**Повторяемый**.</span><span class="sxs-lookup"><span data-stu-id="a282a-140">**Repeatable**.</span></span> <span data-ttu-id="a282a-141">Запуски модульного теста должны иметь согласованные результаты, то есть всегда возвращать одинаковый результат, если вы не вносите никаких изменений между запусками.</span><span class="sxs-lookup"><span data-stu-id="a282a-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="a282a-142">**Самопроверяющий**.</span><span class="sxs-lookup"><span data-stu-id="a282a-142">**Self-Checking**.</span></span> <span data-ttu-id="a282a-143">Тест должен автоматически определять, пройден он или нет, без участия пользователя.</span><span class="sxs-lookup"><span data-stu-id="a282a-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="a282a-144">**Уместный**.</span><span class="sxs-lookup"><span data-stu-id="a282a-144">**Timely**.</span></span> <span data-ttu-id="a282a-145">Время на написание модульного теста не должно значительно превышать время написания тестируемого кода.</span><span class="sxs-lookup"><span data-stu-id="a282a-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="a282a-146">Если вам кажется, что тестирование кода занимает слишком много времени по сравнению с написанием кода, продумайте структуру, более подходящую для тестирования.</span><span class="sxs-lookup"><span data-stu-id="a282a-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="code-coverage"></a><span data-ttu-id="a282a-147">Покрытие кода</span><span class="sxs-lookup"><span data-stu-id="a282a-147">Code coverage</span></span>

<span data-ttu-id="a282a-148">Высокий процент покрытия кода зачастую связан с более высоким качеством кода.</span><span class="sxs-lookup"><span data-stu-id="a282a-148">A high code coverage percentage is often associated with a higher quality of code.</span></span> <span data-ttu-id="a282a-149">Однако само по себе измерение *не может* определить качество кода.</span><span class="sxs-lookup"><span data-stu-id="a282a-149">However, the measurement itself *cannot* determine the quality of code.</span></span> <span data-ttu-id="a282a-150">Задание чрезмерно большого процента объема протестированного кода может снизить производительность.</span><span class="sxs-lookup"><span data-stu-id="a282a-150">Setting an overly ambitious code coverage percentage goal can be counterproductive.</span></span> <span data-ttu-id="a282a-151">Представьте себе сложный проект с тысячами условных ветвей и представьте, что объем протестированного кода составляет 95 %.</span><span class="sxs-lookup"><span data-stu-id="a282a-151">Imagine a complex project with thousands of conditional branches, and imagine that you set a goal of 95% code coverage.</span></span> <span data-ttu-id="a282a-152">В настоящее время проект поддерживает объем протестированного кода в 90 %.</span><span class="sxs-lookup"><span data-stu-id="a282a-152">Currently the project maintains 90% code coverage.</span></span> <span data-ttu-id="a282a-153">Время, затрачиваемое на принятие всех пограничных вариантов в оставшихся 5 %, может оказаться очень значительным, а ценность предложения быстро сокращается.</span><span class="sxs-lookup"><span data-stu-id="a282a-153">The amount of time it takes to account for all of the edge cases in the remaining 5% could be a massive undertaking, and the value proposition quickly diminishes.</span></span>

<span data-ttu-id="a282a-154">Высокий процент объема протестированного кода не является индикатором успеха и не подразумевает высокое качество кода.</span><span class="sxs-lookup"><span data-stu-id="a282a-154">A high code coverage percentage is not an indicator of success, nor does it imply high code quality.</span></span> <span data-ttu-id="a282a-155">Он представляет собой лишь объем кода, охваченного модульными тестами.</span><span class="sxs-lookup"><span data-stu-id="a282a-155">It just represents the amount of code that is covered by unit tests.</span></span> <span data-ttu-id="a282a-156">Дополнительные сведения см. в статье [Модульное тестирование объема протестированного кода](unit-testing-code-coverage.md).</span><span class="sxs-lookup"><span data-stu-id="a282a-156">For more information, see [unit testing code coverage](unit-testing-code-coverage.md).</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="a282a-157">Определимся с терминами</span><span class="sxs-lookup"><span data-stu-id="a282a-157">Let's speak the same language</span></span>

<span data-ttu-id="a282a-158">К сожалению, термин *макет* по отношению к тестированию часто употребляется неправильно.</span><span class="sxs-lookup"><span data-stu-id="a282a-158">The term *mock* is unfortunately often misused when talking about testing.</span></span> <span data-ttu-id="a282a-159">Следующие пункты определяют самые распространенные типы *заполнителей* при написании модульных тестов:</span><span class="sxs-lookup"><span data-stu-id="a282a-159">The following points define the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="a282a-160">*Заполнитель* — это общий термин, который можно использовать для описания заглушки или макета объекта.</span><span class="sxs-lookup"><span data-stu-id="a282a-160">*Fake* - A fake is a generic term that can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="a282a-161">Использование заглушки или макета зависит от контекста.</span><span class="sxs-lookup"><span data-stu-id="a282a-161">Whether it's a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="a282a-162">Иными словами, заполнитель может быть заглушкой или макетом.</span><span class="sxs-lookup"><span data-stu-id="a282a-162">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="a282a-163">*Макет*. Макет объекта — это объект-заполнитель в системе, который решает, пройден ли модульный тест.</span><span class="sxs-lookup"><span data-stu-id="a282a-163">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="a282a-164">Макет начинает существование как заполнитель, пока по нему не будет проведена проверка.</span><span class="sxs-lookup"><span data-stu-id="a282a-164">A mock starts out as a Fake until it's asserted against.</span></span>

<span data-ttu-id="a282a-165">*Заглушка* — это управляемая замена существующей зависимости (или участника) в системе.</span><span class="sxs-lookup"><span data-stu-id="a282a-165">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="a282a-166">С помощью заглушки можно протестировать код, не задействовав зависимость напрямую.</span><span class="sxs-lookup"><span data-stu-id="a282a-166">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="a282a-167">По умолчанию заглушка выступает как заполнитель.</span><span class="sxs-lookup"><span data-stu-id="a282a-167">By default, a stub starts out as a fake.</span></span>

<span data-ttu-id="a282a-168">Рассмотрим следующий фрагмент кода:</span><span class="sxs-lookup"><span data-stu-id="a282a-168">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="a282a-169">Это будет пример заглушки, которая будет называться макетом.</span><span class="sxs-lookup"><span data-stu-id="a282a-169">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="a282a-170">В данном случае это заглушка.</span><span class="sxs-lookup"><span data-stu-id="a282a-170">In this case, it is a stub.</span></span> <span data-ttu-id="a282a-171">Вы передаете Order, чтобы создать экземпляр `Purchase` (тестируемая система).</span><span class="sxs-lookup"><span data-stu-id="a282a-171">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="a282a-172">Имя `MockOrder` также вводит в заблуждение, поскольку Order не является макетом.</span><span class="sxs-lookup"><span data-stu-id="a282a-172">The name `MockOrder` is also misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="a282a-173">Лучше было бы так:</span><span class="sxs-lookup"><span data-stu-id="a282a-173">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="a282a-174">Если переименовать класс в `FakeOrder`, он будет более универсальным и его можно будет использовать как макет или как заглушку.</span><span class="sxs-lookup"><span data-stu-id="a282a-174">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="a282a-175">Это зависит от тестового случая.</span><span class="sxs-lookup"><span data-stu-id="a282a-175">Whichever is better for the test case.</span></span> <span data-ttu-id="a282a-176">В приведенном выше примере `FakeOrder` используется в качестве заглушки.</span><span class="sxs-lookup"><span data-stu-id="a282a-176">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="a282a-177">Вы никак не используете `FakeOrder` во время проверки.</span><span class="sxs-lookup"><span data-stu-id="a282a-177">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="a282a-178">`FakeOrder` передается в класс `Purchase`, чтобы удовлетворить требованиям конструктора.</span><span class="sxs-lookup"><span data-stu-id="a282a-178">`FakeOrder` was passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="a282a-179">Чтобы использовать его как макет, можно сделать нечто подобное:</span><span class="sxs-lookup"><span data-stu-id="a282a-179">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="a282a-180">В этом случае проверяется свойство заполнителя (выполняется проверка по нему), поэтому в приведенном выше фрагменте кода `mockOrder` является макетом.</span><span class="sxs-lookup"><span data-stu-id="a282a-180">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a282a-181">Очень важно правильно разобраться в терминологии.</span><span class="sxs-lookup"><span data-stu-id="a282a-181">It's important to get this terminology correct.</span></span> <span data-ttu-id="a282a-182">Если вы будете называть заглушки макетами, другие разработчики не поймут ваших намерений.</span><span class="sxs-lookup"><span data-stu-id="a282a-182">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="a282a-183">В первую очередь следует помнить, что макеты отличаются от заглушек тем, что вы выполняете проверку по макету объекта, но не выполняете проверку по заглушке.</span><span class="sxs-lookup"><span data-stu-id="a282a-183">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="a282a-184">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a282a-184">Best practices</span></span>

<span data-ttu-id="a282a-185">Попробуйте не создавать зависимости в инфраструктуре при написании модульных тестов.</span><span class="sxs-lookup"><span data-stu-id="a282a-185">Try not to introduce dependencies on infrastructure when writing unit tests.</span></span> <span data-ttu-id="a282a-186">Из-за этого тесты выполняются медленно и нестабильно. Зависимости следует использовать в интеграционных тестах.</span><span class="sxs-lookup"><span data-stu-id="a282a-186">These make the tests slow and brittle and should be reserved for integration tests.</span></span> <span data-ttu-id="a282a-187">Чтобы избежать появления зависимостей в коде приложения, следуйте [принципу явных зависимостей](https://deviq.com/explicit-dependencies-principle) и используйте [внедрение зависимостей](../extensions/dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="a282a-187">You can avoid these dependencies in your application by following the [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle) and using [Dependency Injection](../extensions/dependency-injection.md).</span></span> <span data-ttu-id="a282a-188">Вы также можете разместить модульные тесты в отдельном проекте, не содержащем интеграционных тестов.</span><span class="sxs-lookup"><span data-stu-id="a282a-188">You can also keep your unit tests in a separate project from your integration tests.</span></span> <span data-ttu-id="a282a-189">Это гарантирует отсутствие в проекте модульного теста ссылок на пакеты инфраструктуры или зависимостей от них.</span><span class="sxs-lookup"><span data-stu-id="a282a-189">This ensures your unit test project doesn't have references to or dependencies on infrastructure packages.</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="a282a-190">Выбор имен для тестов</span><span class="sxs-lookup"><span data-stu-id="a282a-190">Naming your tests</span></span>

<span data-ttu-id="a282a-191">Имя теста должно состоять из трех частей:</span><span class="sxs-lookup"><span data-stu-id="a282a-191">The name of your test should consist of three parts:</span></span>

- <span data-ttu-id="a282a-192">имя тестируемого метода;</span><span class="sxs-lookup"><span data-stu-id="a282a-192">The name of the method being tested.</span></span>
- <span data-ttu-id="a282a-193">сценарий, в котором выполняется тестирование;</span><span class="sxs-lookup"><span data-stu-id="a282a-193">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="a282a-194">ожидаемое поведение при вызове сценария.</span><span class="sxs-lookup"><span data-stu-id="a282a-194">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="a282a-195">Почему?</span><span class="sxs-lookup"><span data-stu-id="a282a-195">Why?</span></span>

- <span data-ttu-id="a282a-196">Стандарты именования важны, так как они выражают намерение теста.</span><span class="sxs-lookup"><span data-stu-id="a282a-196">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="a282a-197">Тесты не просто проверяют работоспособность кода — они также предоставляют документацию.</span><span class="sxs-lookup"><span data-stu-id="a282a-197">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="a282a-198">Просто посмотрев на набор модульных тестов, вы должны определить поведение кода, не глядя на сам код.</span><span class="sxs-lookup"><span data-stu-id="a282a-198">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="a282a-199">Кроме того, если тест не пройден, вы сразу увидите, какие сценарии не соответствуют вашим ожиданиям.</span><span class="sxs-lookup"><span data-stu-id="a282a-199">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="a282a-200">Плохо:</span><span class="sxs-lookup"><span data-stu-id="a282a-200">Bad:</span></span>

[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="a282a-201">Лучше:</span><span class="sxs-lookup"><span data-stu-id="a282a-201">Better:</span></span>

[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="a282a-202">Упорядочивание тестов</span><span class="sxs-lookup"><span data-stu-id="a282a-202">Arranging your tests</span></span>

<span data-ttu-id="a282a-203">**Упорядочивайте, действуйте, проверяйте** — это общий шаблон для модульного тестирования.</span><span class="sxs-lookup"><span data-stu-id="a282a-203">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="a282a-204">Как и предполагает название, он состоит из трех элементов.</span><span class="sxs-lookup"><span data-stu-id="a282a-204">As the name implies, it consists of three main actions:</span></span>

- <span data-ttu-id="a282a-205">*Упорядочивайте* объекты, создавая и настраивая их по необходимости.</span><span class="sxs-lookup"><span data-stu-id="a282a-205">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="a282a-206">*Действуйте*, работая с объектами.</span><span class="sxs-lookup"><span data-stu-id="a282a-206">*Act* on an object.</span></span>
- <span data-ttu-id="a282a-207">*Проверяйте*, что все выполняется, как ожидалось.</span><span class="sxs-lookup"><span data-stu-id="a282a-207">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="a282a-208">Почему?</span><span class="sxs-lookup"><span data-stu-id="a282a-208">Why?</span></span>

- <span data-ttu-id="a282a-209">Объект тестирования четко отделяется от этапов *упорядочивания* и *проверки*.</span><span class="sxs-lookup"><span data-stu-id="a282a-209">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="a282a-210">Меньше вероятности перепутать проверочные утверждения с кодом действия.</span><span class="sxs-lookup"><span data-stu-id="a282a-210">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="a282a-211">Удобочитаемость является одним из наиболее важных аспектов при написании тестов.</span><span class="sxs-lookup"><span data-stu-id="a282a-211">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="a282a-212">Четкое разделение каждого из этих действий в тесте подчеркивает зависимости, необходимые для вызова кода, указывает, как вызывается ваш код и что вы пытаетесь проверить.</span><span class="sxs-lookup"><span data-stu-id="a282a-212">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="a282a-213">Хотя некоторые шаги можно объединить и уменьшить размер теста, основной целью является удобочитаемость теста.</span><span class="sxs-lookup"><span data-stu-id="a282a-213">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="a282a-214">Плохо:</span><span class="sxs-lookup"><span data-stu-id="a282a-214">Bad:</span></span>

[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="a282a-215">Лучше:</span><span class="sxs-lookup"><span data-stu-id="a282a-215">Better:</span></span>

[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="a282a-216">Пишите минималистичные тесты</span><span class="sxs-lookup"><span data-stu-id="a282a-216">Write minimally passing tests</span></span>

<span data-ttu-id="a282a-217">Входные данные для модульного теста должны быть как можно проще, чтобы проверить поведение, которое вы тестируете в данный момент.</span><span class="sxs-lookup"><span data-stu-id="a282a-217">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="a282a-218">Почему?</span><span class="sxs-lookup"><span data-stu-id="a282a-218">Why?</span></span>

- <span data-ttu-id="a282a-219">Тесты становятся более устойчивыми к будущим изменениям в базе кода.</span><span class="sxs-lookup"><span data-stu-id="a282a-219">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="a282a-220">Ближе к тестированию поведения по сравнению с реализацией.</span><span class="sxs-lookup"><span data-stu-id="a282a-220">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="a282a-221">Тесты, которые включают больше информации, чем требуется для прохождения, могут содержать больше ошибок и затруднять понимание намерения.</span><span class="sxs-lookup"><span data-stu-id="a282a-221">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="a282a-222">При написании тестов необходимо сосредоточиться на поведении.</span><span class="sxs-lookup"><span data-stu-id="a282a-222">When writing tests, you want to focus on the behavior.</span></span> <span data-ttu-id="a282a-223">Установка дополнительных свойств для моделей или использование ненулевых значений, когда это не требуется, только затрудняет проверку.</span><span class="sxs-lookup"><span data-stu-id="a282a-223">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="a282a-224">Плохо:</span><span class="sxs-lookup"><span data-stu-id="a282a-224">Bad:</span></span>

[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="a282a-225">Лучше:</span><span class="sxs-lookup"><span data-stu-id="a282a-225">Better:</span></span>

[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="a282a-226">Избегайте "магических" строк</span><span class="sxs-lookup"><span data-stu-id="a282a-226">Avoid magic strings</span></span>

<span data-ttu-id="a282a-227">Именование переменных в модульных тестах так же важно, как именование переменных в рабочем коде, если не важнее.</span><span class="sxs-lookup"><span data-stu-id="a282a-227">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="a282a-228">Модульные тесты не должны содержать "магических" строк.</span><span class="sxs-lookup"><span data-stu-id="a282a-228">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="a282a-229">Почему?</span><span class="sxs-lookup"><span data-stu-id="a282a-229">Why?</span></span>

- <span data-ttu-id="a282a-230">Избавит читателя теста от необходимости проверять рабочий код, чтобы выяснить, что делает значение особенным.</span><span class="sxs-lookup"><span data-stu-id="a282a-230">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="a282a-231">Явно показывает, что вы пытаетесь *проверить*, а не *выполнить*.</span><span class="sxs-lookup"><span data-stu-id="a282a-231">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="a282a-232">"Магические" строки могут запутать читателя тестов.</span><span class="sxs-lookup"><span data-stu-id="a282a-232">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="a282a-233">Если строка выглядит необычно, у него может возникнуть вопрос, почему было выбрано определенное значение для параметра или возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="a282a-233">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="a282a-234">И ему придется рассматривать детали реализации, вместо того чтобы сосредоточиться на тесте.</span><span class="sxs-lookup"><span data-stu-id="a282a-234">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP]
> <span data-ttu-id="a282a-235">При написании тестов старайтесь как можно яснее выразить свое намерение.</span><span class="sxs-lookup"><span data-stu-id="a282a-235">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="a282a-236">В случае "магических" строк рекомендуется присваивать эти значения константам.</span><span class="sxs-lookup"><span data-stu-id="a282a-236">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="a282a-237">Плохо:</span><span class="sxs-lookup"><span data-stu-id="a282a-237">Bad:</span></span>

[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="a282a-238">Лучше:</span><span class="sxs-lookup"><span data-stu-id="a282a-238">Better:</span></span>

[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="a282a-239">Избегайте логики в тестах</span><span class="sxs-lookup"><span data-stu-id="a282a-239">Avoid logic in tests</span></span>

<span data-ttu-id="a282a-240">При написании модульных тестов избегайте объединения строк вручную и логических условий, таких как `if`, `while`, `for`, `switch` и т. д.</span><span class="sxs-lookup"><span data-stu-id="a282a-240">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="a282a-241">Почему?</span><span class="sxs-lookup"><span data-stu-id="a282a-241">Why?</span></span>

- <span data-ttu-id="a282a-242">Меньше шансов внедрить ошибку в тесты.</span><span class="sxs-lookup"><span data-stu-id="a282a-242">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="a282a-243">Направленность на конечный результат, а не на детали реализации.</span><span class="sxs-lookup"><span data-stu-id="a282a-243">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="a282a-244">При введении логики в набор тестов вероятность появления ошибок значительно возрастает.</span><span class="sxs-lookup"><span data-stu-id="a282a-244">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="a282a-245">Меньше всего вам нужна ошибка в наборе тестов.</span><span class="sxs-lookup"><span data-stu-id="a282a-245">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="a282a-246">Вы должны быть уверены, что тесты работают. Иначе вы не сможете им доверять.</span><span class="sxs-lookup"><span data-stu-id="a282a-246">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="a282a-247">Если вы не доверяете тесту, он бесполезен.</span><span class="sxs-lookup"><span data-stu-id="a282a-247">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="a282a-248">Если тест не пройден, вы должны знать, что с кодом действительно что-то не так и это нельзя игнорировать.</span><span class="sxs-lookup"><span data-stu-id="a282a-248">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="a282a-249">Если логика в тесте неизбежна, рекомендуется разбить тест на несколько тестов.</span><span class="sxs-lookup"><span data-stu-id="a282a-249">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="a282a-250">Плохо:</span><span class="sxs-lookup"><span data-stu-id="a282a-250">Bad:</span></span>

[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="a282a-251">Лучше:</span><span class="sxs-lookup"><span data-stu-id="a282a-251">Better:</span></span>

[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="a282a-252">Выбирайте вспомогательные методы вместо установки и удаления</span><span class="sxs-lookup"><span data-stu-id="a282a-252">Prefer helper methods to setup and teardown</span></span>

<span data-ttu-id="a282a-253">Если вам требуется аналогичный объект или состояние для тестов, лучше используйте вспомогательный метод, чем атрибуты `Setup` и `Teardown`, если они существуют.</span><span class="sxs-lookup"><span data-stu-id="a282a-253">If you require a similar object or state for your tests, prefer a helper method than leveraging `Setup` and `Teardown` attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="a282a-254">Почему?</span><span class="sxs-lookup"><span data-stu-id="a282a-254">Why?</span></span>

- <span data-ttu-id="a282a-255">Меньше путаницы при чтении тестов, так как весь код виден в каждом тесте.</span><span class="sxs-lookup"><span data-stu-id="a282a-255">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="a282a-256">Меньше шансов настроить слишком много или слишком мало для определенного теста.</span><span class="sxs-lookup"><span data-stu-id="a282a-256">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="a282a-257">Меньше шансов совместного использования состояния несколькими тестами, что приводит к нежелательным зависимостям между ними.</span><span class="sxs-lookup"><span data-stu-id="a282a-257">Less chance of sharing state between tests, which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="a282a-258">В модульном тестировании `Setup` вызывается до всех модульных тестов в наборе.</span><span class="sxs-lookup"><span data-stu-id="a282a-258">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="a282a-259">Хотя некоторые считают это полезным инструментом, в конечном итоге тесты сложно воспринимать.</span><span class="sxs-lookup"><span data-stu-id="a282a-259">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="a282a-260">Каждый тест обычно имеет различные требования для запуска.</span><span class="sxs-lookup"><span data-stu-id="a282a-260">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="a282a-261">К сожалению, `Setup` заставляет вас использовать одинаковые требования для всех тестов.</span><span class="sxs-lookup"><span data-stu-id="a282a-261">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE]
> <span data-ttu-id="a282a-262">В xUnit удалены SetUp и TearDown в версии 2.x.</span><span class="sxs-lookup"><span data-stu-id="a282a-262">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="a282a-263">Плохо:</span><span class="sxs-lookup"><span data-stu-id="a282a-263">Bad:</span></span>

[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="a282a-264">Лучше:</span><span class="sxs-lookup"><span data-stu-id="a282a-264">Better:</span></span>

[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="a282a-265">Избегайте нескольких проверочных утверждений</span><span class="sxs-lookup"><span data-stu-id="a282a-265">Avoid multiple asserts</span></span>

<span data-ttu-id="a282a-266">При написании тестов попробуйте включить только одно проверочное утверждение в каждый тест.</span><span class="sxs-lookup"><span data-stu-id="a282a-266">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="a282a-267">Общие подходы к использованию только одного проверочного утверждения включают следующее.</span><span class="sxs-lookup"><span data-stu-id="a282a-267">Common approaches to using only one assert include:</span></span>

- <span data-ttu-id="a282a-268">Создание отдельного теста для каждого проверочного утверждения.</span><span class="sxs-lookup"><span data-stu-id="a282a-268">Create a separate test for each assert.</span></span>
- <span data-ttu-id="a282a-269">Использование параметризованных тестов.</span><span class="sxs-lookup"><span data-stu-id="a282a-269">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="a282a-270">Почему?</span><span class="sxs-lookup"><span data-stu-id="a282a-270">Why?</span></span>

- <span data-ttu-id="a282a-271">Если одно проверочное утверждение завершится неудачей, последующие не будут вычисляться.</span><span class="sxs-lookup"><span data-stu-id="a282a-271">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="a282a-272">Гарантирует, что вы не будете проверять несколько случаев в тестах.</span><span class="sxs-lookup"><span data-stu-id="a282a-272">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="a282a-273">Предоставляет полную картину о том, почему тесты завершаются неудачей.</span><span class="sxs-lookup"><span data-stu-id="a282a-273">Gives you the entire picture as to why your tests are failing.</span></span>

<span data-ttu-id="a282a-274">При использовании нескольких проверочных утверждений в тестовом случае у вас нет гарантии, что все утверждения будут выполняться.</span><span class="sxs-lookup"><span data-stu-id="a282a-274">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="a282a-275">В большинстве платформ модульного тестирования, когда одно утверждение в модульном тесте завершается неудачей, все последующие тесты считаются непройденными.</span><span class="sxs-lookup"><span data-stu-id="a282a-275">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="a282a-276">Это может вызывать путаницу, так как действующие функции будут казаться неработоспособными.</span><span class="sxs-lookup"><span data-stu-id="a282a-276">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="a282a-277">Общее исключение из этого правила — проверка объекта.</span><span class="sxs-lookup"><span data-stu-id="a282a-277">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="a282a-278">В этом случае обычно допустимо иметь несколько утверждений для каждого свойства, чтобы убедиться, что объект находится в ожидаемом состоянии.</span><span class="sxs-lookup"><span data-stu-id="a282a-278">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="a282a-279">Плохо:</span><span class="sxs-lookup"><span data-stu-id="a282a-279">Bad:</span></span>

[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="a282a-280">Лучше:</span><span class="sxs-lookup"><span data-stu-id="a282a-280">Better:</span></span>

[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="a282a-281">Проверяйте закрытые методы путем модульного тестирования открытых методов</span><span class="sxs-lookup"><span data-stu-id="a282a-281">Validate private methods by unit testing public methods</span></span>

<span data-ttu-id="a282a-282">В большинстве случаев вам не понадобится тестировать закрытые методы.</span><span class="sxs-lookup"><span data-stu-id="a282a-282">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="a282a-283">Закрытые методы относятся к тонкостям реализации.</span><span class="sxs-lookup"><span data-stu-id="a282a-283">Private methods are an implementation detail.</span></span> <span data-ttu-id="a282a-284">Подумайте об этом так: закрытые методы никогда не существуют в изоляции.</span><span class="sxs-lookup"><span data-stu-id="a282a-284">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="a282a-285">Рано или поздно у вас будет открытый метод, вызывающий закрытый метод в рамках его реализации.</span><span class="sxs-lookup"><span data-stu-id="a282a-285">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="a282a-286">Вам следует думать о конечном результате открытого метода, который вызывает закрытый метод.</span><span class="sxs-lookup"><span data-stu-id="a282a-286">What you should care about is the end result of the public method that calls into the private one.</span></span>

<span data-ttu-id="a282a-287">Рассмотрим следующий случай.</span><span class="sxs-lookup"><span data-stu-id="a282a-287">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="a282a-288">Возможно, в первую очередь вам захочется написать тест для `TrimInput`, поскольку вы хотите убедиться, что метод работает должным образом.</span><span class="sxs-lookup"><span data-stu-id="a282a-288">Your first reaction may be to start writing a test for `TrimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="a282a-289">Но вполне возможно, что `ParseLogLine` манипулирует `sanitizedInput` неожиданным для вас образом и тестирование `TrimInput` окажется бесполезным.</span><span class="sxs-lookup"><span data-stu-id="a282a-289">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `TrimInput` useless.</span></span>

<span data-ttu-id="a282a-290">Настоящий тест нужно провести для открытого метода `ParseLogLine`, потому что в конечном итоге для вас важен именно он.</span><span class="sxs-lookup"><span data-stu-id="a282a-290">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span>

```csharp
public void ParseLogLine_StartsAndEndsWithSpace_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="a282a-291">С этой точки зрения, если вы видите закрытый метод, найдите открытый метод и напишите тесты для него.</span><span class="sxs-lookup"><span data-stu-id="a282a-291">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="a282a-292">Тот факт, что закрытый метод возвращает ожидаемый результат, вовсе не означает, что система, которая вызывает закрытый метод, использует этот результат правильно.</span><span class="sxs-lookup"><span data-stu-id="a282a-292">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="a282a-293">Используйте заглушки для статических ссылок</span><span class="sxs-lookup"><span data-stu-id="a282a-293">Stub static references</span></span>

<span data-ttu-id="a282a-294">Один из принципов модульного тестирования — его полный контроль над тестируемой системой.</span><span class="sxs-lookup"><span data-stu-id="a282a-294">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="a282a-295">Это может быть проблематичным, когда рабочий код вызывает статические ссылки (например, `DateTime.Now`).</span><span class="sxs-lookup"><span data-stu-id="a282a-295">This can be problematic when production code includes calls to static references (for example, `DateTime.Now`).</span></span> <span data-ttu-id="a282a-296">Рассмотрим следующий код.</span><span class="sxs-lookup"><span data-stu-id="a282a-296">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if (DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="a282a-297">Как можно провести модульное тестирование этого кода?</span><span class="sxs-lookup"><span data-stu-id="a282a-297">How can this code possibly be unit tested?</span></span> <span data-ttu-id="a282a-298">Вы можете попробовать следующий подход.</span><span class="sxs-lookup"><span data-stu-id="a282a-298">You may try an approach such as</span></span>

```csharp
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="a282a-299">К сожалению, вы быстро поймете, что в тестах есть несколько проблем.</span><span class="sxs-lookup"><span data-stu-id="a282a-299">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span>

- <span data-ttu-id="a282a-300">Если набор тестов выполняется во вторник, второй тест будет пройден, а первый — нет.</span><span class="sxs-lookup"><span data-stu-id="a282a-300">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="a282a-301">Если набор тестов выполняется в другой день, первый тест будет пройден, а второй — нет.</span><span class="sxs-lookup"><span data-stu-id="a282a-301">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="a282a-302">Для решения этих проблем вам потребуется ввести *шов* в рабочий код.</span><span class="sxs-lookup"><span data-stu-id="a282a-302">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="a282a-303">Например, можно заключить код, который необходимо контролировать, в интерфейс, чтобы рабочий код зависел от этого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a282a-303">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if (dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="a282a-304">Набор тестов теперь выглядит так.</span><span class="sxs-lookup"><span data-stu-id="a282a-304">Your test suite now becomes</span></span>

```csharp
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="a282a-305">Теперь набор тестов имеет полный контроль над `DateTime.Now` и может использовать заглушку для любого значения при вызове метода.</span><span class="sxs-lookup"><span data-stu-id="a282a-305">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
