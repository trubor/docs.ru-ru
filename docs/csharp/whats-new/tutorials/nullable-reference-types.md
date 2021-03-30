---
title: Разработка с использованием ссылочных типов, допускающих значение null
description: В этом расширенном руководстве содержатся общие сведения о ссылочных типах, допускающих значение null. Вы научитесь выражать проектный замысел относительно того, когда ссылочные значения могут иметь значение null, и используете компилятор, который будет применять соответствующее поведение, когда они не могут иметь значение null.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 01b05c6fa71c71546109cb25474b703458eb6e22
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104878979"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="45208-104">Учебник. Четкое выражение проектного замысла с помощью ссылочных типов, допускающих и не допускающих значение null</span><span class="sxs-lookup"><span data-stu-id="45208-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="45208-105">В C# 8.0 вводятся [ссылочные типы, допускающие значение NULL](../../nullable-references.md), которые дополняют ссылочные типы таким же образом, как типы значений, допускающие значение NULL, дополняют другие типы значений.</span><span class="sxs-lookup"><span data-stu-id="45208-105">C# 8.0 introduces [nullable reference types](../../nullable-references.md), which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="45208-106">Чтобы объявить переменную как имеющую **ссылочный тип, допускающий значение null**, добавьте `?` к типу.</span><span class="sxs-lookup"><span data-stu-id="45208-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="45208-107">Например, `string?` соответствует типу `string`, допускающему значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="45208-108">Эти новые типы можно использовать для более четкого выражения проектного замысла: некоторые переменные *всегда должны содержать значение*, а в других *они могут отсутствовать*.</span><span class="sxs-lookup"><span data-stu-id="45208-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="45208-109">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="45208-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="45208-110">Внедрять в проекты ссылочные типы, допускающие и не допускающие значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="45208-111">Включать в коде проверку ссылочных типов, допускающих значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="45208-112">Писать код, в котором компилятор принудительно применяет эти проектные решения.</span><span class="sxs-lookup"><span data-stu-id="45208-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="45208-113">Использовать ссылочный тип, допускающий значение null, в собственных проектах.</span><span class="sxs-lookup"><span data-stu-id="45208-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="45208-114">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="45208-114">Prerequisites</span></span>

<span data-ttu-id="45208-115">Вам нужно настроить свой компьютер для выполнения .NET Core, включая компилятор C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="45208-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="45208-116">Компилятор C# 8.0 доступен в [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet/3.0).</span><span class="sxs-lookup"><span data-stu-id="45208-116">The C# 8.0 compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet/3.0).</span></span>

<span data-ttu-id="45208-117">В этом руководстве предполагается, что вы знакомы с C# и .NET, включая Visual Studio или .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="45208-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="45208-118">Внедрение в проекты ссылочных типов, допускающих значение null</span><span class="sxs-lookup"><span data-stu-id="45208-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="45208-119">В этом руководстве вы создадите библиотеку, моделирующую выполнение опроса.</span><span class="sxs-lookup"><span data-stu-id="45208-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="45208-120">Код использует оба ссылочных типа (допускающий и не допускающий значение null) для представления реальных понятий.</span><span class="sxs-lookup"><span data-stu-id="45208-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="45208-121">Вопросы в опросе никогда не могут принимать значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-121">The survey questions can never be null.</span></span> <span data-ttu-id="45208-122">Респондент может предпочесть не отвечать на вопрос.</span><span class="sxs-lookup"><span data-stu-id="45208-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="45208-123">В этом случае ответы могут принимать значение `null`.</span><span class="sxs-lookup"><span data-stu-id="45208-123">The responses might be `null` in this case.</span></span>

