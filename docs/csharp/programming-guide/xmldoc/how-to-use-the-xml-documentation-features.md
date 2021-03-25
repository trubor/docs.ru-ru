---
title: Руководство по программированию на C#. Использование XML-документации
description: Сведения об использовании XML-документации. Изучите примеры кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 3a030e07e6f0e48a37c1682ef1d93b33932bbaaa
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478421"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="84782-104">Практическое руководство. Использование XML-документации</span><span class="sxs-lookup"><span data-stu-id="84782-104">How to use the XML documentation features</span></span>

<span data-ttu-id="84782-105">В данном примере представлены основные общие сведения о задокументированном типе.</span><span class="sxs-lookup"><span data-stu-id="84782-105">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="84782-106">Пример</span><span class="sxs-lookup"><span data-stu-id="84782-106">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="84782-107">В примере создается файл *.xml* со следующим содержимым:</span><span class="sxs-lookup"><span data-stu-id="84782-107">The example generates an *.xml* file with the following contents.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xmlsample</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            <summary>
            Class level summary documentation goes here.
            </summary>
            <remarks>
            Longer comments can be associated with a type or member through
            the remarks tag.
            </remarks>
        </member>
        <member name="F:TestClass._name">
            <summary>
            Store for the Name property.
            </summary>
        </member>
        <member name="M:TestClass.#ctor">
            <summary>
            The class constructor.
            </summary>
        </member>
        <member name="P:TestClass.Name">
            <summary>
            Name property.
            </summary>
            <value>
            A value tag is used to describe the property value.
            </value>
        </member>
        <member name="M:TestClass.SomeMethod(System.String)">
            <summary>
            Description for SomeMethod.
            </summary>
            <param name="s"> Parameter description for s goes here.</param>
            <seealso cref="T:System.String">
            You can use the cref attribute on any tag to reference a type or member
            and the compiler will check that the reference exists.
            </seealso>
        </member>
        <member name="M:TestClass.SomeOtherMethod">
            <summary>
            Some other method.
            </summary>
            <returns>
            Return values are described through the returns tag.
            </returns>
            <seealso cref="M:TestClass.SomeMethod(System.String)">
            Notice the use of the cref attribute to reference a specific method.
            </seealso>
        </member>
        <member name="M:TestClass.Main(System.String[])">
            <summary>
            The entry point for the application.
            </summary>
            <param name="args"> A list of command line arguments.</param>
        </member>
        <member name="T:TestInterface">
            <summary>
            Documentation that describes the interface goes here.
            </summary>
            <remarks>
            Details about the interface go here.
            </remarks>
        </member>
        <member name="M:TestInterface.InterfaceMethod(System.Int32)">
            <summary>
            Documentation that describes the method goes here.
            </summary>
            <param name="n">
            Parameter n requires an integer argument.
            </param>
            <returns>
            The method returns an integer.
            </returns>
        </member>
    </members>
