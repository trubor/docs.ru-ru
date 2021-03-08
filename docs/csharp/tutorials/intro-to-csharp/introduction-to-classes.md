---
title: Классы и объекты. Вводное руководство по C#.
description: Создайте свою первую программу на C# и ознакомьтесь с основными понятиями объектно-ориентированного программирования
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 3da445e6c656628fffdb9ef9384fb1a1c556a2cd
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255422"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="440dd-103">Сведения об использовании классов и объектов в объектно-ориентированном программировании</span><span class="sxs-lookup"><span data-stu-id="440dd-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="440dd-104">В этом руководстве показано, как создать консольное приложение, и приведены основные объектно-ориентированные функции языка C#.</span><span class="sxs-lookup"><span data-stu-id="440dd-104">In this tutorial, you'll build a console application and see the basic object-oriented features that are part of the C# language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="440dd-105">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="440dd-105">Prerequisites</span></span>

<span data-ttu-id="440dd-106">Для работы с руководством вам потребуется компьютер, настроенный для разработки в локальной среде.</span><span class="sxs-lookup"><span data-stu-id="440dd-106">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="440dd-107">В Windows, Linux или macOS для создания, сборки и запуска приложений можно использовать .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="440dd-107">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="440dd-108">В Windows можно использовать Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="440dd-108">On Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="440dd-109">Инструкции по настройке см. в статье [Настройка локальной среды](../../tour-of-csharp/tutorials/local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="440dd-109">For setup instructions, see [Set up your local environment](../../tour-of-csharp/tutorials/local-environment.md).</span></span>

## <a name="create-your-application"></a><span data-ttu-id="440dd-110">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="440dd-110">Create your application</span></span>

<span data-ttu-id="440dd-111">С помощью окна терминала создайте каталог с именем *classes*.</span><span class="sxs-lookup"><span data-stu-id="440dd-111">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="440dd-112">В этом каталоге вы создадите приложение.</span><span class="sxs-lookup"><span data-stu-id="440dd-112">You'll build your application there.</span></span> <span data-ttu-id="440dd-113">Откройте этот каталог и введите в окне консоли `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="440dd-113">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="440dd-114">При помощи этой команды создается приложение.</span><span class="sxs-lookup"><span data-stu-id="440dd-114">This command creates your application.</span></span> <span data-ttu-id="440dd-115">Откройте файл *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="440dd-115">Open *Program.cs*.</span></span> <span data-ttu-id="440dd-116">Он должен выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="440dd-116">It should look like this:</span></span>

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="440dd-117">При работе с этим руководством вы создадите новые типы, представляющие банковский счет.</span><span class="sxs-lookup"><span data-stu-id="440dd-117">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="440dd-118">Обычно разработчики определяют каждый класс в отдельном текстовом файле.</span><span class="sxs-lookup"><span data-stu-id="440dd-118">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="440dd-119">Благодаря этому программой легче управлять, когда ее размер увеличивается.</span><span class="sxs-lookup"><span data-stu-id="440dd-119">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="440dd-120">Создайте новый файл с именем *BankAccount.cs* в каталоге *classes*.</span><span class="sxs-lookup"><span data-stu-id="440dd-120">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="440dd-121">Этот файл будет содержать определение \***банковского счета** _.</span><span class="sxs-lookup"><span data-stu-id="440dd-121">This file will contain the definition of a \***bank account** _.</span></span> <span data-ttu-id="440dd-122">Средства объектно-ориентированного программирования обеспечивают упорядочение кода. При этом создаются типы в виде _\*_классов_\*\*.</span><span class="sxs-lookup"><span data-stu-id="440dd-122">Object Oriented programming organizes code by creating types in the form of _\*_classes_\*\*.</span></span> <span data-ttu-id="440dd-123">Классы содержат код, который представляет отдельную сущность.</span><span class="sxs-lookup"><span data-stu-id="440dd-123">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="440dd-124">Класс `BankAccount` представляет банковский счет.</span><span class="sxs-lookup"><span data-stu-id="440dd-124">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="440dd-125">Этот код реализует определенные операции с помощью методов и свойств.</span><span class="sxs-lookup"><span data-stu-id="440dd-125">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="440dd-126">Созданный в этом кратком руководстве банковский счет поддерживает следующий алгоритм работы:</span><span class="sxs-lookup"><span data-stu-id="440dd-126">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="440dd-127">Представляет собой число из 10 цифр, которое однозначно определяет банковский счет.</span><span class="sxs-lookup"><span data-stu-id="440dd-127">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="440dd-128">Содержит строку, в которой хранятся имена владельцев.</span><span class="sxs-lookup"><span data-stu-id="440dd-128">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="440dd-129">Позволяет получить данные сальдо.</span><span class="sxs-lookup"><span data-stu-id="440dd-129">The balance can be retrieved.</span></span>
1. <span data-ttu-id="440dd-130">Принимает депозиты.</span><span class="sxs-lookup"><span data-stu-id="440dd-130">It accepts deposits.</span></span>
1. <span data-ttu-id="440dd-131">Принимает списания.</span><span class="sxs-lookup"><span data-stu-id="440dd-131">It accepts withdrawals.</span></span>
1. <span data-ttu-id="440dd-132">Начальное сальдо должно было положительным.</span><span class="sxs-lookup"><span data-stu-id="440dd-132">The initial balance must be positive.</span></span>
1. <span data-ttu-id="440dd-133">После списания не должно оставаться отрицательное сальдо.</span><span class="sxs-lookup"><span data-stu-id="440dd-133">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="440dd-134">Определение типа банковского счета</span><span class="sxs-lookup"><span data-stu-id="440dd-134">Define the bank account type</span></span>

<span data-ttu-id="440dd-135">Сначала можно создать основы класса, который определяет такой режим работы.</span><span class="sxs-lookup"><span data-stu-id="440dd-135">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="440dd-136">Создайте новый файл с помощью команды **File:New**.</span><span class="sxs-lookup"><span data-stu-id="440dd-136">Create a new file using the **File:New** command.</span></span> <span data-ttu-id="440dd-137">Присвойте ему имя *BankAccount.cs*.</span><span class="sxs-lookup"><span data-stu-id="440dd-137">Name it *BankAccount.cs*.</span></span> <span data-ttu-id="440dd-138">Добавьте в файл *BankAccount.cs* следующий код:</span><span class="sxs-lookup"><span data-stu-id="440dd-138">Add the following code to your *BankAccount.cs* file:</span></span>

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

<span data-ttu-id="440dd-139">Прежде чем продолжить, рассмотрим созданный код.</span><span class="sxs-lookup"><span data-stu-id="440dd-139">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="440dd-140">Объявление `namespace` предоставляет способ логического упорядочения кода.</span><span class="sxs-lookup"><span data-stu-id="440dd-140">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="440dd-141">Это относительно небольшое руководство, поэтому весь код размещается в одном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="440dd-141">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="440dd-142">`public class BankAccount` определяет класс или тип, который вы создаете.</span><span class="sxs-lookup"><span data-stu-id="440dd-142">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="440dd-143">Весь код в скобках `{` и `}`, который следует за объявлением класса, определяет состояние и поведение класса.</span><span class="sxs-lookup"><span data-stu-id="440dd-143">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="440dd-144">Есть пять \***элементов** _ класса `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="440dd-144">There are five \***members** _ of the `BankAccount` class.</span></span> <span data-ttu-id="440dd-145">Первые три элемента представляют собой _\*_свойства_\*_.</span><span class="sxs-lookup"><span data-stu-id="440dd-145">The first three are _*_properties_*_.</span></span> <span data-ttu-id="440dd-146">Свойства являются элементами данных и могут содержать код для запуска проверки или других правил.</span><span class="sxs-lookup"><span data-stu-id="440dd-146">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="440dd-147">Последние два элемента являются _\*_методами_\*\*.</span><span class="sxs-lookup"><span data-stu-id="440dd-147">The last two are _\*_methods_\*\*.</span></span> <span data-ttu-id="440dd-148">Методы представляют собой блоки кода, которые выполняют только одну функцию.</span><span class="sxs-lookup"><span data-stu-id="440dd-148">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="440dd-149">Имя каждого элемента должно содержать достаточно информации, чтобы разработчик мог понять, какие функции выполняет класс.</span><span class="sxs-lookup"><span data-stu-id="440dd-149">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="440dd-150">Открытие нового счета</span><span class="sxs-lookup"><span data-stu-id="440dd-150">Open a new account</span></span>

<span data-ttu-id="440dd-151">Сначала нужно открыть банковский счет.</span><span class="sxs-lookup"><span data-stu-id="440dd-151">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="440dd-152">Когда клиент открывает счет, он должен указать начальное сальдо и сведения о владельцах этого счета.</span><span class="sxs-lookup"><span data-stu-id="440dd-152">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="440dd-153">Создайте новый объект типа `BankAccount`, чтобы определить \***конструктор** _, который назначает эти значения.</span><span class="sxs-lookup"><span data-stu-id="440dd-153">Creating a new object of the `BankAccount` type means defining a \***constructor** _ that assigns those values.</span></span> <span data-ttu-id="440dd-154">_ \*_Конструктор_\*\* — это элемент, имя которого совпадает с классом.</span><span class="sxs-lookup"><span data-stu-id="440dd-154">A _ *_constructor_*\* is a member that has the same name as the class.</span></span> <span data-ttu-id="440dd-155">Он используется для инициализации объектов этого типа класса.</span><span class="sxs-lookup"><span data-stu-id="440dd-155">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="440dd-156">Добавьте указанный ниже конструктор в тип `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="440dd-156">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="440dd-157">Добавьте следующий код непосредственно перед объявлением `MakeDeposit`:</span><span class="sxs-lookup"><span data-stu-id="440dd-157">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="440dd-158">Конструкторы вызываются при создании объекта с помощью [`new`](../../language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="440dd-158">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="440dd-159">Замените строку `Console.WriteLine("Hello World!");` в файле *Program.cs* следующим кодом (замените `<name>` своим именем):</span><span class="sxs-lookup"><span data-stu-id="440dd-159">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="440dd-160">Давайте выполним то, что уже создано.</span><span class="sxs-lookup"><span data-stu-id="440dd-160">Let's run what you've built so far.</span></span> <span data-ttu-id="440dd-161">Если вы работаете в Visual Studio, выберите **Запуск без отладки** из меню **Выполнить**.</span><span class="sxs-lookup"><span data-stu-id="440dd-161">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="440dd-162">Если вы используете командную строку, введите `dotnet run` в том каталоге, где создали проект.</span><span class="sxs-lookup"><span data-stu-id="440dd-162">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="440dd-163">Вы заметили, что номер счета не указан?</span><span class="sxs-lookup"><span data-stu-id="440dd-163">Did you notice that the account number is blank?</span></span> <span data-ttu-id="440dd-164">Нужно решить эту проблему.</span><span class="sxs-lookup"><span data-stu-id="440dd-164">It's time to fix that.</span></span> <span data-ttu-id="440dd-165">Номер счета следует назначить при создании объекта.</span><span class="sxs-lookup"><span data-stu-id="440dd-165">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="440dd-166">Но создавать этот номер не входит в обязанности вызывающего.</span><span class="sxs-lookup"><span data-stu-id="440dd-166">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="440dd-167">Код класса `BankAccount` должен иметь информацию о том, как присвоить номера новым счетам.</span><span class="sxs-lookup"><span data-stu-id="440dd-167">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="440dd-168">Проще всего начать с 10-значного числа.</span><span class="sxs-lookup"><span data-stu-id="440dd-168">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="440dd-169">Увеличивайте его при создании каждого нового счета.</span><span class="sxs-lookup"><span data-stu-id="440dd-169">Increment it when each new account is created.</span></span> <span data-ttu-id="440dd-170">Затем при создании объекта сохраните номер текущего счета.</span><span class="sxs-lookup"><span data-stu-id="440dd-170">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="440dd-171">Добавьте в класс `BankAccount` объявление члена.</span><span class="sxs-lookup"><span data-stu-id="440dd-171">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="440dd-172">Поместите следующую строку кода после открывающей скобки `{` в начале класса `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="440dd-172">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="440dd-173">Это элемент данных.</span><span class="sxs-lookup"><span data-stu-id="440dd-173">This is a data member.</span></span> <span data-ttu-id="440dd-174">Он имеет свойство `private`, то есть к нему может получить доступ только код внутри класса `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="440dd-174">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="440dd-175">Таким образом общедоступные обязательства (например, получение номера счета) отделяются от закрытой реализации (способ создания номеров счетов).</span><span class="sxs-lookup"><span data-stu-id="440dd-175">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="440dd-176">Также он является `static`, то есть совместно используется всеми объектами `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="440dd-176">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="440dd-177">Значение нестатической переменной является уникальным для каждого экземпляра объекта `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="440dd-177">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="440dd-178">Добавьте две приведенные ниже строки в конструктор, чтобы назначить номер счета.</span><span class="sxs-lookup"><span data-stu-id="440dd-178">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="440dd-179">Они должны располагаться за строкой с текстом `this.Balance = initialBalance`.</span><span class="sxs-lookup"><span data-stu-id="440dd-179">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="440dd-180">Введите `dotnet run`, чтобы просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="440dd-180">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="440dd-181">Создание депозитов и списаний</span><span class="sxs-lookup"><span data-stu-id="440dd-181">Create deposits and withdrawals</span></span>

<span data-ttu-id="440dd-182">Для надлежащей работы ваш класс банковского счета должен принимать депозиты и списания.</span><span class="sxs-lookup"><span data-stu-id="440dd-182">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="440dd-183">Чтобы реализовать депозиты и списания, создадим журнал для каждой транзакции на счете.</span><span class="sxs-lookup"><span data-stu-id="440dd-183">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="440dd-184">Этот подход предпочтительнее, чем простое обновление сальдо после каждой транзакции.</span><span class="sxs-lookup"><span data-stu-id="440dd-184">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="440dd-185">Журнал можно использовать для аудита всех транзакций и управления ежедневным сальдо.</span><span class="sxs-lookup"><span data-stu-id="440dd-185">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="440dd-186">При необходимости можно вычислять сальдо с помощью журнала всех транзакций. Тогда при следующем вычислении все исправленные ошибки в одной транзакции будут правильно учтены в сальдо.</span><span class="sxs-lookup"><span data-stu-id="440dd-186">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="440dd-187">Начнем с создания нового типа, который представляет транзакцию.</span><span class="sxs-lookup"><span data-stu-id="440dd-187">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="440dd-188">Это простой тип без обязательств.</span><span class="sxs-lookup"><span data-stu-id="440dd-188">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="440dd-189">Ему нужно назначить несколько свойств.</span><span class="sxs-lookup"><span data-stu-id="440dd-189">It needs a few properties.</span></span> <span data-ttu-id="440dd-190">Создайте новый файл с именем *Transaction.cs*.</span><span class="sxs-lookup"><span data-stu-id="440dd-190">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="440dd-191">Добавьте в этот файл следующий код:</span><span class="sxs-lookup"><span data-stu-id="440dd-191">Add the following code to it:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

<span data-ttu-id="440dd-192">Теперь добавим <xref:System.Collections.Generic.List%601> объектов `Transaction` в класс `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="440dd-192">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="440dd-193">Добавьте следующее объявление после конструктора в файл *BankAccount.cs*:</span><span class="sxs-lookup"><span data-stu-id="440dd-193">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<span data-ttu-id="440dd-194">Класс <xref:System.Collections.Generic.List%601> требует импортировать другое пространство имен.</span><span class="sxs-lookup"><span data-stu-id="440dd-194">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="440dd-195">Добавьте следующий код в начало файла *BankAccount.cs*:</span><span class="sxs-lookup"><span data-stu-id="440dd-195">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="440dd-196">Далее мы соответствующим образом вычислим `Balance`.</span><span class="sxs-lookup"><span data-stu-id="440dd-196">Now, let's correctly compute the `Balance`.</span></span> <span data-ttu-id="440dd-197">Чтобы вычислить текущий баланс, нужно суммировать значения всех транзакций.</span><span class="sxs-lookup"><span data-stu-id="440dd-197">The current balance can be found by summing the values of all transactions.</span></span> <span data-ttu-id="440dd-198">В этом виде этот код позволяет получить только начальный баланс счета, поэтому необходимо обновить свойство `Balance`.</span><span class="sxs-lookup"><span data-stu-id="440dd-198">As the code is currently, you can only get the initial balance of the account, so you'll have to update the `Balance` property.</span></span> <span data-ttu-id="440dd-199">В файле *BankAccount.cs* замените строку `public decimal Balance { get; }` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="440dd-199">Replace the line `public decimal Balance { get; }` in *BankAccount.cs* with the following code:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

<span data-ttu-id="440dd-200">В этом примере показан важный аспект ***свойств***.</span><span class="sxs-lookup"><span data-stu-id="440dd-200">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="440dd-201">Вы вычисляете сальдо, когда другой программист запрашивает значение.</span><span class="sxs-lookup"><span data-stu-id="440dd-201">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="440dd-202">В результате вашего вычисления выводится список всех транзакций и сумма в виде текущего сальдо.</span><span class="sxs-lookup"><span data-stu-id="440dd-202">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="440dd-203">Теперь реализуйте методы `MakeDeposit` и `MakeWithdrawal`.</span><span class="sxs-lookup"><span data-stu-id="440dd-203">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="440dd-204">Эти методы будут выполнять два последних правила: начальное сальдо должно быть положительным, списание не должно создавать отрицательное сальдо.</span><span class="sxs-lookup"><span data-stu-id="440dd-204">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="440dd-205">Это действие вводит понятие ***исключений***.</span><span class="sxs-lookup"><span data-stu-id="440dd-205">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="440dd-206">Чтобы определить, что метод не может выполнить свою функцию, обычно вызывается исключение.</span><span class="sxs-lookup"><span data-stu-id="440dd-206">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="440dd-207">В типе исключения и связанном с ним сообщении описывается ошибка.</span><span class="sxs-lookup"><span data-stu-id="440dd-207">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="440dd-208">В этом примере метод `MakeDeposit` вызывает исключение, если сумма депозита является отрицательной.</span><span class="sxs-lookup"><span data-stu-id="440dd-208">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="440dd-209">Метод `MakeWithdrawal` вызывает исключение, если сумма списания является отрицательной или если при списании создается отрицательное сальдо.</span><span class="sxs-lookup"><span data-stu-id="440dd-209">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="440dd-210">Добавьте следующий код после объявления списка `allTransactions`:</span><span class="sxs-lookup"><span data-stu-id="440dd-210">Add the following code after the declaration of the `allTransactions` list:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

<span data-ttu-id="440dd-211">Инструкция [`throw`](../../language-reference/keywords/throw.md)**вызывает** исключение.</span><span class="sxs-lookup"><span data-stu-id="440dd-211">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="440dd-212">Выполнение текущего блока завершается и управление передается в первый подходящий блок `catch` из стека вызовов.</span><span class="sxs-lookup"><span data-stu-id="440dd-212">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="440dd-213">Вы добавите блок `catch` для тестирования этого кода немного позже.</span><span class="sxs-lookup"><span data-stu-id="440dd-213">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="440dd-214">Чтобы вместо непосредственного обновления сальдо добавлялась начальная транзакция, конструктор должен получить одно изменение.</span><span class="sxs-lookup"><span data-stu-id="440dd-214">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="440dd-215">Так как вы уже написали метод `MakeDeposit`, вызовите его из конструктора.</span><span class="sxs-lookup"><span data-stu-id="440dd-215">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="440dd-216">Готовый конструктор должен выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="440dd-216">The finished constructor should look like this:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<span data-ttu-id="440dd-217"><xref:System.DateTime.Now?displayProperty=nameWithType> — это свойство, которое возвращает текущие дату и время.</span><span class="sxs-lookup"><span data-stu-id="440dd-217"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="440dd-218">Проверьте его. Для этого добавьте несколько депозитов и списаний в метод `Main` после кода, с помощью которого создается `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="440dd-218">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="440dd-219">Теперь убедитесь, что условия возникновения ошибки срабатывают правильно, создав счет с отрицательным сальдо.</span><span class="sxs-lookup"><span data-stu-id="440dd-219">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="440dd-220">Добавьте следующий код после только что добавленного блока кода:</span><span class="sxs-lookup"><span data-stu-id="440dd-220">Add the following code after the preceding code you just added:</span></span>

```csharp
// Test that the initial balances must be positive.
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="440dd-221">С помощью [инструкций `try` и `catch`](../../language-reference/keywords/try-catch.md) пометьте блок кода, который может вызывать исключения, и перехватывайте ожидаемые сообщения об ошибках.</span><span class="sxs-lookup"><span data-stu-id="440dd-221">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="440dd-222">Так же можно проверять код, который вызывает исключение при получении отрицательного баланса.</span><span class="sxs-lookup"><span data-stu-id="440dd-222">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="440dd-223">Добавьте следующий код в конец метода `Main`:</span><span class="sxs-lookup"><span data-stu-id="440dd-223">Add the following code at the end of your `Main` method:</span></span>

```csharp
// Test for a negative balance.
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="440dd-224">Сохраните файл и введите `dotnet run` для проверки.</span><span class="sxs-lookup"><span data-stu-id="440dd-224">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="440dd-225">Задача — регистрация всех транзакций</span><span class="sxs-lookup"><span data-stu-id="440dd-225">Challenge - log all transactions</span></span>

<span data-ttu-id="440dd-226">В завершение вы создадите метод `GetAccountHistory`, который создает `string` для журнала транзакций.</span><span class="sxs-lookup"><span data-stu-id="440dd-226">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="440dd-227">Добавьте этот метод в тип `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="440dd-227">Add this method to the `BankAccount` type:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

<span data-ttu-id="440dd-228">В этом примере используется класс <xref:System.Text.StringBuilder>, чтобы отформатировать строку, которая содержит одну строку для каждой транзакции.</span><span class="sxs-lookup"><span data-stu-id="440dd-228">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="440dd-229">Код форматирования строки вы уже видели в этой серии руководств.</span><span class="sxs-lookup"><span data-stu-id="440dd-229">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="440dd-230">В этом коде есть новый символ `\t`.</span><span class="sxs-lookup"><span data-stu-id="440dd-230">One new character is `\t`.</span></span> <span data-ttu-id="440dd-231">Он позволяет вставить вкладку для форматирования выходных данных.</span><span class="sxs-lookup"><span data-stu-id="440dd-231">That inserts a tab to format the output.</span></span>

<span data-ttu-id="440dd-232">Добавьте следующую строку, чтобы проверить его в файле *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="440dd-232">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="440dd-233">Снова выполните программу, чтобы просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="440dd-233">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="440dd-234">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="440dd-234">Next steps</span></span>

<span data-ttu-id="440dd-235">Если у вас возникли проблемы, изучите исходный код для этого руководства, размещенный [в репозитории GitHub](https://github.com/dotnet/docs/tree/main/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes).</span><span class="sxs-lookup"><span data-stu-id="440dd-235">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/main/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes).</span></span>

<span data-ttu-id="440dd-236">Вы можете продолжить, перейдя к учебнику по [объектно-ориентированному программированию](object-oriented-programming.md).</span><span class="sxs-lookup"><span data-stu-id="440dd-236">You can continue with the [object oriented programming](object-oriented-programming.md) tutorial.</span></span>

<span data-ttu-id="440dd-237">Дополнительные сведения об этих понятиях см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="440dd-237">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="440dd-238">if-else (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="440dd-238">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="440dd-239">while (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="440dd-239">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="440dd-240">do (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="440dd-240">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="440dd-241">for (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="440dd-241">For statement</span></span>](../../language-reference/keywords/for.md)
