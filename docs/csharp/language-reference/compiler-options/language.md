---
description: Параметры компилятора C# для правил языковых функций. Эти параметры определяют способ интерпретации компилятором определенных языковых конструкций.
title: Параметры компилятора C# — правила языковых функций
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- CheckForOverflowUnderflow compiler option [C#]
- AllowUnsafeBlocks compiler option [C#]
- DefineConstants compiler option [C#]
- LangVersion compiler option [C#]
- Nullable compiler option [C#]
ms.openlocfilehash: fe3b7b8c06aa86e406757feb7635a5e9ca1032e9
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637030"
---
# <a name="c-compiler-options-for-language-feature-rules"></a>Параметры компилятора C# для правил языковых функций

Следующие параметры определяют, как компилятор интерпретирует языковые функции. Новый синтаксис MSBuild выделен **полужирным шрифтом**. Для старого синтаксиса *csc.exe* используется формат `code style`.

- **CheckForOverflowUnderflow** / `-checked`: создание проверок на переполнение.
- **AllowUnsafeBlocks** / `-unsafe`: разрешение использовать небезопасный код.
- **DefineConstants** / `-define`: определение символов условной компиляции.
- **LangVersion** / `-langversion`: указание версии языка, например `default` (последняя основная версия) или `latest` (последняя версия, включая дополнительные версии).
- **Nullable** / `-nullable`: включение контекста, допускающего значение NULL, или предупреждений, допускающих значение NULL.

## <a name="checkforoverflowunderflow"></a>CheckForOverflowUnderflow

Параметр **CheckForOverflowUnderflow** указывает, будет ли использование целочисленного арифметического оператора, в результате выполнения которого получено значение, выходящее за установленный для определенного типа данных диапазон значений, приводить к возникновению исключения во время выполнения.  

```xml
<CheckForOverflowUnderflow>true</CheckForOverflowUnderflow>
```

Действие параметра **CheckForOverflowUnderflow** не распространяется на целочисленный арифметический оператор, находящийся в области действия ключевых слов `checked` или `unchecked`. Если в результате выполнения целочисленного арифметического оператора, находящегося за пределами области действия ключевых слов `checked` или `unchecked`, получено значение, выходящее за установленный для определенного типа данных диапазон значений, и для параметра **CheckForOverflowUnderflow** установлено значение `true`, во время выполнения возникнет исключение из-за этого оператора. Если параметр **CheckForOverflowUnderflow** имеет значение `false`, использование такого оператора не приводит к возникновению исключения во время выполнения. Значение этого параметра по умолчанию — `false`; проверка переполнения отключена.

## <a name="allowunsafeblocks"></a>AllowUnsafeBlocks

Параметр **AllowUnsafeBlocks** разрешает компилировать код, в котором используется ключевое слово [unsafe](../keywords/unsafe.md). Значение по умолчанию для этого параметра — `false`, то есть использование небезопасного кода запрещено.

```xml
<AllowUnsafeBlocks>true</AllowUnsafeBlocks>
```

Дополнительные сведения см. в разделе [Небезопасный код и указатели](../../programming-guide/unsafe-code-pointers/index.md).

## <a name="defineconstants"></a>DefineConstants

Параметр **DefineConstants** определяет символы в файлах исходного кода вашей программы.

```xml
<DefineConstants>name;name2</DefineConstants>
```

Этот параметр задает имена одного или нескольких символов, которые необходимо определить. Параметр **DefineConstants** действует так же, как директива препроцессора [#define](../preprocessor-directives.md#defining-symbols), но применяется ко всем файлам проекта. Символ остается определенным в файле исходного кода до тех пор, пока определение не будет отменено с помощью директивы [#undef](../preprocessor-directives.md#defining-symbols) в файле исходного кода. При использовании параметра `-define` директива `#undef` в одном файле не действует для других файлов исходного кода в проекте. Вы можете использовать символы, созданные этим параметром, с директивами [#if](../preprocessor-directives.md#conditional-compilation), [#else](../preprocessor-directives.md), [#elif](../preprocessor-directives.md#conditional-compilation) и [#endif](../preprocessor-directives.md#conditional-compilation) для условной компиляции исходных файлов. Компилятор C# сам по себе не определяет символы и макросы, которые можно использовать в исходном коде. Все такие определения задаются пользователем.

> [!NOTE]
> Директива C# `#define` не поддерживает присваивание значения символу, как, например, в языке C++. Например, с помощью директивы `#define` нельзя создать макрос или определить константу. Чтобы определить константу, используйте переменную `enum`. Для создания макросов в стиле C++ необходимо использовать альтернативные способы, например универсальные шаблоны. Поскольку макросы по своей природе подвержены ошибкам, в C# они запрещены, однако вместо них предлагаются более безопасные альтернативы.

## <a name="langversion"></a>LangVersion

Инструктирует компилятор принимать только синтаксис, включенный в заданную спецификацию языка C#.

```xml
<LangVersion>9.0</LangVersion>
```

Допустимы следующие значения.

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

Версия языка по умолчанию зависит от целевой платформы приложения, а также от установленной версии пакета SDK или Visual Studio. Такие правила определены в статье [Управление версиями языка C#](../configure-language-version.md#defaults).

Параметр компилятора **LangVersion** не влияет на метаданные, на которые ссылается ваше приложение C#.

Так как каждая версия компилятора C# содержит расширения для спецификации языка, параметр **LangVersion** не позволяет использовать возможности, аналогичные возможностям более ранней версии компилятора.

Кроме того, в отличие от обновлений версии C#, которые обычно совпадают с основными выпусками .NET Framework, новые функции и возможности синтаксиса могут быть не привязаны к конкретной версии этой платформы. Для работы с новыми версиями требуется обновление компилятора, которое также выпускается с новой редакцией C#. Тем не менее для каждой функции определен собственный набор минимальных требований к API .NET или общеязыковой среде выполнения, в результате чего их можно выполнять на более ранних версиях платформы, добавив необходимые пакеты NuGet или другие библиотеки.

Независимо от того, какой параметр **LangVersion** вы задали, используйте для создания файлов с расширением .exe или .dll. текущую версию среды CLR. Единственным исключением являются дружественные сборки и [**ModuleAssemblyName**](advanced.md#moduleassemblyname), которые работают при установке параметра **-langversion:ISO-1**.

Другие способы указания версии языка C# см. в статье [Управление версиями языка C#](../configure-language-version.md).

Дополнительные сведения об установке этого параметра компилятора программным путем см. в разделе <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.

### <a name="c-language-specification"></a>Спецификация языка C#

| Version          | Ссылка                       | Описание                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| C# 7.0 и более поздние версии |                            | В настоящее время недоступно.                                                 |
| C# 6.0           | [Ссылка][csharp-6]           | Спецификация языка C# версии 6 (неофициальный проект): .NET Foundation |
| C# 5.0           | [Загрузить PDF-файл][csharp-5]   | Стандарт ECMA-334, 5-й выпуск                                           |
| C# 3.0           | [Загрузить DOC-файл][csharp-3]   | Спецификация языка C#, версия 3.0: Microsoft Corporation            |
| C# 2.0           | [Загрузить PDF-файл][csharp-2]   | Стандарт ECMA-334, 4-й выпуск                                           |
| C# 1.2           | [Загрузить DOC-файл][csharp-1.2] | Спецификация языка C#, версия 1.2: Microsoft Corporation            |
| C# 1.0           | [Загрузить DOC-файл][csharp-1]   | Спецификация языка C#, версия 1.0: Microsoft Corporation            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

### <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Минимальная версия пакета SDK, необходимая для поддержки всех возможностей языка

В следующей таблице перечислены минимальные версии пакета SDK с компилятором C#, поддерживающим соответствующую версию языка:

| Версия C# | Минимальная версия пакета SDK                                                                  |
|------------|--------------------------------------------------------------------------------------|
| C# 8.0     | Microsoft Visual Studio/Build Tools 2019, версия 16.3 или пакет SDK .NET Core 3.0         |
| C# 7.3     | Microsoft Visual Studio/Build Tools 2017, версия 15.7                               |
| C# 7.2     | Microsoft Visual Studio/Build Tools 2017, версия 15.5                               |
| C# 7.1     | Microsoft Visual Studio/Build Tools 2017, версия 15.3                               |
| C# 7.0     | Microsoft Visual Studio/Build Tools 2017                                             |
| C# 6       | Microsoft Visual Studio/Build Tools 2015                                             |
| C# 5       | Microsoft Visual Studio/Build Tools 2012 или встроенный компилятор .NET Framework 4.5      |
| C# 4       | Microsoft Visual Studio/Build Tools 2010 или встроенный компилятор .NET Framework 4.0      |
| C# 3       | Microsoft Visual Studio/Build Tools 2008 или встроенный компилятор .NET Framework 3.5      |
| C# 2       | Microsoft Visual Studio/Build Tools 2005 или встроенный компилятор .NET Framework 2.0      |
| C# 1.0/1.2 | Microsoft Visual Studio/Build Tools .NET 2002 или встроенный компилятор .NET Framework 1.0 |

## <a name="nullable"></a>Допускает значения NULL

Параметр **Nullable** позволяет указать контекст, допускающий значение NULL.

```xml
<Nullable>enable</Nullable>
```

Аргумент должен иметь одно из следующих значений: `enable`, `disable`, `warnings` или `annotations`. Аргумент `enable` разрешает контекст, допускающий значение NULL. При указании `disable` контекст, допускающий значение NULL, будет отключен. Аргумент `warnings` включает контекст предупреждения, допускающий значение NULL. При указании аргумента `annotations` будет включен контекст заметок, допускающий значение NULL.

Анализ потока используется для определения допустимости значений NULL в переменных в исполняемом коде. Выводимая допустимость переменной значения NULL не зависит от объявленной в переменной допустимости значения NULL. Вызовы методов анализируются, даже если они условно опущены. Например, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> в режиме выпуска.

Вызов методов, снабженных следующими атрибутами, также повлияет на анализ потока:

- Простые предварительные условия: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> и <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- Простые постусловия: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> и <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- Условные постусловия: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> и <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (например, `DoesNotReturnIf(false)` для <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) и <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- Постусловия элемента: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> и <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

> [!IMPORTANT]
> Глобальный контекст, допускающий значения NULL, не применяется для созданных файлов кода. Независимо от этого параметра, контекст, допускающий значение NULL, *отключен* для любого исходного файла, помеченного как созданный. Существует четыре способа пометки файла как созданного:
>
> 1. В файле. editorconfig укажите `generated_code = true` в разделе, который применяется к этому файлу.
> 1. Вставьте `<auto-generated>` или `<auto-generated/>` в комментарий в верхней части файла. Он может находиться в любой строке комментария, однако блок комментариев должен быть первым элементом в файле.
> 1. Имя файла следует начинать с *TemporaryGeneratedFile_*
> 1. В конце имени файла следует указать *.designer.cs*, *.generated.cs*, *.g.cs* или *.g.i.cs*.
>
> Генераторы могут явно использовать директиву препроцессора [`#nullable`](../preprocessor-directives.md#nullable-context).