<span data-ttu-id="45208-124">Код, который вы напишете для этого примера, выражает это намерение, а компилятор применяет его.</span><span class="sxs-lookup"><span data-stu-id="45208-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="45208-125">Создание приложения и включение ссылочных типов, допускающих значение null</span><span class="sxs-lookup"><span data-stu-id="45208-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="45208-126">Создайте новое консольное приложение в Visual Studio или из командной строки с помощью `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="45208-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="45208-127">Присвойте приложению имя `NullableIntroduction`.</span><span class="sxs-lookup"><span data-stu-id="45208-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="45208-128">Создав приложение, вам нужно указать, что весь проект компилируется c включенным **контекстом заметок, допускающим значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="45208-128">Once you've created the application, you'll need to specify that the entire project compiles in an enabled **nullable annotation context**.</span></span> <span data-ttu-id="45208-129">Откройте файл *.csproj* и добавьте элемент `Nullable` в элемент `PropertyGroup`.</span><span class="sxs-lookup"><span data-stu-id="45208-129">Open the *.csproj* file and add a `Nullable` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="45208-130">Задайте для него значение `enable`.</span><span class="sxs-lookup"><span data-stu-id="45208-130">Set its value to `enable`.</span></span> <span data-ttu-id="45208-131">Необходимо выбрать функцию **ссылочных типов, допускающих значение NULL**, даже в проектах C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="45208-131">You must opt into the **nullable reference types** feature, even in C# 8.0 projects.</span></span> <span data-ttu-id="45208-132">Это связано с тем, что когда эта функция будет включена, существующие объявления ссылочных переменных становятся **ссылочными типами, допускающими значение null**.</span><span class="sxs-lookup"><span data-stu-id="45208-132">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="45208-133">Хотя это решение поможет найти проблемы, где существующий код может не иметь правильных проверок нулевых значений, оно может не точно отражать исходное намерение проекта.</span><span class="sxs-lookup"><span data-stu-id="45208-133">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent:</span></span>

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="45208-134">Проектирование типов для приложения</span><span class="sxs-lookup"><span data-stu-id="45208-134">Design the types for the application</span></span>

<span data-ttu-id="45208-135">Для этого приложения опроса требуется создать ряд классов:</span><span class="sxs-lookup"><span data-stu-id="45208-135">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="45208-136">Класс, моделирующий список вопросов.</span><span class="sxs-lookup"><span data-stu-id="45208-136">A class that models the list of questions.</span></span>
- <span data-ttu-id="45208-137">Класс, моделирующий список людей, с которыми связались для опроса.</span><span class="sxs-lookup"><span data-stu-id="45208-137">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="45208-138">Класс, моделирующий ответы человека, принявшего участие в опросе.</span><span class="sxs-lookup"><span data-stu-id="45208-138">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="45208-139">Эти типы будут использовать ссылочные типы, допускающие значения null и не допускающие значения null, чтобы выразить, какие элементы являются обязательными, а какие — необязательными.</span><span class="sxs-lookup"><span data-stu-id="45208-139">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="45208-140">Ссылочные типы, допускающие значение null, четко указывают на это намерение проекта:</span><span class="sxs-lookup"><span data-stu-id="45208-140">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="45208-141">Вопросы, входящие в опрос, не могут иметь значение null: Нет смысла задавать пустой вопрос.</span><span class="sxs-lookup"><span data-stu-id="45208-141">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="45208-142">Респонденты никогда не могут принимать значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-142">The respondents can never be null.</span></span> <span data-ttu-id="45208-143">Следует отслеживать людей, с которыми вы связались, включая респондентов, которые отказались участвовать.</span><span class="sxs-lookup"><span data-stu-id="45208-143">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="45208-144">Любой ответ на вопрос может принимать значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-144">Any response to a question may be null.</span></span> <span data-ttu-id="45208-145">Респонденты могут отказаться отвечать на некоторые или все вопросы.</span><span class="sxs-lookup"><span data-stu-id="45208-145">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="45208-146">Если вы программировали на C#, возможно, вы так привыкли ссылаться на типы, допускающие значение `null`, что упустили другие возможности для объявления экземпляров, не допускающих значение null:</span><span class="sxs-lookup"><span data-stu-id="45208-146">If you've programmed in C#, you may be so accustomed to reference types that allow `null` values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="45208-147">Набор вопросов не должен допускать значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-147">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="45208-148">Набор ответов не должен допускать значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-148">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="45208-149">При написании кода вы увидите, что если ссылочный тип, не допускающий значение null, является типом по умолчанию для ссылок, это позволяет избежать распространенных ошибок, которые могут привести к исключениям из-за пустых ссылок (<xref:System.NullReferenceException>).</span><span class="sxs-lookup"><span data-stu-id="45208-149">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to <xref:System.NullReferenceException>s.</span></span> <span data-ttu-id="45208-150">В этом руководстве описана важность принятия решений о том, какие переменные могут или не могут принимать значение `null`.</span><span class="sxs-lookup"><span data-stu-id="45208-150">One lesson from this tutorial is that you made decisions about which variables could or could not be `null`.</span></span> <span data-ttu-id="45208-151">Язык не предоставлял синтаксис для выражения этих решений,</span><span class="sxs-lookup"><span data-stu-id="45208-151">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="45208-152">а теперь предоставляет.</span><span class="sxs-lookup"><span data-stu-id="45208-152">Now it does.</span></span>

<span data-ttu-id="45208-153">Приложение, которое вы создадите, будет выполнять следующие действия:</span><span class="sxs-lookup"><span data-stu-id="45208-153">The app you'll build does the following steps:</span></span>

1. <span data-ttu-id="45208-154">Создание опроса и добавление в него вопросов.</span><span class="sxs-lookup"><span data-stu-id="45208-154">Creates a survey and adds questions to it.</span></span>
1. <span data-ttu-id="45208-155">Создание псевдослучайного набора респондентов для опроса.</span><span class="sxs-lookup"><span data-stu-id="45208-155">Creates a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="45208-156">Связь с респондентами, пока размер опроса не достигает целевого значения.</span><span class="sxs-lookup"><span data-stu-id="45208-156">Contacts respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="45208-157">Запись важных статистических данных на основе ответов на опрос.</span><span class="sxs-lookup"><span data-stu-id="45208-157">Writes out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="45208-158">Создание опроса с типами, допускающими и не допускающими значение NULL</span><span class="sxs-lookup"><span data-stu-id="45208-158">Build the survey with nullable and non-nullable reference types</span></span>

<span data-ttu-id="45208-159">Первый код, который вы напишете, создает опрос.</span><span class="sxs-lookup"><span data-stu-id="45208-159">The first code you'll write creates the survey.</span></span> <span data-ttu-id="45208-160">Вы напишете классы для моделирования вопроса и выполнения опроса.</span><span class="sxs-lookup"><span data-stu-id="45208-160">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="45208-161">Опрос состоит из вопросов трех типов, различающихся форматом ответов: да или нет, числовые ответы и текстовые ответы.</span><span class="sxs-lookup"><span data-stu-id="45208-161">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="45208-162">Создайте класс `public SurveyQuestion`:</span><span class="sxs-lookup"><span data-stu-id="45208-162">Create a `public SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="45208-163">Компилятор интерпретирует каждое объявление переменной ссылочного типа как ссылочный тип, **не допускающий значение NULL**, для кода во включенном контексте заметок, допускающих значение NULL.</span><span class="sxs-lookup"><span data-stu-id="45208-163">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in an enabled nullable annotation context.</span></span> <span data-ttu-id="45208-164">Первое предупреждение вы увидите после добавления свойств текста и типа вопроса, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="45208-164">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

