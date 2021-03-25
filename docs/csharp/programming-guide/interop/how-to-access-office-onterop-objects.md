---
title: Руководство по программированию на C#. Получение доступа к объектам взаимодействия
description: Узнайте о возможностях C#, которые упрощают доступ к объектам API Office. Используйте новые возможности для написания кода, который создает и отображает лист Excel.
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: 6c2c49a9fd55c406b69c02586a9b0e4a1d16ccd4
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479924"
---
# <a name="how-to-access-office-interop-objects-c-programming-guide"></a>Руководство по программированию на C#. Получение доступа к объектам взаимодействия

В C# предусмотрены функции, которые упрощают доступ к объектам API Office. К новым функциям относятся именованные и необязательные аргументы, новый тип `dynamic`, а также возможность передавать аргументы ссылочным параметрам в методах COM, как если бы они были параметрами значений.

В этом разделе с использованием новых функций будет написан код, который создает и отображает лист Microsoft Office Excel. После этого будет написан код для добавления документа Office Word, который содержит значок, ссылающийся на лист Excel.

Для выполнения данного пошагового руководства на компьютере должны быть установлены Microsoft Office Excel 2007 и Microsoft Office Word 2007 или более поздние версии продуктов.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Создание нового проекта консольного приложения

1. Запустите Visual Studio.

2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**. Откроется диалоговое окно **Новый проект** .

3. В области **Установленные шаблоны** разверните узел **Visual C#** и выберите **Windows**.

4. В верхней части диалогового окна **Новый проект** в качестве целевой платформы необходимо выбрать **.NET Framework 4** (или более позднюю версию).

5. В области **Шаблоны** щелкните **Консольное приложение**.

6. Введите имя проекта в поле **Имя**.

7. Нажмите кнопку **ОК**.

     В **обозревателе решений** появится новый проект.

## <a name="to-add-references"></a>Добавление ссылок

1. В **обозревателе решений** щелкните имя проекта правой кнопкой мыши и выберите пункт **Добавить ссылку**. Откроется диалоговое окно **Добавление ссылки**.

2. На странице **Сборки** в списке **Имя компонента** выберите **Microsoft.Office.Interop.Word**, а затем, удерживая нажатой клавишу CTRL, выберите **Microsoft.Office.Interop.Excel**.  Если сборки отсутствуют, может потребоваться проверить, что они установлены и отображаются. См. практическое руководство по [ установке основных сборок взаимодействия Microsoft Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).

3. Нажмите кнопку **ОК**.

## <a name="to-add-necessary-using-directives"></a>Добавление необходимых директив using

1. В **обозревателе решений** щелкните правой кнопкой мыши файл *Program.cs* и выберите пункт **Просмотреть код**.

2. В начало файла кода добавьте следующие директивы `using`:

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a>Создание списка банковских счетов

1. Вставьте следующее определение класса в файл **Program.cs** в класс `Program`.

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. Чтобы создать список `bankAccounts`, содержащий два счета, добавьте в метод `Main` следующий код.

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Объявление метода, экспортирующего сведения о счетах в Excel

1. Чтобы настроить лист Excel, добавьте в класс `Program` следующий метод.

     У метода <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> есть необязательный параметр для указания конкретного шаблона. Для необязательных параметров, впервые появившихся в C# 4, можно опускать аргумент, если нужно использовать значение параметра по умолчанию. Поскольку в следующем коде никакой аргумент не передается, в методе `Add` используется шаблон по умолчанию и создается новая книга. В эквивалентном операторе в более ранних версиях C# необходимо было использовать аргумент-местозаполнитель `ExcelApp.Workbooks.Add(Type.Missing)`.

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. Добавьте в конец метода `DisplayInExcel` следующий код. Этот код вставляет значения в первые два столбца первой строки листа.

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. Добавьте в конец метода `DisplayInExcel` следующий код. Цикл `foreach` помещает сведения из списка счетов в первые два столбца последовательных строк листа.

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. Добавьте в конец метода `DisplayInExcel` следующий код, чтобы ширина столбца изменялась в соответствии с содержимым.

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     В более ранних версиях C# требовалось явное приведение типов для этих операций, поскольку `ExcelApp.Columns[1]` возвращает тип `Object`, а метод `AutoFit` является методом Excel <xref:Microsoft.Office.Interop.Excel.Range>. Приведение показано в следующих строках.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     C# 4 и более поздних версий преобразует возвращаемое значение `Object` в `dynamic` автоматически, если ссылка на сборку задана с помощью параметра компилятора [**EmbedInteropTypes**](../../language-reference/compiler-options/inputs.md#embedinteroptypes) или, что эквивалентно, если свойство Excel **Внедрить типы взаимодействия** имеет значение true. True является значением по умолчанию для этого свойства.

## <a name="to-run-the-project"></a>Запуск проекта

1. Добавьте в конец метода `Main` следующую строку.

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. Нажмите клавиши CTRL+F5.

     Появится книга Excel, содержащая данные о двух счетах.

## <a name="to-add-a-word-document"></a>Добавление документа Word

