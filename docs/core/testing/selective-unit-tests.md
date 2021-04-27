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
# <a name="run-selective-unit-tests"></a><span data-ttu-id="fa19c-103">Выполнение выборочных модульных тестов</span><span class="sxs-lookup"><span data-stu-id="fa19c-103">Run selective unit tests</span></span>

<span data-ttu-id="fa19c-104">Использовать выражения фильтра для выполнения выборочных модульных тестов можно с помощью команды [`dotnet test`](../tools/dotnet-test.md) в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fa19c-104">With the [`dotnet test`](../tools/dotnet-test.md) command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="fa19c-105">В этой статье показано, как отфильтровывать модульные тесты для выполнения.</span><span class="sxs-lookup"><span data-stu-id="fa19c-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="fa19c-106">В следующих примерах используется `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="fa19c-107">Если вы используете `vstest.console.exe`, замените `--filter` на `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="fa19c-108">Экранирование символов</span><span class="sxs-lookup"><span data-stu-id="fa19c-108">Character escaping</span></span>

<span data-ttu-id="fa19c-109">Чтобы в `!` использовать фильтры, содержащие восклицательный знак (`*nix`), требуется выполнять экранирование, так как символ `!` зарезервирован.</span><span class="sxs-lookup"><span data-stu-id="fa19c-109">Using filters that include exclamation mark `!` on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="fa19c-110">Например, такой фильтр пропускает все тесты, если пространство имен содержит IntegrationTests:</span><span class="sxs-lookup"><span data-stu-id="fa19c-110">For example, this filter skips all tests if the namespace contains IntegrationTests:</span></span>

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> <span data-ttu-id="fa19c-111">Обратная косая черта добавляется перед восклицательным знаком, чтобы экранировать его как escape-символ `\!`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-111">The backslash precedes the exclamation mark to indicate it is an escaped character `\!`.</span></span>

<span data-ttu-id="fa19c-112">Для значений `FullyQualifiedName`, включающих запятую для параметров универсального типа, необходимо экранировать запятую с помощью `%2C`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="fa19c-113">Пример:</span><span class="sxs-lookup"><span data-stu-id="fa19c-113">For example:</span></span>

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

| <span data-ttu-id="fa19c-114">Выражение</span><span class="sxs-lookup"><span data-stu-id="fa19c-114">Expression</span></span> | <span data-ttu-id="fa19c-115">Результат</span><span class="sxs-lookup"><span data-stu-id="fa19c-115">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="fa19c-116">Выполняет тесты, <xref:System.Reflection.Module.FullyQualifiedName> которых содержит `Method`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-116">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="fa19c-117">Доступно в `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-117">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="fa19c-118">Выполняет тесты, имя которых содержит `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-118">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="fa19c-119">Выполняет тесты, которые находятся в классе `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-119">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="fa19c-120">**Примечание.** Значение `ClassName` должно иметь пространство имен, поэтому `ClassName=UnitTest1` не будет работать.</span><span class="sxs-lookup"><span data-stu-id="fa19c-120">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="fa19c-121">Выполняет все тесты, за исключением `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-121">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="fa19c-122">Выполняет тесты, которые помечены атрибутом `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-122">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="fa19c-123">Выполняет тесты, которые помечены атрибутом `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-123">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="fa19c-124">Примеры использования условных операторов `|` и `&`:</span><span class="sxs-lookup"><span data-stu-id="fa19c-124">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="fa19c-125">Выполняет тесты, у которых есть `UnitTest1` в <xref:System.Reflection.Module.FullyQualifiedName> **или** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> является `"CategoryA"`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-125">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> is `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="fa19c-126">Выполняет тесты, у которых есть `UnitTest1` в <xref:System.Reflection.Module.FullyQualifiedName> **и** есть <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> со значением `"CategoryA"`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-126">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="fa19c-127">Выполняет тесты, у которых есть <xref:System.Reflection.Module.FullyQualifiedName> с `UnitTest1` **и** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> с `"CategoryA"` **или** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> с приоритетом `1`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-127">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"` **or** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> with a priority of `1`.</span></span>

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

| <span data-ttu-id="fa19c-128">Выражение</span><span class="sxs-lookup"><span data-stu-id="fa19c-128">Expression</span></span> | <span data-ttu-id="fa19c-129">Результат</span><span class="sxs-lookup"><span data-stu-id="fa19c-129">Result</span></span> |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="fa19c-130">Выполняет только один тест — `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-130">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="fa19c-131">Выполняет все тесты, за исключением `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-131">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="fa19c-132">Выполняет тесты, отображаемое имя которых содержит `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-132">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="fa19c-133">В примере кода определенные характеристики с ключами `"Category"` и `"Priority"` можно использовать для фильтрации.</span><span class="sxs-lookup"><span data-stu-id="fa19c-133">In the code example, the defined traits with keys `"Category"` and `"Priority"` can be used for filtering.</span></span>