```csharp
namespace NullableIntroduction
{
    public enum QuestionType
    {
        YesNo,
        Number,
        Text
    }

    public class SurveyQuestion
    {
        public string QuestionText { get; }
        public QuestionType TypeOfQuestion { get; }
    }
}
```

<span data-ttu-id="45208-165">Так как вы еще не инициализировали `QuestionText`, компилятор выдает предупреждение о том, что свойство, не допускающее значение null, не инициализировано.</span><span class="sxs-lookup"><span data-stu-id="45208-165">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="45208-166">Для проекта требуется, чтобы текст вопроса не принимал значение null, поэтому необходимо добавить конструктор, чтобы инициализировать свойство и значение `QuestionType`.</span><span class="sxs-lookup"><span data-stu-id="45208-166">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="45208-167">Законченное определение класса выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="45208-167">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="45208-168">После добавления конструктора предупреждение удаляется.</span><span class="sxs-lookup"><span data-stu-id="45208-168">Adding the constructor removes the warning.</span></span> <span data-ttu-id="45208-169">Аргумент конструктора также является ссылочным типом, не допускающим значение null, поэтому компилятор не выдает никаких предупреждений.</span><span class="sxs-lookup"><span data-stu-id="45208-169">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="45208-170">Затем создайте класс `public` с именем `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="45208-170">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="45208-171">Этот класс содержит список объектов `SurveyQuestion` и методов для добавления вопросов в опрос, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="45208-171">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

```csharp
using System.Collections.Generic;