1. Чтобы продемонстрировать дополнительные способы, совершенствующие программирование для Office в C# 4 и более поздних версиях, следующий код открывает приложение Word и создает значок со ссылкой на лист Excel.

     Вставьте метод `CreateIconInWordDoc`, указанный далее в этом шаге, в класс `Program`. `CreateIconInWordDoc` использует именованные и необязательные аргументы, чтобы упростить вызовы методов <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> и <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>. В этих вызовах используются две новые возможности, появившиеся в C# 4, которые упрощают вызовы к методам COM, имеющим ссылочные параметры. Во-первых, аргументы можно передать в ссылочные параметры, как если бы они были параметрами значений. Это значит, что значения можно передавать напрямую без создания переменной для каждого ссылочного параметра. Компилятор создает временные переменные для хранения значений аргументов и уничтожает эти переменные после завершения вызываемого метода. Во-вторых, ключевое слово `ref` в списке аргументов можно опустить.

     У метода `Add` имеется четыре ссылочных параметра, все из которых являются необязательными. В C# 4.0 или более поздних версиях вы можете опустить аргументы для любого или для всех параметров, если требуется использовать значения по умолчанию. В C# 3.0 и более ранних версиях необходимо было указывать аргумент для каждого из параметров, и этот аргумент должен был быть переменной, поскольку параметры являются ссылочными.

     Метод `PasteSpecial` вставляет содержимое буфера обмена. У метода имеется семь ссылочных параметров, все из которых являются необязательными. Следующий код задает аргументы для двух из них: `Link` для создания ссылки на исходное содержимое буфера и `DisplayAsIcon` для отображения ссылки в виде значка. В C# 4.0 и более поздних версиях можно использовать именованные аргументы для этих двух параметров и опустить остальные аргументы. Хотя эти параметры являются ссылочными, использовать ключевое слово `ref` или создавать переменные для передачи аргументов не требуется. Значения можно передать напрямую. В C# 3.0 и более ранних версиях необходимо было передавать аргумент в виде переменной для каждого ссылочного параметра.

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     В C# 3.0 и более ранних версиях приходилось использовать следующий более сложный синтаксис.

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. Добавьте в конец метода `Main` следующую инструкцию.

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. Добавьте в конец метода `DisplayInExcel` следующую инструкцию. Метод `Copy` добавляет лист в буфер обмена.

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. Нажмите клавиши CTRL+F5.

     Появится документ Word, содержащий значок. Дважды щелкните значок, чтобы отобразить лист на переднем плане.

## <a name="to-set-the-embed-interop-types-property"></a>Задание свойства "Внедрить типы взаимодействия"

1. При вызове типа COM, который не требует во время выполнения основной сборки взаимодействия (PIA), можно использовать дополнительные усовершенствования. Избавление от зависимостей от PIA приводит к независимости версий и делает развертывание более простым. Дополнительные сведения о преимуществах программирования без основных сборок взаимодействия см. в руководстве по [ внедрению типов из управляемых сборок](../../../standard/assembly/embed-types-visual-studio.md).

     Кроме того, писать программы стало проще, поскольку типы, принимаемые и возвращаемые методами COM, можно представить с помощью типа `dynamic` вместо типа `Object`. Переменные типа `dynamic` не вычисляются до времени выполнения, что позволяет обходиться без явного приведения. Дополнительные сведения см. в разделе [Использование типа dynamic](../types/using-type-dynamic.md).

     В C# 4 внедрение сведений о типах вместо использования сборок PIA является поведением по умолчанию. За счет этого несколько приведенных выше примеров становятся проще, поскольку явное приведение не требуется. Например, объявление `worksheet` в методе `DisplayInExcel` записывается как `Excel._Worksheet workSheet = excelApp.ActiveSheet`, а не как `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`. Для вызовов `AutoFit` в рамках одного метода также требовалось бы явное приведение без поведения по умолчанию, поскольку `ExcelApp.Columns[1]` возвращает тип `Object`, а `AutoFit` является методом Excel. Приведение показано в следующем примере.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. Чтобы изменить поведение по умолчанию и использовать сборки PIA вместо внедрения сведений о типе, разверните узел **Ссылки** в **обозревателе решений** и выберите **Microsoft.Office.Interop.Excel** или **Microsoft.Office.Interop.Word**.

3. Если окно **Свойства** не отображается, нажмите клавишу **F4**.

4. В списке свойств найдите свойство **Внедрить типы взаимодействия** и измените его значение на **False**. Также можно выполнить компиляцию с помощью командной строки с использованием параметра компилятора [**References**](../../language-reference/compiler-options/inputs.md#references) вместо [**EmbedInteropTypes**](../../language-reference/compiler-options/inputs.md#embedinteroptypes).

## <a name="to-add-additional-formatting-to-the-table"></a>Дополнительное форматирование таблицы

1. Замените два вызова `AutoFit` в методе `DisplayInExcel` следующей инструкцией.

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     У метода <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> имеется семь параметров значений, и все они являются необязательными. Именованные и необязательные аргументы позволяют задать аргументы для всех параметров, их части или ни для одного параметра. В приведенной выше инструкции аргумент задается только для одного из параметров, `Format`. Поскольку `Format` является первым параметром в списке, имя параметра указывать не требуется. Однако инструкция может быть проще для понимания, если указать имя параметра, как показано в следующем фрагменте кода.

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. Нажмите сочетание клавиш CTRL + F5, чтобы увидеть результат. Другие форматы представлены в перечислении <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat>.

3. Сравните инструкцию в шаге 1 со следующим кодом, в котором показаны аргументы, необходимые в C# 3.0 или более ранних версиях.

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a>Пример

Ниже приведен полный пример кода.

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a>См. также

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Использование типа dynamic](../types/using-type-dynamic.md)
- [Именованные и необязательные аргументы](../classes-and-structs/named-and-optional-arguments.md)
- [Использование именованных и необязательных аргументов в программировании приложений Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