| <span data-ttu-id="fa19c-134">Выражение</span><span class="sxs-lookup"><span data-stu-id="fa19c-134">Expression</span></span> | <span data-ttu-id="fa19c-135">Результат</span><span class="sxs-lookup"><span data-stu-id="fa19c-135">Result</span></span> |
|--|--|
| `dotnet test --filter XUnit` | <span data-ttu-id="fa19c-136">Выполняет тесты, <xref:System.Reflection.Module.FullyQualifiedName> которых содержит `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-136">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `XUnit`.</span></span>  <span data-ttu-id="fa19c-137">Доступно в `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-137">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="fa19c-138">Выполняет тесты с `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-138">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="fa19c-139">Примеры использования условных операторов `|` и `&`:</span><span class="sxs-lookup"><span data-stu-id="fa19c-139">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="fa19c-140">Выполняет тесты, у которых есть `TestClass1` в <xref:System.Reflection.Module.FullyQualifiedName> **или** есть `Trait` с ключом `"Category"` и значением `"CategoryA"`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-140">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

<span data-ttu-id="fa19c-141">Выполняет тесты, у которых есть `TestClass1` в <xref:System.Reflection.Module.FullyQualifiedName> **и** есть `Trait` с ключом `"Category"` и значением `"CategoryA"`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-141">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

<span data-ttu-id="fa19c-142">Выполняет тесты, у которых есть либо <xref:System.Reflection.Module.FullyQualifiedName> с `TestClass1` **и** есть `Trait` с ключом `"Category"` и значением `"CategoryA"` **или** у которых есть `Trait` с ключом `"Priority"` и значением `1`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-142">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `TestClass1` **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"` **or** have a `Trait` with a key of `"Priority"` and value of `1`.</span></span>

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

| <span data-ttu-id="fa19c-143">Выражение</span><span class="sxs-lookup"><span data-stu-id="fa19c-143">Expression</span></span> | <span data-ttu-id="fa19c-144">Результат</span><span class="sxs-lookup"><span data-stu-id="fa19c-144">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="fa19c-145">Выполняет тесты, <xref:System.Reflection.Module.FullyQualifiedName> которых содержит `Method`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-145">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="fa19c-146">Доступно в `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-146">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="fa19c-147">Выполняет тесты, имя которых содержит `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-147">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="fa19c-148">Выполняет тесты, которые находятся в классе `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-148">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="fa19c-149">Выполняет все тесты, за исключением `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-149">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="fa19c-150">Выполняет тесты, которые помечены атрибутом `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-150">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="fa19c-151">Выполняет тесты, которые помечены атрибутом `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-151">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="fa19c-152">Примеры использования условных операторов `|` и `&`:</span><span class="sxs-lookup"><span data-stu-id="fa19c-152">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="fa19c-153">Выполняет тесты, у которых есть `UnitTest1` в <xref:System.Reflection.Module.FullyQualifiedName> **или** есть `Category` со значением `"CategoryA"`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-153">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="fa19c-154">Выполняет тесты, у которых есть `UnitTest1` в <xref:System.Reflection.Module.FullyQualifiedName> **и** есть `Category` со значением `"CategoryA"`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-154">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="fa19c-155">Выполняет тесты, у которых есть <xref:System.Reflection.Module.FullyQualifiedName> с `UnitTest1` **и** `Category` с `"CategoryA"` **или** есть `Property`, где `"Priority"` имеет значение `1`.</span><span class="sxs-lookup"><span data-stu-id="fa19c-155">To run tests that have either a <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a `Category` of `"CategoryA"` **or** have a `Property` with a `"Priority"` of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

<span data-ttu-id="fa19c-156">Дополнительные сведения см. в документе о [фильтре TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="fa19c-156">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

:::zone-end

## <a name="see-also"></a><span data-ttu-id="fa19c-157">См. также</span><span class="sxs-lookup"><span data-stu-id="fa19c-157">See also</span></span>

- [<span data-ttu-id="fa19c-158">dotnet test</span><span class="sxs-lookup"><span data-stu-id="fa19c-158">dotnet test</span></span>](../tools/dotnet-test.md)
- [<span data-ttu-id="fa19c-159">dotnet test --filter</span><span class="sxs-lookup"><span data-stu-id="fa19c-159">dotnet test --filter</span></span>](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a><span data-ttu-id="fa19c-160">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="fa19c-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fa19c-161">Упорядочение модульных тестов</span><span class="sxs-lookup"><span data-stu-id="fa19c-161">Order unit tests</span></span>](order-unit-tests.md)
