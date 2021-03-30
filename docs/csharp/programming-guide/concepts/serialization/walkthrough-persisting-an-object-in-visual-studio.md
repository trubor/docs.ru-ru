---
title: Пошаговое руководство. Сохранение объекта с помощью C#
description: В этом примере создается базовый объект Loan в C#, а его данные сохраняются в файле, после чего создается новый объект с данными из файла.
ms.date: 04/26/2018
ms.openlocfilehash: 0fc733982b7800653a3c8c283bd0af8384d72168
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876452"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="0a18a-103">Пошаговое руководство. Сохранение объекта с помощью C\#</span><span class="sxs-lookup"><span data-stu-id="0a18a-103">Walkthrough: persisting an object using C\#</span></span>

<span data-ttu-id="0a18a-104">С помощью сериализации можно сохранить данные объекта между экземплярами, что позволит сохранять значения и извлекать их при следующем создании экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="0a18a-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="0a18a-105">В этом пошаговом руководстве будет создан базовый объект `Loan`, а его данные сохранены в файл.</span><span class="sxs-lookup"><span data-stu-id="0a18a-105">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="0a18a-106">Затем при повторном создании объекта вы получите данные из файла.</span><span class="sxs-lookup"><span data-stu-id="0a18a-106">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a18a-107">В этом примере создается файл (если файл отсутствует).</span><span class="sxs-lookup"><span data-stu-id="0a18a-107">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="0a18a-108">Если приложение должно создать файл, ему необходимо разрешение `Create` для папки.</span><span class="sxs-lookup"><span data-stu-id="0a18a-108">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="0a18a-109">Для задания разрешений используются списки управления доступом.</span><span class="sxs-lookup"><span data-stu-id="0a18a-109">Permissions are set by using access control lists.</span></span> <span data-ttu-id="0a18a-110">Если файл уже существует, приложению требуется лишь разрешение `Write` (с более низким уровнем).</span><span class="sxs-lookup"><span data-stu-id="0a18a-110">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="0a18a-111">Если возможно, безопаснее создать файл во время развертывания и предоставить только разрешения `Read` для одного файла (вместо разрешения Create для папки).</span><span class="sxs-lookup"><span data-stu-id="0a18a-111">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="0a18a-112">По тем же соображениям рекомендуется записывать данные в пользовательские папки, а не в корневую папку или папку Program Files.</span><span class="sxs-lookup"><span data-stu-id="0a18a-112">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a18a-113">В этом примере данные сохраняются в двоичном формате.</span><span class="sxs-lookup"><span data-stu-id="0a18a-113">This example stores data in a binary format file.</span></span> <span data-ttu-id="0a18a-114">Эти форматы не следует использовать для конфиденциальных данных, таких как пароли или сведения о кредитных картах.</span><span class="sxs-lookup"><span data-stu-id="0a18a-114">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0a18a-115">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="0a18a-115">Prerequisites</span></span>

