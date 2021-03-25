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
# <a name="how-to-use-the-xml-documentation-features"></a>Практическое руководство. Использование XML-документации

В данном примере представлены основные общие сведения о задокументированном типе.

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

В примере создается файл *.xml* со следующим содержимым:

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

## <a name="compiling-the-code"></a>Компиляция кода

Чтобы скомпилировать этот пример, введите следующую команду:

`csc XMLsample.cs /doc:XMLsample.xml`

Эта команда создает XML-файл *XMLsample.xml*, который можно просмотреть в браузере или с помощью команды `TYPE`.

## <a name="robust-programming"></a>Отказоустойчивость

Документация XML начинается с `///`. При создании проекта мастер добавляет несколько строк `///`. Обработка этих комментариев имеет некоторые ограничения.

- Документация должна представлять собой XML с правильным форматом. Если формат XML неверен, то выдается предупреждение и файл документации содержит комментарий о том, что произошла ошибка.

- Разработчики могут создавать собственные наборы тегов. При этом существует [рекомендуемый набор тегов](recommended-tags-for-documentation-comments.md). Некоторые рекомендуемые теги имеют особые значения.

  - Тег `<param>` используется для описания параметров. При использовании этого тега компилятор проверяет, что параметр существует и все параметры описаны в документации. При сбое проверки компилятор выдает предупреждение.

  - Атрибут `cref` может быть присоединен к любому тегу для ссылки на элемент кода. Компилятор проверяет наличие этого элемента кода. При сбое проверки компилятор выдает предупреждение. Компилятор учитывает любые операторы `using` при поиске типа, описанного в атрибуте `cref`.

  - Тег `<summary>` используется технологией IntelliSense в Visual Studio для отображения дополнительных сведений о типе или элементе.

    > [!NOTE]
    > XML-файл не предоставляет полную информацию о типе и членах (например, он не содержит никаких сведений о типе). Чтобы получить полную информацию о типе или элементе, используйте файл документации вместе с отражением для текущего типа или элемента.

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [**DocumentationFile** (параметры компилятора C#)](../../language-reference/compiler-options/output.md#documentationfile)
- [Комментарии XML-документации](./index.md)
- [Обработчик документации DocFX](https://dotnet.github.io/docfx/)
- [Обработчик документации Sandcastle](https://github.com/EWSoftware/SHFB)