namespace NullableIntroduction
{
    public class SurveyRun
    {
        private List<SurveyQuestion> surveyQuestions = new List<SurveyQuestion>();

        public void AddQuestion(QuestionType type, string question) =>
            AddQuestion(new SurveyQuestion(type, question));
        public void AddQuestion(SurveyQuestion surveyQuestion) => surveyQuestions.Add(surveyQuestion);
    }
}
```

<span data-ttu-id="45208-172">Как и раньше, необходимо инициализировать объект списка с помощью значения, отличного от null, или компилятор выдаст предупреждение.</span><span class="sxs-lookup"><span data-stu-id="45208-172">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="45208-173">При второй перегрузке `AddQuestion` не будет проверок значений null, так как они не требуются: вы объявили, что переменная не допускает значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-173">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="45208-174">Это значение не может быть равно `null`.</span><span class="sxs-lookup"><span data-stu-id="45208-174">Its value can't be `null`.</span></span>

<span data-ttu-id="45208-175">Переключитесь на *Program.cs* в редакторе и замените содержимое метода `Main` следующими строками кода:</span><span class="sxs-lookup"><span data-stu-id="45208-175">Switch to *Program.cs* in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="45208-176">Так как весь проект находится во включенном контексте заметок, допускающих значение NULL, при каждой передаче значения `null` в любой метод, который ожидает ссылочный тип, не допускающий значение NULL, будет отображаться предупреждение.</span><span class="sxs-lookup"><span data-stu-id="45208-176">Because the entire project is in an enabled nullable annotation context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="45208-177">Попробуйте добавить следующую строку в `Main`:</span><span class="sxs-lookup"><span data-stu-id="45208-177">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="45208-178">Создание респондентов и получение ответов на опрос</span><span class="sxs-lookup"><span data-stu-id="45208-178">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="45208-179">Теперь напишите код, который генерирует ответы на опрос.</span><span class="sxs-lookup"><span data-stu-id="45208-179">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="45208-180">Этот процесс включает в себя несколько мелких задач:</span><span class="sxs-lookup"><span data-stu-id="45208-180">This process involves several small tasks:</span></span>

1. <span data-ttu-id="45208-181">Создать метод, генерирующий объекты-респонденты.</span><span class="sxs-lookup"><span data-stu-id="45208-181">Build a method that generates respondent objects.</span></span> <span data-ttu-id="45208-182">Они представляют людей, которых просят пройти опрос.</span><span class="sxs-lookup"><span data-stu-id="45208-182">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="45208-183">Создать логику, чтобы имитировать процесс задания вопросов респонденту и собирать ответы или отмечать, что респондент не ответил.</span><span class="sxs-lookup"><span data-stu-id="45208-183">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="45208-184">Повторять опрос до тех пор, пока нужное количество респондентов не ответит на вопросы.</span><span class="sxs-lookup"><span data-stu-id="45208-184">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="45208-185">Вам понадобится класс для представления ответа на опрос, поэтому добавьте его сейчас.</span><span class="sxs-lookup"><span data-stu-id="45208-185">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="45208-186">Включите поддержку значений null.</span><span class="sxs-lookup"><span data-stu-id="45208-186">Enable nullable support.</span></span> <span data-ttu-id="45208-187">Добавьте свойство `Id` и конструктор, который его инициализирует, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="45208-187">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyResponse
    {
        public int Id { get; }

        public SurveyResponse(int id) => Id = id;
    }
}
```