- <span data-ttu-id="0a18a-116">Для сборки и запуска установите [пакет SDK для .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="0a18a-116">To build and run, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

- <span data-ttu-id="0a18a-117">Установите любой привычный для вас редактор кода, если еще не сделали этого.</span><span class="sxs-lookup"><span data-stu-id="0a18a-117">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="0a18a-118">Нужно ли устанавливать редактор кода?</span><span class="sxs-lookup"><span data-stu-id="0a18a-118">Need to install a code editor?</span></span> <span data-ttu-id="0a18a-119">Попробуйте использовать [Visual Studio](https://visualstudio.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="0a18a-119">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

- <span data-ttu-id="0a18a-120">Этот пример требует C# версии 7.3.</span><span class="sxs-lookup"><span data-stu-id="0a18a-120">The example requires C# 7.3.</span></span> <span data-ttu-id="0a18a-121">См. [сведения о выборе версии языка C#](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="0a18a-121">See [Select the C# language version](../../../language-reference/configure-language-version.md)</span></span>

<span data-ttu-id="0a18a-122">Можно просмотреть образец кода онлайн [в репозитории GitHub с примерами .NET](https://github.com/dotnet/samples/tree/main/csharp/serialization).</span><span class="sxs-lookup"><span data-stu-id="0a18a-122">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/main/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="0a18a-123">Создание объекта Loan</span><span class="sxs-lookup"><span data-stu-id="0a18a-123">Creating the loan object</span></span>

<span data-ttu-id="0a18a-124">Первым шагом является создание класса `Loan` и консольного приложения, которое использует этот класс:</span><span class="sxs-lookup"><span data-stu-id="0a18a-124">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="0a18a-125">Создание нового приложения.</span><span class="sxs-lookup"><span data-stu-id="0a18a-125">Create a new application.</span></span> <span data-ttu-id="0a18a-126">Введите `dotnet new console -o serialization` для создания нового консольного приложения в подкаталоге `serialization`.</span><span class="sxs-lookup"><span data-stu-id="0a18a-126">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="0a18a-127">Откройте приложение в редакторе и добавьте новый класс с именем `Loan.cs`.</span><span class="sxs-lookup"><span data-stu-id="0a18a-127">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="0a18a-128">Добавьте приведенный ниже код к классу `Loan`:</span><span class="sxs-lookup"><span data-stu-id="0a18a-128">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="0a18a-129">Также потребуется создать приложение, которое использует класс `Loan`.</span><span class="sxs-lookup"><span data-stu-id="0a18a-129">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="0a18a-130">Сериализация объекта Loan</span><span class="sxs-lookup"><span data-stu-id="0a18a-130">Serialize the loan object</span></span>

1. <span data-ttu-id="0a18a-131">Откройте `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="0a18a-131">Open `Program.cs`.</span></span> <span data-ttu-id="0a18a-132">Добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="0a18a-132">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

<span data-ttu-id="0a18a-133">Добавьте обработчик событий для события `PropertyChanged` и несколько строк, чтобы изменить объект `Loan` и отобразить изменения.</span><span class="sxs-lookup"><span data-stu-id="0a18a-133">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="0a18a-134">Дополнения отображаются в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="0a18a-134">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

<span data-ttu-id="0a18a-135">На этом этапе можно запустить код и посмотреть текущие выходные данные:</span><span class="sxs-lookup"><span data-stu-id="0a18a-135">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="0a18a-136">При повторном запуске приложения выводятся одни и те же значения.</span><span class="sxs-lookup"><span data-stu-id="0a18a-136">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="0a18a-137">При каждом запуске программы создается новый объект Loan.</span><span class="sxs-lookup"><span data-stu-id="0a18a-137">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="0a18a-138">В реальной жизни процентная ставка время от времени меняется, но не при каждом запуске этого приложения.</span><span class="sxs-lookup"><span data-stu-id="0a18a-138">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="0a18a-139">Код сериализации позволяет сохранять последние процентные ставки между экземплярами приложения.</span><span class="sxs-lookup"><span data-stu-id="0a18a-139">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="0a18a-140">На следующем шаге для этого в класс Loan будет добавлена сериализация.</span><span class="sxs-lookup"><span data-stu-id="0a18a-140">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="0a18a-141">Использование сериализации для хранения объекта</span><span class="sxs-lookup"><span data-stu-id="0a18a-141">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="0a18a-142">Чтобы сохранить значения для класса Loan, прежде всего необходимо отметить класс атрибутом `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="0a18a-142">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="0a18a-143">Добавьте следующий код непосредственно перед определением класса Loan:</span><span class="sxs-lookup"><span data-stu-id="0a18a-143">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="0a18a-144">Атрибут <xref:System.SerializableAttribute> сообщает компилятору, что все находящееся в классе может быть сохранено в файле.</span><span class="sxs-lookup"><span data-stu-id="0a18a-144">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="0a18a-145">Поскольку событие `PropertyChanged` не представляет часть графа объекта, который должен быть сохранен, оно не подлежит сериализации.</span><span class="sxs-lookup"><span data-stu-id="0a18a-145">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="0a18a-146">В противном случае будут сериализованы все объекты, присоединенные к этому событию.</span><span class="sxs-lookup"><span data-stu-id="0a18a-146">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="0a18a-147">Можно добавить <xref:System.NonSerializedAttribute> к объявлению поля для обработчика событий `PropertyChanged`.</span><span class="sxs-lookup"><span data-stu-id="0a18a-147">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="0a18a-148">Начиная с C# 7.3 можно прикреплять атрибуты к резервному полю автоматически реализуемого свойства с помощью значения целевого объекта `field`.</span><span class="sxs-lookup"><span data-stu-id="0a18a-148">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="0a18a-149">Следующий код добавляет свойство `TimeLastLoaded` и помечает его как не подлежащее сериализации:</span><span class="sxs-lookup"><span data-stu-id="0a18a-149">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="0a18a-150">Следующим шагом будет добавление кода сериализации в приложение LoanApp.</span><span class="sxs-lookup"><span data-stu-id="0a18a-150">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="0a18a-151">Чтобы выполнить сериализацию класса и записать данные в файл, используйте пространства имен <xref:System.IO> и <xref:System.Runtime.Serialization.Formatters.Binary>.</span><span class="sxs-lookup"><span data-stu-id="0a18a-151">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="0a18a-152">Во избежание ввода полных имен можно добавить ссылки на необходимые пространства имен, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="0a18a-152">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

<span data-ttu-id="0a18a-153">Следующим шагом является добавление кода для десериализации объекта из файла при создании объекта.</span><span class="sxs-lookup"><span data-stu-id="0a18a-153">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="0a18a-154">Добавьте в класс константу для имени файла сериализованных данных, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="0a18a-154">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

<span data-ttu-id="0a18a-155">Затем добавьте следующий код после строки, которая создает объект `TestLoan`:</span><span class="sxs-lookup"><span data-stu-id="0a18a-155">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

<span data-ttu-id="0a18a-156">Прежде всего убедитесь, что файл существует.</span><span class="sxs-lookup"><span data-stu-id="0a18a-156">You first must check that the file exists.</span></span> <span data-ttu-id="0a18a-157">Если он существует, создайте класс <xref:System.IO.Stream> для чтения двоичного файла и класс <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> для преобразования файла.</span><span class="sxs-lookup"><span data-stu-id="0a18a-157">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="0a18a-158">Кроме того, необходимо преобразовать тип потока в тип объекта Loan.</span><span class="sxs-lookup"><span data-stu-id="0a18a-158">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="0a18a-159">Далее необходимо добавить код для сериализации класса в файл.</span><span class="sxs-lookup"><span data-stu-id="0a18a-159">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="0a18a-160">Добавьте следующий код после существующего кода в методе `Main`:</span><span class="sxs-lookup"><span data-stu-id="0a18a-160">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

<span data-ttu-id="0a18a-161">Теперь можно снова собрать и запустить приложение.</span><span class="sxs-lookup"><span data-stu-id="0a18a-161">At this point, you can again build and run the application.</span></span> <span data-ttu-id="0a18a-162">При первом запуске вы заметите, что процентная ставка имеет значение 7,5, а затем меняется на 7,1.</span><span class="sxs-lookup"><span data-stu-id="0a18a-162">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="0a18a-163">Закройте приложение, а затем снова запустите его.</span><span class="sxs-lookup"><span data-stu-id="0a18a-163">Close the application and then run it again.</span></span> <span data-ttu-id="0a18a-164">Теперь приложение выводит сообщение о том, что сохраненный файл прочитан и процентная ставка составляет 7,1, даже раньше кода, который меняет ее.</span><span class="sxs-lookup"><span data-stu-id="0a18a-164">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a18a-165">См. также</span><span class="sxs-lookup"><span data-stu-id="0a18a-165">See also</span></span>

- [<span data-ttu-id="0a18a-166">Сериализация (C#)</span><span class="sxs-lookup"><span data-stu-id="0a18a-166">Serialization (C#)</span></span>](index.md)
- [<span data-ttu-id="0a18a-167">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="0a18a-167">C# Programming Guide</span></span>](../../index.md)
