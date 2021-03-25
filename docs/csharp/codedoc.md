---
title: Документирование кода C# с помощью XML-комментариев
description: Сведения о том, как документировать код с использованием комментариев XML-документации и создавать XML-файл документации во время компиляции.
ms.date: 01/21/2020
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: cdc3937ba3b641b90aed85a604ca05195ea34fe7
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478482"
---
# <a name="document-your-c-code-with-xml-comments"></a><span data-ttu-id="c88c6-103">Документирование кода C# с помощью XML-комментариев</span><span class="sxs-lookup"><span data-stu-id="c88c6-103">Document your C# code with XML comments</span></span>

<span data-ttu-id="c88c6-104">Комментарии к XML-документации — это особый тип комментария, добавляемого перед определением определяемого пользователем типа или члена.</span><span class="sxs-lookup"><span data-stu-id="c88c6-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="c88c6-105">Их особенность в том, что компилятор может обрабатывать их для создания XML-файла документации во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="c88c6-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="c88c6-106">Созданный компилятором XML-файл можно распространять вместе со сборкой .NET, чтобы Visual Studio и другие интегрированные среды разработки могли использовать IntelliSense для отображения кратких сведений о типах или членах.</span><span class="sxs-lookup"><span data-stu-id="c88c6-106">The compiler-generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="c88c6-107">Кроме того, XML-файл можно запускать с помощью таких средств, как [DocFX](https://dotnet.github.io/docfx/) и [Sandcastle](https://github.com/EWSoftware/SHFB), и создавать веб-сайты со справочными сведениями по API.</span><span class="sxs-lookup"><span data-stu-id="c88c6-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="c88c6-108">Комментарии к XML-документации, как и все другие комментарии, пропускаются компилятором.</span><span class="sxs-lookup"><span data-stu-id="c88c6-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="c88c6-109">Можно создать XML-файл во время компиляции, выполнив одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="c88c6-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="c88c6-110">Если вы разрабатываете приложение с использованием .NET Core из командной строки, добавьте элемент `GenerateDocumentationFile` в раздел `<PropertyGroup>` CSPROJ-файла проекта.</span><span class="sxs-lookup"><span data-stu-id="c88c6-110">If you are developing an application with .NET Core from the command line, you can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="c88c6-111">Также можно указать путь к файлу документации напрямую с помощью [элемента `DocumentationFile`](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="c88c6-111">You can also specify the path to the documentation file directly using [`DocumentationFile` element](/visualstudio/msbuild/common-msbuild-project-properties).</span></span> <span data-ttu-id="c88c6-112">В следующем примере создается XML-файл в каталоге проекта с тем же именем корневого файла, что и у сборки:</span><span class="sxs-lookup"><span data-stu-id="c88c6-112">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

   <span data-ttu-id="c88c6-113">Оно эквивалентно следующему выражению:</span><span class="sxs-lookup"><span data-stu-id="c88c6-113">This is equivalent to the following:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- <span data-ttu-id="c88c6-114">Если вы разрабатываете приложение с помощью Visual Studio, щелкните правой кнопкой мыши проект и выберите **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="c88c6-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="c88c6-115">В диалоговом окне свойств откройте вкладку **Сборка** и выберите **XML-файл документации**.</span><span class="sxs-lookup"><span data-stu-id="c88c6-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="c88c6-116">Можно также изменить расположение, в котором компилятор записывает файл.</span><span class="sxs-lookup"><span data-stu-id="c88c6-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="c88c6-117">Если вы компилируете приложение .NET из командной строки, добавьте [параметр компилятора **DocumentationFile**](language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="c88c6-117">If you are compiling a .NET application from the command line, add the [**DocumentationFile** compiler option](language-reference/compiler-options/output.md#documentationfile) when compiling.</span></span>  

<span data-ttu-id="c88c6-118">Для вставки комментария к XML-документации используются три символа косой черты (`///`) и текст комментария в формате XML.</span><span class="sxs-lookup"><span data-stu-id="c88c6-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="c88c6-119">Пример:</span><span class="sxs-lookup"><span data-stu-id="c88c6-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="c88c6-120">Пошаговое руководство</span><span class="sxs-lookup"><span data-stu-id="c88c6-120">Walkthrough</span></span>

<span data-ttu-id="c88c6-121">Давайте разберем документирование простейшей математической библиотеки, чтобы новые разработчики могли без труда понимать и дополнять ее, а сторонние разработчики — легко использовать ее.</span><span class="sxs-lookup"><span data-stu-id="c88c6-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third-party developers to use.</span></span>

<span data-ttu-id="c88c6-122">Ниже приведен код для простой математической библиотеки.</span><span class="sxs-lookup"><span data-stu-id="c88c6-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="c88c6-123">Этот пример библиотеки поддерживает четыре основные арифметические операции `add`, `subtract`, `multiply` и `divide` с типами данных `int` и `double`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-123">The sample library supports four major arithmetic operations (`add`, `subtract`, `multiply`, and `divide`) on `int` and `double` data types.</span></span>

<span data-ttu-id="c88c6-124">Теперь вам нужна возможность создания справочного документа по API из кода для сторонних разработчиков, которые используют библиотеку, но не имеют доступа к исходному коду.</span><span class="sxs-lookup"><span data-stu-id="c88c6-124">Now you want to be able to create an API reference document from your code for third-party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="c88c6-125">Как упоминалось ранее, это можно сделать с помощью тегов XML-документации.</span><span class="sxs-lookup"><span data-stu-id="c88c6-125">As mentioned earlier XML documentation tags can be used to achieve this.</span></span> <span data-ttu-id="c88c6-126">Сейчас вы познакомитесь со стандартными XML-тегами, которые поддерживает компилятор C#.</span><span class="sxs-lookup"><span data-stu-id="c88c6-126">You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

## \<summary>

<span data-ttu-id="c88c6-127">Тег `<summary>` добавляет краткие сведения о типе или члене.</span><span class="sxs-lookup"><span data-stu-id="c88c6-127">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="c88c6-128">Я продемонстрирую использование тега путем его добавления в определение класса `Math` и первый метод `Add`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-128">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="c88c6-129">Кроме того, его можно применить к остальной части кода.</span><span class="sxs-lookup"><span data-stu-id="c88c6-129">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="c88c6-130">Тег `<summary>` имеет важное значение. Мы рекомендуем всегда использовать его, так как его содержимое — основной источник информации о типе или члене в IntelliSense либо справочном документе по API.</span><span class="sxs-lookup"><span data-stu-id="c88c6-130">The `<summary>` tag is important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

## \<remarks>

<span data-ttu-id="c88c6-131">Тег `<remarks>` дополняет сведения о типах или членах, предоставляемые тегом `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-131">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="c88c6-132">В этом примере вы просто добавите его в класс.</span><span class="sxs-lookup"><span data-stu-id="c88c6-132">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## \<returns>

<span data-ttu-id="c88c6-133">Тег `<returns>` описывает возвращаемое значение объявления метода.</span><span class="sxs-lookup"><span data-stu-id="c88c6-133">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="c88c6-134">Как и ранее, в следующем примере демонстрируется тег `<returns>` в первом методе `Add`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-134">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="c88c6-135">То же самое можно сделать и с другими методами.</span><span class="sxs-lookup"><span data-stu-id="c88c6-135">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## \<value>

<span data-ttu-id="c88c6-136">Тег `<value>` аналогичен тегу `<returns>`, за исключением того, что он используется для свойств.</span><span class="sxs-lookup"><span data-stu-id="c88c6-136">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="c88c6-137">Если бы в библиотеке `Math` было статическое свойство `PI`, вы использовали бы этот тег следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c88c6-137">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## \<example>

<span data-ttu-id="c88c6-138">Тег `<example>` применяется для включения примера в XML-документацию.</span><span class="sxs-lookup"><span data-stu-id="c88c6-138">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="c88c6-139">В этом случае нужно использовать дочерний тег `<code>`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-139">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="c88c6-140">Тег `code` сохраняет разрывы строк и отступы для более длинных примеров.</span><span class="sxs-lookup"><span data-stu-id="c88c6-140">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

## \<para>

<span data-ttu-id="c88c6-141">Тег `<para>` используется для форматирования содержимого в его родительском теге.</span><span class="sxs-lookup"><span data-stu-id="c88c6-141">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="c88c6-142">`<para>` обычно используется внутри тега, такого как `<remarks>` или `<returns>`, чтобы разделить текст на абзацы.</span><span class="sxs-lookup"><span data-stu-id="c88c6-142">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="c88c6-143">Содержимое тега `<remarks>` для определения класса можно отформатировать.</span><span class="sxs-lookup"><span data-stu-id="c88c6-143">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## \<c>

<span data-ttu-id="c88c6-144">Что касается форматирования, можно использовать тег `<c>` для пометки части текста в качестве кода.</span><span class="sxs-lookup"><span data-stu-id="c88c6-144">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="c88c6-145">Он подобен тегу `<code>`, но является встроенным.</span><span class="sxs-lookup"><span data-stu-id="c88c6-145">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="c88c6-146">Он полезен, если требуется показать пример кода как часть содержимого тега.</span><span class="sxs-lookup"><span data-stu-id="c88c6-146">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="c88c6-147">Давайте обновим в документацию для класса `Math`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-147">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## \<exception>

<span data-ttu-id="c88c6-148">С помощью тега `<exception>` можно сообщить разработчикам, что метод может генерировать определенные исключения.</span><span class="sxs-lookup"><span data-stu-id="c88c6-148">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="c88c6-149">Если взглянуть на библиотеку `Math`, можно увидеть, что оба метода `Add` создают исключение при выполнении определенного условия.</span><span class="sxs-lookup"><span data-stu-id="c88c6-149">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="c88c6-150">Метод `Divide` с типом integer также создает исключение (хотя и не столь очевидно), если параметр `b` равен нулю.</span><span class="sxs-lookup"><span data-stu-id="c88c6-150">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="c88c6-151">Теперь добавьте в этот метод документацию по исключению.</span><span class="sxs-lookup"><span data-stu-id="c88c6-151">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="c88c6-152">Атрибут `cref` представляет ссылку на исключение, которое доступно из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="c88c6-152">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="c88c6-153">Это может быть любой тип, определенный в проекте или ссылочной сборке.</span><span class="sxs-lookup"><span data-stu-id="c88c6-153">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="c88c6-154">Компилятор выдаст предупреждение, если его значение не может быть разрешено.</span><span class="sxs-lookup"><span data-stu-id="c88c6-154">The compiler will issue a warning if its value cannot be resolved.</span></span>

## \<see>

<span data-ttu-id="c88c6-155">Тег `<see>` позволяет создать активную ссылку на страницу документации по другому элементу кода.</span><span class="sxs-lookup"><span data-stu-id="c88c6-155">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="c88c6-156">В следующем примере будет создана активная ссылка между двумя методами `Add`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-156">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="c88c6-157">Атрибут `cref` является **обязательным** и представляет ссылку на тип или его член, который доступен из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="c88c6-157">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="c88c6-158">Это может быть любой тип, определенный в проекте или ссылочной сборке.</span><span class="sxs-lookup"><span data-stu-id="c88c6-158">This can be any type defined in the project or a referenced assembly.</span></span>

## \<seealso>

<span data-ttu-id="c88c6-159">Тег `<seealso>` используется так же, как тег `<see>`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-159">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="c88c6-160">Единственное различие заключается в том, что его содержимое обычно помещается в раздел "См. также".</span><span class="sxs-lookup"><span data-stu-id="c88c6-160">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="c88c6-161">Мы добавим тег `seealso` в метод `Add` с типом integer для ссылки на другие методы в классе, принимающие параметры с типом integer:</span><span class="sxs-lookup"><span data-stu-id="c88c6-161">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="c88c6-162">Атрибут `cref` представляет ссылку на тип или его член, который доступен из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="c88c6-162">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="c88c6-163">Это может быть любой тип, определенный в проекте или ссылочной сборке.</span><span class="sxs-lookup"><span data-stu-id="c88c6-163">This can be any type defined in the project or a referenced assembly.</span></span>

## \<param>

<span data-ttu-id="c88c6-164">Тег `<param>` используется для описания параметров метода.</span><span class="sxs-lookup"><span data-stu-id="c88c6-164">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="c88c6-165">Ниже приведен пример на метода `Add` с типом double: параметр, описываемый тегом, указан в **обязательном атрибуте** `name`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-165">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## \<typeparam>

<span data-ttu-id="c88c6-166">Тег `<typeparam>` используется так же, как тег `<param>`, но для объявлений универсального типа или метода он служит для описания универсального параметра.</span><span class="sxs-lookup"><span data-stu-id="c88c6-166">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="c88c6-167">Добавьте в класс `Math` быстрый универсальный метод, чтобы проверить, что одно количество больше другого.</span><span class="sxs-lookup"><span data-stu-id="c88c6-167">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## \<paramref>

<span data-ttu-id="c88c6-168">Иногда в процессе описания выполнения метода в теге `<summary>` может потребоваться создание ссылки на параметр.</span><span class="sxs-lookup"><span data-stu-id="c88c6-168">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="c88c6-169">Для этого отлично подойдет тег `<paramref>`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-169">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="c88c6-170">Обновим сводку по методу `Add` с типом double.</span><span class="sxs-lookup"><span data-stu-id="c88c6-170">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="c88c6-171">Как и для тега `<param>`, имя параметра указано в **обязательном атрибуте** `name`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-171">Like the `<param>` tag, the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## \<typeparamref>

<span data-ttu-id="c88c6-172">Тег `<typeparamref>` используется так же, как тег `<paramref>`, но для объявлений универсального типа или метода он служит для описания универсального параметра.</span><span class="sxs-lookup"><span data-stu-id="c88c6-172">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="c88c6-173">Можно использовать созданные ранее универсальный метод.</span><span class="sxs-lookup"><span data-stu-id="c88c6-173">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## \<list>

<span data-ttu-id="c88c6-174">Тег `<list>` используется для форматирования сведений о документации в виде упорядоченного списка, неупорядоченного списка или таблицы.</span><span class="sxs-lookup"><span data-stu-id="c88c6-174">You use the `<list>` tag to format documentation information as an ordered list, unordered list, or table.</span></span> <span data-ttu-id="c88c6-175">Создайте неупорядоченный список для каждой математической операции, поддерживаемой библиотекой `Math`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-175">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="c88c6-176">Упорядоченный список или таблицу можно сформировать, изменив атрибут `type` на `number` или `table` соответственно.</span><span class="sxs-lookup"><span data-stu-id="c88c6-176">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

## \<inheritdoc>

<span data-ttu-id="c88c6-177">Тег `<inheritdoc>` можно использовать для наследования XML-комментариев от базовых классов, интерфейсов и аналогичных методов.</span><span class="sxs-lookup"><span data-stu-id="c88c6-177">You can use the `<inheritdoc>` tag to inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="c88c6-178">Это позволяет обойтись без копирования и вставки одинаковых XML-комментариев и автоматически поддерживать их синхронизацию.</span><span class="sxs-lookup"><span data-stu-id="c88c6-178">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a><span data-ttu-id="c88c6-179">Сборка</span><span class="sxs-lookup"><span data-stu-id="c88c6-179">Put it all together</span></span>

<span data-ttu-id="c88c6-180">Вы выполнили инструкции в этом учебнике и включили теги в код там, где необходимо. Теперь ваш код должен иметь следующий вид:</span><span class="sxs-lookup"><span data-stu-id="c88c6-180">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="c88c6-181">В коде можно создать подробную документацию к веб-сайту, содержащую интерактивные перекрестные ссылки.</span><span class="sxs-lookup"><span data-stu-id="c88c6-181">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="c88c6-182">При этом вы можете столкнуться с другой проблемой — такой код очень трудно читать.</span><span class="sxs-lookup"><span data-stu-id="c88c6-182">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="c88c6-183">Для любого разработчика, который хочет вносить дополнения в этот код, необходимость обработки большого количества данных становится настоящим кошмаром.</span><span class="sxs-lookup"><span data-stu-id="c88c6-183">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="c88c6-184">К счастью, есть XML-тег, который поможет справиться с этой задачей:</span><span class="sxs-lookup"><span data-stu-id="c88c6-184">Thankfully there's an XML tag that can help you deal with this:</span></span>

## \<include>

<span data-ttu-id="c88c6-185">Тег `<include>` позволяет обращаться к комментариям в отдельном XML-файле, описывающем типы и члены в исходном коде, а не размещать комментарии к документации непосредственно в файле исходного кода.</span><span class="sxs-lookup"><span data-stu-id="c88c6-185">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="c88c6-186">Переместим все XML-теги в отдельный файл XML с именем `docs.xml`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-186">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="c88c6-187">Файлу можно задать любое имя.</span><span class="sxs-lookup"><span data-stu-id="c88c6-187">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="c88c6-188">В приведенном выше XML комментарии к документации по каждому члену отображаются непосредственно внутри тега с именем, соответствующим его назначению.</span><span class="sxs-lookup"><span data-stu-id="c88c6-188">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="c88c6-189">Можно выбрать собственную стратегию.</span><span class="sxs-lookup"><span data-stu-id="c88c6-189">You can choose your own strategy.</span></span>
<span data-ttu-id="c88c6-190">Теперь, когда комментарии XML находятся в отдельном файле, давайте посмотрим, как можно улучшить удобочитаемость кода с помощью тега `<include>`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-190">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="c88c6-191">Сейчас чтение кода снова не вызывает сложностей, и никакие сведения не были потеряны.</span><span class="sxs-lookup"><span data-stu-id="c88c6-191">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="c88c6-192">Атрибут `file` представляет имя XML-файла, содержащего документацию.</span><span class="sxs-lookup"><span data-stu-id="c88c6-192">The `file` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="c88c6-193">Атрибут `path` представляет запрос [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) к `tag name`, находящемуся в указанном `file`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-193">The `path` attribute represents an [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) query to the `tag name` present in the specified `file`.</span></span>

<span data-ttu-id="c88c6-194">Атрибут `name` представляет спецификатор имени в теге, который предшествует комментариям.</span><span class="sxs-lookup"><span data-stu-id="c88c6-194">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="c88c6-195">Атрибут `id`, который можно использовать вместо `name`, представляет идентификатор для тега, предшествующего комментариям.</span><span class="sxs-lookup"><span data-stu-id="c88c6-195">The `id` attribute, which can be used in place of `name`, represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="c88c6-196">Пользовательские теги</span><span class="sxs-lookup"><span data-stu-id="c88c6-196">User-defined tags</span></span>

<span data-ttu-id="c88c6-197">Все описанные выше теги распознаются компилятором C#.</span><span class="sxs-lookup"><span data-stu-id="c88c6-197">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="c88c6-198">Тем не менее пользователь может определять собственные теги.</span><span class="sxs-lookup"><span data-stu-id="c88c6-198">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="c88c6-199">Инструменты, такие как Sandcastle, обеспечивают поддержку дополнительных тегов (например, [\<event>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) и [\<note>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm)) и даже поддержку [пространств имен документирования](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="c88c6-199">Tools like Sandcastle bring support for extra tags like [\<event>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) and [\<note>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm), and even support [documenting namespaces](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="c88c6-200">Средства создания пользовательской или внутренней документации также можно использовать со стандартными тегами. Кроме того, поддерживается несколько выходных форматов — от HTML до PDF.</span><span class="sxs-lookup"><span data-stu-id="c88c6-200">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="c88c6-201">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="c88c6-201">Recommendations</span></span>

<span data-ttu-id="c88c6-202">Документирование кода рекомендуется по многим причинам.</span><span class="sxs-lookup"><span data-stu-id="c88c6-202">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="c88c6-203">Далее приводится ряд рекомендаций, распространенные сценарии использования и вопросы, которые нужно иметь в виду при работе с тегами XML-документации в коде C#.</span><span class="sxs-lookup"><span data-stu-id="c88c6-203">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

- <span data-ttu-id="c88c6-204">Для обеспечения согласованности все открытые типы и их члены должны быть задокументированы.</span><span class="sxs-lookup"><span data-stu-id="c88c6-204">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="c88c6-205">Если это необходимо, задокументируйте их все.</span><span class="sxs-lookup"><span data-stu-id="c88c6-205">If you must do it, do it all.</span></span>
- <span data-ttu-id="c88c6-206">Закрытые члены можно также задокументировать с помощью XML-комментариев.</span><span class="sxs-lookup"><span data-stu-id="c88c6-206">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="c88c6-207">Однако это приводит к раскрытию внутренних (возможно, конфиденциальных) процессов библиотеки.</span><span class="sxs-lookup"><span data-stu-id="c88c6-207">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
- <span data-ttu-id="c88c6-208">Как минимум, типы и их члены должен иметь тег `<summary>`, так как его содержимое требуется для IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c88c6-208">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
- <span data-ttu-id="c88c6-209">Текст документации должны быть написан с использованием законченных предложений, в конце которых ставится точка.</span><span class="sxs-lookup"><span data-stu-id="c88c6-209">Documentation text should be written using complete sentences ending with full stops.</span></span>
- <span data-ttu-id="c88c6-210">Разделяемые классы полностью поддерживаются, и данные о документации объединяются в одну запись для этого типа.</span><span class="sxs-lookup"><span data-stu-id="c88c6-210">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
- <span data-ttu-id="c88c6-211">Компилятор проверяет синтаксис тегов `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` и `<typeparam>`.</span><span class="sxs-lookup"><span data-stu-id="c88c6-211">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>`, and `<typeparam>` tags.</span></span>
- <span data-ttu-id="c88c6-212">Компилятор проверяет параметры, которые содержат пути к файлам и ссылки на другие части кода.</span><span class="sxs-lookup"><span data-stu-id="c88c6-212">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c88c6-213">См. также</span><span class="sxs-lookup"><span data-stu-id="c88c6-213">See also</span></span>

- [<span data-ttu-id="c88c6-214">Комментарии к XML-документации (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="c88c6-214">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/index.md)
- [<span data-ttu-id="c88c6-215">Рекомендуемые теги для комментариев документации (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="c88c6-215">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