<span data-ttu-id="45208-188">Затем добавьте метод `static` для создания новых участников путем генерации случайного идентификатора:</span><span class="sxs-lookup"><span data-stu-id="45208-188">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="45208-189">Основная задача этого класса состоит в том, чтобы генерировать ответы участников на вопросы в опросе.</span><span class="sxs-lookup"><span data-stu-id="45208-189">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="45208-190">Эта задача состоит из нескольких шагов:</span><span class="sxs-lookup"><span data-stu-id="45208-190">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="45208-191">Запросите участие в опросе.</span><span class="sxs-lookup"><span data-stu-id="45208-191">Ask for participation in the survey.</span></span> <span data-ttu-id="45208-192">Если пользователь не согласен, верните отсутствующий (или null) ответ.</span><span class="sxs-lookup"><span data-stu-id="45208-192">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="45208-193">Задайте каждый вопрос и запишите ответы.</span><span class="sxs-lookup"><span data-stu-id="45208-193">Ask each question and record the answer.</span></span> <span data-ttu-id="45208-194">Любой ответ может отсутствовать (или иметь значение null).</span><span class="sxs-lookup"><span data-stu-id="45208-194">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="45208-195">Добавьте приведенный ниже код к классу `SurveyResponse`:</span><span class="sxs-lookup"><span data-stu-id="45208-195">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="45208-196">Хранилищем для ответов на опрос является `Dictionary<int, string>?`, из которого видно, что оно может принимать значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-196">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="45208-197">Используйте новую языковую функцию, чтобы объявить намерение проекта как компилятору, так и всем, кто будет работать с кодом позже.</span><span class="sxs-lookup"><span data-stu-id="45208-197">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="45208-198">Если вы когда-нибудь разыменуете `surveyResponses`, не проверив значения `null`, компилятор отобразит предупреждение.</span><span class="sxs-lookup"><span data-stu-id="45208-198">If you ever dereference `surveyResponses` without checking for the `null` value first, you'll get a compiler warning.</span></span> <span data-ttu-id="45208-199">В методе `AnswerSurvey` предупреждение не отображается, так как компилятор может определить, что переменной `surveyResponses` ранее было присвоено значение, отличное от null.</span><span class="sxs-lookup"><span data-stu-id="45208-199">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="45208-200">Использование значения `null` для отсутствующих ответов указывает на важную особенность при работе с допускающими значение NULL ссылочными типами: перед вами не стоит цель удалить все значения `null` из программы.</span><span class="sxs-lookup"><span data-stu-id="45208-200">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="45208-201">Скорее, вам нужно привести написанный вами код в соответствие со своим замыслом.</span><span class="sxs-lookup"><span data-stu-id="45208-201">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="45208-202">Отсутствующие значения — это неотъемлемая часть кода.</span><span class="sxs-lookup"><span data-stu-id="45208-202">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="45208-203">И значение `null` хорошо подходит для их выражения.</span><span class="sxs-lookup"><span data-stu-id="45208-203">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="45208-204">Если вы попытаетесь удалить все значения `null`, вам придется определить другой способ, чтобы выразить такие отсутствующие значения без использования `null`.</span><span class="sxs-lookup"><span data-stu-id="45208-204">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="45208-205">Далее необходимо написать метод `PerformSurvey` в классе `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="45208-205">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="45208-206">Добавьте в класс `SurveyRun` следующий код:</span><span class="sxs-lookup"><span data-stu-id="45208-206">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="45208-207">В этом случае выбор `List<SurveyResponse>?` с возможностью принимать значение null указывает на то, что ответ может отсутствовать.</span><span class="sxs-lookup"><span data-stu-id="45208-207">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="45208-208">Это значит, что респонденты еще не участвовали в опросе.</span><span class="sxs-lookup"><span data-stu-id="45208-208">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="45208-209">Обратите внимание, что респонденты добавляются до тех пор, пока не будет достигнуто целевое значение.</span><span class="sxs-lookup"><span data-stu-id="45208-209">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="45208-210">Для запуска опроса осталось добавить вызов в конце метода `Main`:</span><span class="sxs-lookup"><span data-stu-id="45208-210">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="45208-211">Анализ ответов на опросы</span><span class="sxs-lookup"><span data-stu-id="45208-211">Examine survey responses</span></span>

