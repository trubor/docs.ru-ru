---
title: Параметры обрезки
description: Узнайте, как управлять обрезкой автономных приложений.
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: 93fee991cf218a52ad1d9a2597b1c9b2d442110a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874255"
---
# <a name="trimming-options"></a>Параметры обрезки

Следующие свойства и элементы MSBuild влияют на поведение [обрезанных автономных развертываний](trim-self-contained.md). Некоторые параметры упоминают `ILLink`, то есть имя базового инструмента, реализующего обрезку. Дополнительные сведения о базовом средстве можно найти в [документации по компоновщику](https://github.com/mono/linker/tree/master/docs).

## <a name="enable-trimming"></a>Включение обрезки

- `<PublishTrimmed>true</PublishTrimmed>`

   Включите обрезку во время публикации с параметрами по умолчанию, определенными пакетом SDK.

При использовании `Microsoft.NET.Sdk` выполняется обрезка сборок платформы из пакета среды выполнения netcoreapp на уровне сборки. Код приложения и библиотеки, отличные от платформы, не обрезаются. Другие пакеты SDK могут определять разные значения по умолчанию.

## <a name="trimming-granularity"></a>Степень детализации обрезки

Следующие параметры степени детализации управляют тем, насколько агрессивно отбрасываются неиспользуемые IL. Это можно задать как свойство или как метаданные в [отдельной сборке](#trimmed-assemblies).

- `<TrimMode>copyused</TrimMode>`

   Включите функцию обрезки на уровне сборки, которая сохранит всю сборку, если какая-либо ее часть используется (статически понятным образом).

- `<TrimMode>link</TrimMode>`

    Включите функцию обрезки на уровне элементов, которая удаляет неиспользуемые элементы из типов.

Сборки с метаданными `<IsTrimmable>true</IsTrimmable>`, но без явного `TrimMode` будут использовать глобальную `TrimMode`. `TrimMode` по умолчанию для `Microsoft.NET.Sdk` — `copyused`.

## <a name="trimmed-assemblies"></a>Обрезанные сборки

При публикации обрезанного приложения пакет SDK выдает `ItemGroup` с именем `ManagedAssemblyToLink`, который представляет набор файлов для обработки обрезки. `ManagedAssemblyToLink` может иметь метаданные, управляющие поведением обрезки для каждой сборки. Чтобы задать эти метаданные, создайте целевой объект, выполняемый перед встроенным целевым объектом `PrepareForILLink`. В следующем примере показано, как включить обрезку `MyAssembly`.

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

Не добавляйте и не удаляйте элементы в `ManagedAssemblyToLink`, так как пакет SDK рассчитывает этот набор во время публикации и полагает, что он не изменяется. Поддерживаются следующие метаданные.

- `<IsTrimmable>true</IsTrimmable>`

  Управление тем, обрезана ли данная сборка.

- `<TrimMode>copyused</TrimMode>` или `<TrimMode>link</TrimMode>`

  Управление [степенью детализации](#trimming-granularity) этой сборки. Имеет приоритет над глобальным `TrimMode`. Установка `TrimMode` для сборки подразумевает `<IsTrimmable>true</IsTrimmable>`.

## <a name="root-assemblies"></a>Корневые сборки

Все сборки без `<IsTrimmable>true</IsTrimmable>` считаются корневыми для анализа. Это означает, что они будут сохранены со всеми своими статически понятными зависимостями. Дополнительные сборки могут быть корневыми по имени (без расширения `.dll`).

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a>Корневые дескрипторы

Другой способ указания корней для анализа — использование XML-файла, в котором используется компоновщик [формата дескриптора](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format). Это позволяет использовать корневые члены вместо целой сборки.

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

Например, `MyRoots.xml` может быть корневым для конкретного метода, к которому приложение обращается динамически.

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a>Предупреждения при анализе

Обрезка приведет к удалению IL, который не является статически достижимым. Приложения, использующие отражение или другие шаблоны, которые создают динамические зависимости, могут быть разорваны путем обрезки. Чтобы получать предупреждения об этих шаблонах, выполните следующие действия.

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    Включите предупреждения при анализе обрезки.

Сюда будут включены предупреждения обо всем приложении, включая собственный код, код библиотеки и код платформы.

## <a name="warning-versions"></a>Версии предупреждений

При анализе обрезки учитывается свойство [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel), которое управляет версией предупреждений при анализе для пакета SDK. Существует еще одно свойство, которое управляет версией предупреждений при анализе обрезки независимо (аналогично `WarningLevel` для компилятора).

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    Настройте отображение только предупреждений заданного или нижнего уровня. Это может быть `9999` для включения всех версий предупреждений.

## <a name="suppressing-warnings"></a>Подавление предупреждений

Отдельные [коды предупреждений](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) можно подавлять с помощью стандартных свойств MSBuild, которые учитываются цепочкой инструментов, включая `NoWarn`, `WarningsAsErrors`, `WarningsNotAsErrors` и `TreatWarningsAsErrors`. Существует дополнительный параметр, который управляет поведением предупреждения как ошибки ILLink отдельно.

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    Не обрабатывайте предупреждения ILLink как ошибки. Это может быть полезно, чтобы не включать предупреждения при анализе обрезки в ошибки при обработке предупреждений компилятора как ошибок в глобальном масштабе.

## <a name="removing-symbols"></a>Удаление символов

Символы, как правило, усекаются, чтобы соответствовать обрезанным сборкам. Можно также удалить все символы.

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    Удалите символы из обрезанного приложения, включая внедренные PDB-файлы и отдельные PDB. Это относится как к коду приложения, так и к любым зависимостям, которые входят в состав символов.

Пакет SDK также позволяет отключить поддержку отладчика, используя свойство `DebuggerSupport`. Если поддержка отладчика отключена, то при обрезке символы автоматически удаляются (`TrimmerRemoveSymbols` по умолчанию принимает значение true).

## <a name="trimming-framework-library-features"></a>Усечение функций библиотеки инфраструктуры

Несколько функциональных возможностей библиотек платформы поставляются с директивами компоновщика, которые позволяют удалить код для отключенных функций.

- `<DebuggerSupport>false</DebuggerSupport>`

    Удалите код, обеспечивающий лучшую отладку. Это также приведет к [удалению символов](#removing-symbols).

- `<EnableUnsafeBinaryFormatterSerialization>false</EnableUnsafeBinaryFormatterSerialization>`

    Удалите поддержку сериализации BinaryFormatter. Дополнительные сведения см. в разделе [Методы сериализации BinaryFormatter устарели](../compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete.md).

- `<EnableUnsafeUTF7Encoding>false</EnableUnsafeUTF7Encoding>`

    Удалите небезопасный код кодировки UTF-7. Дополнительные сведения см. в разделе [Пути к коду в кодировке UTF-7 устарели](../compatibility/core-libraries/5.0/utf-7-code-paths-obsolete.md).

- `<EventSourceSupport>false</EventSourceSupport>`

    Удалите код или логику, связанную с EventSource.

- `<HttpActivityPropagationSupport>false</HttpActivityPropagationSupport>`

    Удалите код, связанный с поддержкой диагностики для System.Net.Http.

- `<InvariantGlobalization>true</InvariantGlobalization>`

    Удалите код и данные, связанные с глобализацией. Дополнительные сведения см. в разделе [Инвариантный режим](../run-time-config/globalization.md#invariant-mode).

- `<UseSystemResourceKeys>true</UseSystemResourceKeys>`

    Удалите сообщения об исключениях для сборок `System.*`. При возникновении исключения из сборки `System.*` сообщение будет содержать упрощенный идентификатор ресурса вместо полного сообщения.

 Эти свойства приведут к усечению связанного кода, а также к отключению функций через файл [runtimeconfig](../run-time-config/index.md). Дополнительные сведения об этих свойствах, включая соответствующие параметры runtimeconfig, см. в разделе, посвященном [переключению функций](https://github.com/dotnet/runtime/blob/main/docs/workflow/trimming/feature-switches.md). Некоторые пакеты SDK могут иметь значения по умолчанию для этих свойств.
