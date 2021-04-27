---
title: Выполнение выборочных модульных тестов
description: Как использовать выражения фильтра для выполнения выборочных модульных тестов с помощью команды dotnet test в .NET Core.
author: smadala
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.topic: reference
ms.openlocfilehash: 7f072952c6200e10602ec476b5d075819044fc5a
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740947"
---
# <a name="run-selective-unit-tests"></a>Выполнение выборочных модульных тестов

Использовать выражения фильтра для выполнения выборочных модульных тестов можно с помощью команды [`dotnet test`](../tools/dotnet-test.md) в .NET Core. В этой статье показано, как отфильтровывать модульные тесты для выполнения. В следующих примерах используется `dotnet test`. Если вы используете `vstest.console.exe`, замените `--filter` на `--testcasefilter:`.

## <a name="character-escaping"></a>Экранирование символов

Чтобы в `!` использовать фильтры, содержащие восклицательный знак (`*nix`), требуется выполнять экранирование, так как символ `!` зарезервирован. Например, такой фильтр пропускает все тесты, если пространство имен содержит IntegrationTests:

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> Обратная косая черта добавляется перед восклицательным знаком, чтобы экранировать его как escape-символ `\!`.

Для значений `FullyQualifiedName`, включающих запятую для параметров универсального типа, необходимо экранировать запятую с помощью `%2C`. Пример:

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

:::zone pivot="mstest"

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod, Priority(1), TestCategory("CategoryA")]
        public void TestMethod1()
        {
        }

        [TestMethod, Priority(2)]
        public void TestMethod2()
        {
        }
    }
}
```

| Выражение | Результат |
|--|--|
| `dotnet test --filter Method` | Выполняет тесты, <xref:System.Reflection.Module.FullyQualifiedName> которых содержит `Method`. Доступно в `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Выполняет тесты, имя которых содержит `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Выполняет тесты, которые находятся в классе `MSTestNamespace.UnitTest1`.<br>**Примечание.** Значение `ClassName` должно иметь пространство имен, поэтому `ClassName=UnitTest1` не будет работать. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Выполняет все тесты, за исключением `MSTestNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Выполняет тесты, которые помечены атрибутом `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Выполняет тесты, которые помечены атрибутом `[Priority(2)]`. |

Примеры использования условных операторов `|` и `&`:

Выполняет тесты, у которых есть `UnitTest1` в <xref:System.Reflection.Module.FullyQualifiedName> **или** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> является `"CategoryA"`.

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

Выполняет тесты, у которых есть `UnitTest1` в <xref:System.Reflection.Module.FullyQualifiedName> **и** есть <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> со значением `"CategoryA"`.

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

Выполняет тесты, у которых есть <xref:System.Reflection.Module.FullyQualifiedName> с `UnitTest1` **и** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> с `"CategoryA"` **или** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> с приоритетом `1`.

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="xunit"

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Fact, Trait("Priority", "1"), Trait("Category", "CategoryA")]
        public void Test1()
        {
        }

        [Fact, Trait("Priority", "2")]
        public void Test2()
        {
        }
    }
}
```

| Выражение | Результат |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Выполняет только один тест — `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Выполняет все тесты, за исключением `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Выполняет тесты, отображаемое имя которых содержит `TestClass1`. |

В примере кода определенные характеристики с ключами `"Category"` и `"Priority"` можно использовать для фильтрации.

| Выражение | Результат |
|--|--|
| `dotnet test --filter XUnit` | Выполняет тесты, <xref:System.Reflection.Module.FullyQualifiedName> которых содержит `XUnit`.  Доступно в `vstest 15.1+`. |
| `dotnet test --filter Category=CategoryA` | Выполняет тесты с `[Trait("Category", "CategoryA")]`. |

Примеры использования условных операторов `|` и `&`:

Выполняет тесты, у которых есть `TestClass1` в <xref:System.Reflection.Module.FullyQualifiedName> **или** есть `Trait` с ключом `"Category"` и значением `"CategoryA"`.

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

Выполняет тесты, у которых есть `TestClass1` в <xref:System.Reflection.Module.FullyQualifiedName> **и** есть `Trait` с ключом `"Category"` и значением `"CategoryA"`.

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

Выполняет тесты, у которых есть либо <xref:System.Reflection.Module.FullyQualifiedName> с `TestClass1` **и** есть `Trait` с ключом `"Category"` и значением `"CategoryA"` **или** у которых есть `Trait` с ключом `"Priority"` и значением `1`.

```dotnetcli
dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="nunit"

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Test, Property("Priority", 1), Category("CategoryA")]
        public void TestMethod1()
        {
        }

        [Test, Property("Priority", 2)]
        public void TestMethod2()
        {
        }
    }
}
```

| Выражение | Результат |
|--|--|
| `dotnet test --filter Method` | Выполняет тесты, <xref:System.Reflection.Module.FullyQualifiedName> которых содержит `Method`. Доступно в `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Выполняет тесты, имя которых содержит `TestMethod1`. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Выполняет тесты, которые находятся в классе `NUnitNamespace.UnitTest1`. |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Выполняет все тесты, за исключением `NUnitNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Выполняет тесты, которые помечены атрибутом `[Category("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Выполняет тесты, которые помечены атрибутом `[Priority(2)]`. |

Примеры использования условных операторов `|` и `&`:

Выполняет тесты, у которых есть `UnitTest1` в <xref:System.Reflection.Module.FullyQualifiedName> **или** есть `Category` со значением `"CategoryA"`.

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

Выполняет тесты, у которых есть `UnitTest1` в <xref:System.Reflection.Module.FullyQualifiedName> **и** есть `Category` со значением `"CategoryA"`.

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

Выполняет тесты, у которых есть <xref:System.Reflection.Module.FullyQualifiedName> с `UnitTest1` **и** `Category` с `"CategoryA"` **или** есть `Property`, где `"Priority"` имеет значение `1`.

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

Дополнительные сведения см. в документе о [фильтре TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

:::zone-end

## <a name="see-also"></a>См. также

- [dotnet test](../tools/dotnet-test.md)
- [dotnet test --filter](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Упорядочение модульных тестов](order-unit-tests.md)
