---
title: Пошаговое руководство. Создание и использование динамических объектов (C# и Visual Basic)
description: Узнайте, как создавать и использовать динамические объекты. Создайте настраиваемый динамический объект и проект, использующий библиотеку IronPython.
ms.date: 03/24/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.openlocfilehash: 3b342f23a2974affdcd7a1e91093aaef504afb63
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111027"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>Пошаговое руководство. Создание и использование динамических объектов (C# и Visual Basic)

Динамические объекты предоставляют такие элементы, как свойства и методы, во время выполнения, а не во время компиляции. Это позволяет создавать объекты для работы со структурами, не соответствующими статическому типу или формату. Например, можно использовать динамический объект для ссылки на модель DOM HTML, которая может содержать любую комбинацию допустимых элементов и атрибутов разметки HTML. Поскольку каждый документ HTML является уникальным, элементы для конкретного документа HTML определяются во время выполнения. Наиболее распространенный способ ссылки на атрибут элемента HTML заключается в передаче имени этого атрибута в метод `GetProperty` элемента. Для ссылки на атрибут `id` элемента HTML `<div id="Div1">` следует сначала получить ссылку на элемент `<div>`, а затем использовать `divElement.GetProperty("id")`. При использовании динамического объекта можно сослаться на атрибут `id` в виде `divElement.id`.

 Динамические объекты обеспечивают удобный доступ к динамическим языкам, таким как IronPython и IronRuby. С помощью динамического объекта можно ссылаться на динамический скрипт, интерпретируемый во время выполнения.

 Ссылка на динамический объект выполняется с помощью позднего связывания. В C# тип объектов с поздним связыванием указывается как `dynamic`. В Visual Basic тип объектов с поздним связыванием указывается как `Object`. Дополнительные сведения см. в разделах [dynamic](../../language-reference/builtin-types/reference-types.md) и [Раннее и позднее связывание](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).

 Вы можете создавать настраиваемые динамические объекты, используя классы из пространства имен <xref:System.Dynamic?displayProperty=nameWithType>. Например, можно создать объект <xref:System.Dynamic.ExpandoObject> и задать члены этого объекта во время выполнения. Также можно создать собственный тип, наследующий класс <xref:System.Dynamic.DynamicObject>. Затем для обеспечения динамических функциональных возможностей во время выполнения можно переопределить члены класса <xref:System.Dynamic.DynamicObject>.

 Эта статья содержит два независимых пошаговых руководства.

- Создание пользовательского объекта, который динамически предоставляет содержимое текстового файла в виде свойств объекта.

- Создание проекта, использующего библиотеку `IronPython`.

Вы можете выполнить одно из них или оба, в последнем случае порядок не имеет значения.

## <a name="prerequisites"></a>Предварительные требования

* [Visual Studio 2019 версии 16.9 или более поздней](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) с установленной рабочей нагрузкой **Разработка классических приложений .NET**. Пакет SDK для .NET 5.0 устанавливается автоматически при выборе этой рабочей нагрузки.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

* Для второго пошагового руководства установите [IronPython](https://ironpython.net/) для .NET. Перейдите на [страницу загрузки](https://ironpython.net/download/) для получения последней версии.

## <a name="create-a-custom-dynamic-object"></a>Создание пользовательского динамического объекта

В первом пошаговом руководстве определяется пользовательский динамический объект, выполняющий поиск по содержимому текстового файла. Динамическое свойство указывает искомый текст. Например, если в вызывающем коде указано `dynamicFile.Sample`, динамический класс возвращает общий список строк, содержащий все строки из файла, которые начинаются со слова "Sample". При поиске не учитывается регистр. Динамический класс также поддерживает два дополнительных аргумента. Первый аргумент — это значение перечисления параметра поиска, задающее, где динамический класс должен искать соответствия: в начале строки, в конце строки или в любом месте строки. Второй аргумент задает, что динамический класс должен перед поиском отсекать начальные и конечные пробелы в каждой строке. Например, если в вызывающем коде указано `dynamicFile.Sample(StringSearchOption.Contains)`, динамический класс выполняет поиск слова "Sample" в любом месте строки. Если в вызывающем коде указано `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, динамический класс выполняет поиск слова "Sample" в начале каждой строки и не удаляет начальные и конечные пробелы в строках. По умолчанию динамический класс выполняет поиск соответствия в начале каждой строки, предварительно удаляя начальные и конечные пробелы.

### <a name="to-create-a-custom-dynamic-class"></a>Создание пользовательского динамического класса

1. Запустите Visual Studio.

1. Выберите **Создать новый проект**.

1. В диалоговом окне **Создание нового проекта** выберите C# или Visual Basic, выберите **Консольное приложение**, а затем нажмите кнопку **Далее**.

1. В диалоговом окне **Настройка нового проекта** введите значение `DynamicSample` для параметра **Имя проекта** и нажмите кнопку **Далее**.

1. В диалоговом окне **Дополнительные сведения** выберите значение **.NET 5.0 (текущая)** для параметра **Целевая платформа**, а затем нажмите кнопку **Создать**.

   Создается новый проект.

1. В **обозревателе решений** щелкните проект DynamicSample правой кнопкой мыши и выберите **Добавить** > **Класс**. В поле **Имя** введите `ReadOnlyFile`, а затем нажмите кнопку **Добавить**.

   Будет добавлен новый файл, содержащий класс ReadOnlyFile.

1. В верхней части файла *ReadOnlyFile.cs* или *ReadOnlyFile.vb* добавьте следующий код для импорта пространств имен <xref:System.IO?displayProperty=nameWithType> и <xref:System.Dynamic?displayProperty=nameWithType>.

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]

1. Пользовательский динамический объект использует перечисление для определения условия поиска. Перед оператором класса добавьте следующее определение перечисления.

    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]

1. Обновите оператор класса, чтобы он наследовал класс `DynamicObject`, как показано в следующем примере кода.

    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

1. Добавьте в класс `ReadOnlyFile` следующий код, чтобы задать закрытое поле для пути к файлу и конструктор для класса `ReadOnlyFile`.

    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]

1. Добавьте следующий метод `GetPropertyValue` в класс `ReadOnlyFile`. Метод `GetPropertyValue` принимает в качестве входных данных условие поиска и возвращает строки текстового файла, соответствующие этому условию. Динамический метод, предоставленный классом `ReadOnlyFile`, вызывает метод `GetPropertyValue` для извлечения соответствующих результатов.

    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]

1. После метода `GetPropertyValue` добавьте следующий код, чтобы переопределить метод <xref:System.Dynamic.DynamicObject.TryGetMember%2A> класса <xref:System.Dynamic.DynamicObject>. Метод <xref:System.Dynamic.DynamicObject.TryGetMember%2A> вызывается при запросе члена динамического класса без указания аргументов. Аргумент `binder` содержит сведения об элементе, на который дается ссылка, а аргумент `result` ссылается на результат, возвращенный для указанного элемента. Метод <xref:System.Dynamic.DynamicObject.TryGetMember%2A> возвращает логическое значение `true`, если запрошенный элемент существует. В противном случае возвращается `false`.

    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]

1. После метода `TryGetMember` добавьте следующий код, чтобы переопределить метод <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> класса <xref:System.Dynamic.DynamicObject>. Метод <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> вызывается при запросе члена динамического класса с аргументами. Аргумент `binder` содержит сведения об элементе, на который дается ссылка, а аргумент `result` ссылается на результат, возвращенный для указанного элемента. Аргумент `args` содержит массив аргументов, передаваемых в элемент. Метод <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> возвращает логическое значение `true`, если запрошенный элемент существует. В противном случае возвращается `false`.

    Пользовательская версия метода `TryInvokeMember` ожидает, что первый аргумент будет значением из перечисления `StringSearchOption`, заданного на предыдущем шаге. Метод `TryInvokeMember` ожидает, что второй аргумент будет логическим значением. Если один или оба элемента имеют допустимые значения, они передаются в метод `GetPropertyValue` для получения результатов.

    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]

1. Сохраните и закройте файл.

### <a name="to-create-a-sample-text-file"></a>Создание примера текстового файла

1. В **обозревателе решений** щелкните проект DynamicSample правой кнопкой мыши и выберите **Добавить** > **Новый элемент**. На панели **Установленные шаблоны** выберите **Общие**, а затем шаблон **Текстовый файл**. В поле **Имя** оставьте имя по умолчанию *TextFile1.txt* и нажмите кнопку **Добавить**. В проект добавится новый текстовый файл.

1. Скопируйте в файл *TextFile1.txt* следующий текст.

    ```text
    List of customers and suppliers

    Supplier: Lucerne Publishing (https://www.lucernepublishing.com/)
    Customer: Preston, Chris
    Customer: Hines, Patrick
    Customer: Cameron, Maria
    Supplier: Graphic Design Institute (https://www.graphicdesigninstitute.com/)
    Supplier: Fabrikam, Inc. (https://www.fabrikam.com/)
    Customer: Seubert, Roxanne
    Supplier: Proseware, Inc. (http://www.proseware.com/)
    Customer: Adolphi, Stephan
    Customer: Koch, Paul
    ```

1. Сохраните и закройте файл.

### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>Создание примера приложения, в котором применяется пользовательский динамический объект

1. В **обозревателе решений** дважды щелкните файл *Program.vb*, если используется Visual Basic, или файл *Program.cs*, если используется Visual C#.

2. Добавьте следующий код в процедуру `Main`, чтобы создать экземпляр класса `ReadOnlyFile` для файла *TextFile1.txt*. В этом коде используется позднее связывание для вызова динамических элементов и извлечения строк текста, которые содержат строку "Customer".

     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/Program.vb#8)]

3. Сохраните файл и нажмите клавиши <kbd>CTRL</kdb>+<kbd>F5</kbd> для сборки и запуска приложения.

## <a name="call-a-dynamic-language-library"></a>Вызов библиотеки динамического языка

В следующем пошаговом руководстве создается проект, который осуществляет доступ к библиотеке, написанной на динамическом языке IronPython.

### <a name="to-create-a-custom-dynamic-class"></a>Создание пользовательского динамического класса

1. В Visual Studio выберите **Файл** > **Создать** > **Проект**.

1. В диалоговом окне **Создание нового проекта** выберите C# или Visual Basic, выберите **Консольное приложение**, а затем нажмите кнопку **Далее**.

1. В диалоговом окне **Настройка нового проекта** введите значение `DynamicIronPythonSample` для параметра **Имя проекта** и нажмите кнопку **Далее**.

1. В диалоговом окне **Дополнительные сведения** выберите значение **.NET 5.0 (текущая)** для параметра **Целевая платформа**, а затем нажмите кнопку **Создать**.

   Создается новый проект.

1. Установите пакет NuGet [IronPython](https://www.nuget.org/packages/IronPython).

1. Если вы используете Visual Basic, отредактируйте файл *Program.vb*. Если вы используете Visual C#, отредактируйте файл *Program.cs*.

1. В верхней части файла добавьте следующий код для импорта пространств имен `Microsoft.Scripting.Hosting` и `IronPython.Hosting` из библиотек IronPython и пространства имен `System.Linq`.

    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/Program.vb#1)]

1. В методе Main добавьте следующий код, чтобы создать объект `Microsoft.Scripting.Hosting.ScriptRuntime`, в котором будут размещены библиотеки IronPython. Объект `ScriptRuntime` загружает модуль библиотеки IronPython random.py.

     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/Program.vb#2)]

1. После указания в коде необходимости загрузки модуля random.py добавьте следующий код, чтобы создать массив целых чисел. Массив передается методу `shuffle` модуля random.py, который произвольно сортирует значения в массиве.

     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/Program.vb#3)]

1. Сохраните файл и нажмите клавиши <kbd>CTRL</kdb>+<kbd>F5</kbd> для сборки и запуска приложения.

## <a name="see-also"></a>См. также

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [Использование типа dynamic](./using-type-dynamic.md)
- [Раннее и позднее связывание](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Реализация динамических интерфейсов (документ в формате PDF на сайте Microsoft TechNet)](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