<span data-ttu-id="45208-212">Далее следует отобразить ответы на опрос.</span><span class="sxs-lookup"><span data-stu-id="45208-212">The last step is to display survey results.</span></span> <span data-ttu-id="45208-213">Добавьте код во многие из написанных вами классов.</span><span class="sxs-lookup"><span data-stu-id="45208-213">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="45208-214">Этот код демонстрирует различие ссылочных типов, допускающих и не допускающих значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-214">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="45208-215">Начните с добавления элементов, воплощающих выражение, в класс `SurveyResponse`:</span><span class="sxs-lookup"><span data-stu-id="45208-215">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="45208-216">Так как `surveyResponses` является ссылочным типом, допускающим значение null, прежде чем отменять ссылку на него, укажите, что проверка требуется.</span><span class="sxs-lookup"><span data-stu-id="45208-216">Because `surveyResponses` is a nullable reference type, null checks are necessary before de-referencing it.</span></span> <span data-ttu-id="45208-217">Метод `Answer` возвращает строку, не допускающую значения null, поэтому мы должны охватить вариант отсутствующего ответа, используя оператор объединения со значением null.</span><span class="sxs-lookup"><span data-stu-id="45208-217">The `Answer` method returns a non-nullable string, so we have to cover the case of a missing answer by using the null-coalescing operator.</span></span>

<span data-ttu-id="45208-218">Затем добавьте эти три элемента, воплощающие выражение, в класс `SurveyRun`:</span><span class="sxs-lookup"><span data-stu-id="45208-218">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="45208-219">Элемент `AllParticipants` должен принимать во внимание, что переменная `respondents` может иметь значение null, но возвращаемое значение не может быть равно null.</span><span class="sxs-lookup"><span data-stu-id="45208-219">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="45208-220">Если изменить это выражение, удалив `??` и следующую пустую последовательность, компилятор выдаст предупреждение о том, что метод может возвращать `null`, а его сигнатура возвращает тип, не допускающий значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-220">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="45208-221">Наконец, добавьте следующий цикл в нижней части метода `Main`:</span><span class="sxs-lookup"><span data-stu-id="45208-221">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="45208-222">В этом коде не требуется никаких проверок `null`, так как вы разработали базовые интерфейсы так, чтобы они возвращали ссылочные типы, не допускающие значения null.</span><span class="sxs-lookup"><span data-stu-id="45208-222">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="45208-223">Получите код</span><span class="sxs-lookup"><span data-stu-id="45208-223">Get the code</span></span>

<span data-ttu-id="45208-224">Вы можете получить код этого руководства из нашего репозитория [samples](https://github.com/dotnet/samples) в папке [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/main/csharp/NullableIntroduction).</span><span class="sxs-lookup"><span data-stu-id="45208-224">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/main/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="45208-225">Экспериментируйте, изменяя объявления типов между ссылочными типами, допускающими и не допускающими значение null.</span><span class="sxs-lookup"><span data-stu-id="45208-225">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="45208-226">Посмотрите, как создаются различные предупреждения, чтобы избежать случайного разыменования `null`.</span><span class="sxs-lookup"><span data-stu-id="45208-226">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="45208-227">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="45208-227">Next steps</span></span>

<span data-ttu-id="45208-228">Дополнительные сведения о переводе существующего приложения на использование допускающих значение NULL ссылочных типов:</span><span class="sxs-lookup"><span data-stu-id="45208-228">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="45208-229">Перевод приложения на использование ссылочных типов, допускающих значение NULL</span><span class="sxs-lookup"><span data-stu-id="45208-229">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)

<span data-ttu-id="45208-230">Узнайте, как использовать ссылочный тип, допускающий значение NULL, при использовании Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="45208-230">Learn how to use nullable reference type when using Entity Framework:</span></span>
> [<span data-ttu-id="45208-231">Основы Entity Framework Core. Работа со ссылочными типами, допускающими значение NULL</span><span class="sxs-lookup"><span data-stu-id="45208-231">Entity Framework Core Fundamentals: Working with Nullable Reference Types</span></span>](/ef/core/miscellaneous/nullable-reference-types)