</doc>
```

## <a name="compiling-the-code"></a><span data-ttu-id="84782-108">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="84782-108">Compiling the code</span></span>

<span data-ttu-id="84782-109">Чтобы скомпилировать этот пример, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="84782-109">To compile the example, enter the following command:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="84782-110">Эта команда создает XML-файл *XMLsample.xml*, который можно просмотреть в браузере или с помощью команды `TYPE`.</span><span class="sxs-lookup"><span data-stu-id="84782-110">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the `TYPE` command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="84782-111">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="84782-111">Robust programming</span></span>

<span data-ttu-id="84782-112">Документация XML начинается с `///`.</span><span class="sxs-lookup"><span data-stu-id="84782-112">XML documentation starts with `///`.</span></span> <span data-ttu-id="84782-113">При создании проекта мастер добавляет несколько строк `///`.</span><span class="sxs-lookup"><span data-stu-id="84782-113">When you create a new project, the wizards put some starter `///` lines in for you.</span></span> <span data-ttu-id="84782-114">Обработка этих комментариев имеет некоторые ограничения.</span><span class="sxs-lookup"><span data-stu-id="84782-114">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="84782-115">Документация должна представлять собой XML с правильным форматом.</span><span class="sxs-lookup"><span data-stu-id="84782-115">The documentation must be well-formed XML.</span></span> <span data-ttu-id="84782-116">Если формат XML неверен, то выдается предупреждение и файл документации содержит комментарий о том, что произошла ошибка.</span><span class="sxs-lookup"><span data-stu-id="84782-116">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="84782-117">Разработчики могут создавать собственные наборы тегов.</span><span class="sxs-lookup"><span data-stu-id="84782-117">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="84782-118">При этом существует [рекомендуемый набор тегов](recommended-tags-for-documentation-comments.md).</span><span class="sxs-lookup"><span data-stu-id="84782-118">There is a [recommended set of tags](recommended-tags-for-documentation-comments.md).</span></span> <span data-ttu-id="84782-119">Некоторые рекомендуемые теги имеют особые значения.</span><span class="sxs-lookup"><span data-stu-id="84782-119">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="84782-120">Тег `<param>` используется для описания параметров.</span><span class="sxs-lookup"><span data-stu-id="84782-120">The `<param>` tag is used to describe parameters.</span></span> <span data-ttu-id="84782-121">При использовании этого тега компилятор проверяет, что параметр существует и все параметры описаны в документации.</span><span class="sxs-lookup"><span data-stu-id="84782-121">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="84782-122">При сбое проверки компилятор выдает предупреждение.</span><span class="sxs-lookup"><span data-stu-id="84782-122">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="84782-123">Атрибут `cref` может быть присоединен к любому тегу для ссылки на элемент кода.</span><span class="sxs-lookup"><span data-stu-id="84782-123">The `cref` attribute can be attached to any tag to reference a code element.</span></span> <span data-ttu-id="84782-124">Компилятор проверяет наличие этого элемента кода.</span><span class="sxs-lookup"><span data-stu-id="84782-124">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="84782-125">При сбое проверки компилятор выдает предупреждение.</span><span class="sxs-lookup"><span data-stu-id="84782-125">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="84782-126">Компилятор учитывает любые операторы `using` при поиске типа, описанного в атрибуте `cref`.</span><span class="sxs-lookup"><span data-stu-id="84782-126">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="84782-127">Тег `<summary>` используется технологией IntelliSense в Visual Studio для отображения дополнительных сведений о типе или элементе.</span><span class="sxs-lookup"><span data-stu-id="84782-127">The `<summary>` tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="84782-128">XML-файл не предоставляет полную информацию о типе и членах (например, он не содержит никаких сведений о типе).</span><span class="sxs-lookup"><span data-stu-id="84782-128">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="84782-129">Чтобы получить полную информацию о типе или элементе, используйте файл документации вместе с отражением для текущего типа или элемента.</span><span class="sxs-lookup"><span data-stu-id="84782-129">To get full information about a type or member, use the documentation file together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="84782-130">См. также</span><span class="sxs-lookup"><span data-stu-id="84782-130">See also</span></span>

- [<span data-ttu-id="84782-131">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="84782-131">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="84782-132">**DocumentationFile** (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="84782-132">**DocumentationFile** (C# compiler options</span></span>](../../language-reference/compiler-options/output.md#documentationfile)
- [<span data-ttu-id="84782-133">Комментарии XML-документации</span><span class="sxs-lookup"><span data-stu-id="84782-133">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="84782-134">Обработчик документации DocFX</span><span class="sxs-lookup"><span data-stu-id="84782-134">DocFX documentation processor</span></span>](https://dotnet.github.io/docfx/)
- [<span data-ttu-id="84782-135">Обработчик документации Sandcastle</span><span class="sxs-lookup"><span data-stu-id="84782-135">Sandcastle documentation processor</span></span>](https://github.com/EWSoftware/SHFB)
