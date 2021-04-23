---
title: Типы критических изменений
description: Узнайте, как .NET пытается обеспечить совместимость для разработчиков в разных версиях .NET и какого рода изменения рассматриваются как критические.
ms.date: 01/28/2021
ms.topic: conceptual
ms.openlocfilehash: 5814aa03d89cde086c4f055f36def77d4405be6f
ms.sourcegitcommit: 178ccefa8c454bfae844ce12ed222a54913df157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2021
ms.locfileid: "107883258"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="d7c4c-103">Изменения, влияющие на совместимость</span><span class="sxs-lookup"><span data-stu-id="d7c4c-103">Changes that affect compatibility</span></span>

<span data-ttu-id="d7c4c-104">На протяжении всей истории своего развития в .NET по возможности поддерживался высокий уровень совместимости между версиями и вариантами этой платформы.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across implementations of .NET.</span></span> <span data-ttu-id="d7c4c-105">Хотя .NET 5 (и .NET Core) и более поздних версий можно считать новой технологией в сравнении с платформой .NET Framework, возможность независимого от .NET Framework развития данной реализации .NET ограничивается следующими двумя факторами.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-105">Although .NET 5 (and .NET Core) and later versions can be considered as a new technology compared to .NET Framework, two major factors limit the ability of this implementation of .NET to diverge from .NET Framework:</span></span>

- <span data-ttu-id="d7c4c-106">Большое количество разработчиков разрабатывали ранее и продолжают разрабатывать приложения для .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-106">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="d7c4c-107">Все они рассчитывают на согласованное поведение разных реализаций .NET.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-107">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="d7c4c-108">Проекты библиотек .NET Standard позволяют разработчикам создавать библиотеки для распространенных API, которые совместно используются в .NET Framework и .NET 5 (и .NET Core) и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-108">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Framework and .NET 5 (and .NET Core) and later versions.</span></span> <span data-ttu-id="d7c4c-109">Разработчики ожидают, что библиотеки из приложения .NET 5 будут вести себя точно так же, как аналогичные библиотеки в приложении .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-109">Developers expect that a library used in a .NET 5 application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="d7c4c-110">Кроме совместимости разных реализаций .NET, разработчики также ожидают высокий уровень совместимости между версиями данной реализации .NET.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-110">Along with compatibility across .NET implementations, developers expect a high level of compatibility across versions of a given implementation of .NET.</span></span> <span data-ttu-id="d7c4c-111">В частности, код, написанный для более ранней версии .NET Core, должен без проблем работать в .NET 5 и любой последующей версии.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-111">In particular, code written for an earlier version of .NET Core should run seamlessly on .NET 5 or a later version.</span></span> <span data-ttu-id="d7c4c-112">Более того, многие разработчики ожидают, что новые API в свежих версиях .NET будут также совместимы с предварительными версиями, в которых впервые появились эти API.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-112">In fact, many developers expect that the new APIs found in newly released versions of .NET should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="d7c4c-113">Эта статья описывает, какие изменения связаны с совместимостью и каким образом каждый тип изменений анализируется командой создателей .NET.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-113">This article outlines changes that affect compatibility and the way in which the .NET team evaluates each type of change.</span></span> <span data-ttu-id="d7c4c-114">Узнать о подходах создателей .NET к внедрению потенциальных критических изменений будет особенно полезно разработчикам, которые открывают запросы на вытягивание, изменяющие работу [существующих API .NET](https://github.com/dotnet/runtime).</span><span class="sxs-lookup"><span data-stu-id="d7c4c-114">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests that modify the behavior of [existing .NET APIs](https://github.com/dotnet/runtime).</span></span>

<span data-ttu-id="d7c4c-115">В следующих разделах описываются категории изменений, внесенных в API .NET, и их влияние на совместимость приложений.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-115">The following sections describe the categories of changes made to .NET APIs and their impact on application compatibility.</span></span> <span data-ttu-id="d7c4c-116">Изменения могут быть разрешены (✔️), запрещены (❌) или требовать оценки предсказуемости и очевидности, а также согласованности таких изменений с прежним поведением.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-116">Changes are either allowed ✔️, disallowed ❌, or require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was ❓.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="d7c4c-117">Эти критерии не только разъясняют оценку изменений в библиотеках .NET, но и могут помочь разработчикам оценивать изменения в собственных библиотеках, предназначенных для различных реализаций и версий .NET.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-117">In addition to serving as a guide to how changes to .NET libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>
> - <span data-ttu-id="d7c4c-118">Категории совместимости, например обратная и с будущими версиями, описаны в статье [Совместимость](categories.md).</span><span class="sxs-lookup"><span data-stu-id="d7c4c-118">For information about the compatibility categories, for example, forward and backwards compatibility, see [Compatibility](categories.md).</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="d7c4c-119">Изменения в открытом контракте</span><span class="sxs-lookup"><span data-stu-id="d7c4c-119">Modifications to the public contract</span></span>

<span data-ttu-id="d7c4c-120">Изменения в этой категории изменяют общую контактную зону для типа.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-120">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="d7c4c-121">Большинство изменений в этой категории запрещены, так как они нарушают *обратную совместимость* (возможность выполнять приложения, разработанные для предыдущих версий API, без повторной компиляции для более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="d7c4c-121">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="d7c4c-122">Типы</span><span class="sxs-lookup"><span data-stu-id="d7c4c-122">Types</span></span>

- <span data-ttu-id="d7c4c-123">✔️ **РАЗРЕШЕНО. Удаление реализации интерфейса из типа, если этот интерфейс уже реализован в базовом типе**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-123">✔️ **ALLOWED: Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="d7c4c-124">❓ **ТРЕБУЕТСЯ ОЦЕНКА. Добавление новой реализации интерфейса в тип**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-124">❓ **REQUIRES JUDGMENT: Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="d7c4c-125">Это допустимое изменение, так как оно не сказывается отрицательно на существующих клиентах.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-125">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="d7c4c-126">Чтобы новая реализация оставалась допустимой, любые изменения типа должны выполняться в пределах допустимых изменений, которые определены здесь.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-126">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="d7c4c-127">Следует соблюдать предельную осторожность при добавлении интерфейсов, которые напрямую влияют на способность конструктора или сериализатора создавать код или данные, которые нельзя использовать на нижнем уровне.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-127">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="d7c4c-128">Пример — интерфейс <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-128">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="d7c4c-129">❓ **ТРЕБУЕТСЯ ОЦЕНКА. Добавление нового базового класса**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-129">❓ **REQUIRES JUDGMENT: Introducing a new base class**</span></span>

  <span data-ttu-id="d7c4c-130">Тип можно включать в иерархию между двумя существующими типами, если он не включает новые [абстрактные](../../csharp/language-reference/keywords/abstract.md) элементы и не изменяет семантику или поведение существующих типов.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-130">A type can be introduced into a hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="d7c4c-131">Например, в .NET Framework 2.0 класс <xref:System.Data.Common.DbConnection> стал новым базовым классом для <xref:System.Data.SqlClient.SqlConnection> с наследованием напрямую от <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-131">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="d7c4c-132">✔️ **РАЗРЕШЕНО. Перемещение типа из одной сборки в другую**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-132">✔️ **ALLOWED: Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="d7c4c-133">*Старой* сборке следует присвоить метку <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>, указывающую на новую сборку.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-133">The *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="d7c4c-134">✔️ **РАЗРЕШЕНО. Изменение типа [struct](../../csharp/language-reference/builtin-types/struct.md) на тип `readonly struct`**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-134">✔️ **ALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="d7c4c-135">Изменение типа `readonly struct` на тип `struct` запрещено.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-135">Changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="d7c4c-136">✔️ **РАЗРЕШЕНО. Добавление ключевых слов [sealed](../../csharp/language-reference/keywords/sealed.md) или [abstract](../../csharp/language-reference/keywords/abstract.md) к типу, в котором нет *доступных* конструкторов (открытых или защищенных)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-136">✔️ **ALLOWED: Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="d7c4c-137">✔️ **РАЗРЕШЕНО. Расширение видимости типа**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-137">✔️ **ALLOWED: Expanding the visibility of a type**</span></span>

- <span data-ttu-id="d7c4c-138">❌ **ЗАПРЕЩЕНО. Изменение пространства имен или имени типа**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-138">❌ **DISALLOWED: Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="d7c4c-139">❌ **ЗАПРЕЩЕНО. Переименование или удаление открытого типа**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-139">❌ **DISALLOWED: Renaming or removing a public type**</span></span>

   <span data-ttu-id="d7c4c-140">Это изменение нарушает весь код, в котором использовался переименованный или удаленный тип.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-140">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="d7c4c-141">❌ **ЗАПРЕЩЕНО. Изменение базового типа для перечисления**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-141">❌ **DISALLOWED: Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="d7c4c-142">Это критическое изменение нарушает процесс компиляции и поведение приложения, а также совместимость на двоичном уровне вплоть до невозможности анализировать аргументы атрибутов.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-142">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="d7c4c-143">❌ **ЗАПРЕЩЕНО. Запечатывание типа, который ранее был незапечатанным**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-143">❌ **DISALLOWED: Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="d7c4c-144">❌ **ЗАПРЕЩЕНО. Добавление интерфейса в набор базовых типов интерфейса**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-144">❌ **DISALLOWED: Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="d7c4c-145">Если интерфейс реализует другой интерфейс, который ранее не был в нем реализован, нарушаются все типы, которые реализовали исходную версию этого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-145">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="d7c4c-146">❓ **ТРЕБУЕТСЯ ОЦЕНКА. Удаление класса из набора базовых классов или интерфейса из набора реализованных интерфейсов**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-146">❓ **REQUIRES JUDGMENT: Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="d7c4c-147">Есть одно исключение из правила удаления интерфейса: вы можете добавить реализацию интерфейса, наследуемую от удаленного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-147">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="d7c4c-148">Например, можно удалить <xref:System.IDisposable>, если тип или интерфейс теперь реализуют <xref:System.ComponentModel.IComponent> с реализацией <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-148">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="d7c4c-149">❌ **ЗАПРЕЩЕНО. Изменение типа `readonly struct` на тип [struct](../../csharp/language-reference/builtin-types/struct.md)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-149">❌ **DISALLOWED: Changing a `readonly struct` type to a [struct](../../csharp/language-reference/builtin-types/struct.md) type**</span></span>

  <span data-ttu-id="d7c4c-150">Обратите внимание, что изменение типа `struct` на тип `readonly struct` разрешено.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-150">The change of a `struct` type to a `readonly struct` type is allowed, however.</span></span>

- <span data-ttu-id="d7c4c-151">❌ **ЗАПРЕЩЕНО. Изменение типа [struct](../../csharp/language-reference/builtin-types/struct.md) на тип `ref struct` и наоборот**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-151">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="d7c4c-152">❌ **ЗАПРЕЩЕНО. Снижение видимости типа**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-152">❌ **DISALLOWED: Reducing the visibility of a type**</span></span>

   <span data-ttu-id="d7c4c-153">При этом увеличение видимости типа разрешено.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-153">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="d7c4c-154">Участники</span><span class="sxs-lookup"><span data-stu-id="d7c4c-154">Members</span></span>

- <span data-ttu-id="d7c4c-155">✔️ **РАЗРЕШЕНО. Расширение видимости для элемента, который не является [виртуальным](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-155">✔️ **ALLOWED: Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="d7c4c-156">✔️ **РАЗРЕШЕНО. Добавление абстрактного элемента в открытый тип без *доступных* конструкторов (открытых или защищенных) или в [запечатанный тип](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-156">✔️ **ALLOWED: Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="d7c4c-157">При этом добавление абстрактного элемента в тип с доступными конструкторами (открытыми или защищенными) и в незапечатанный тип (`sealed`) разрешено.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-157">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="d7c4c-158">✔️ **РАЗРЕШЕНО. Ограничение видимости [защищенного](../../csharp/language-reference/keywords/protected.md) элемента, если у типа нет доступных (открытых или защищенных) конструкторов или этот тип [запечатан](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-158">✔️ **ALLOWED: Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="d7c4c-159">✔️ **РАЗРЕШЕНО. Перемещение элемента в класс, расположенный в иерархии выше типа, из которого он был удален**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-159">✔️ **ALLOWED: Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="d7c4c-160">✔️ **РАЗРЕШЕНО. Добавление или удаление переопределения**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-160">✔️ **ALLOWED: Adding or removing an override**</span></span>

  <span data-ttu-id="d7c4c-161">Добавление переопределения может привести к тому, что прежние пользователи не будут его использовать при вызове [базового](../../csharp/language-reference/keywords/base.md) типа.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-161">Introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="d7c4c-162">✔️ **РАЗРЕШЕНО. Добавление в класс конструктора одновременно с конструктором без параметров, если ранее у этого класса не было конструкторов**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-162">✔️ **ALLOWED: Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="d7c4c-163">При этом добавление конструктора в класс, ранее не имевший конструкторов, *без* добавления конструктора без параметров, не разрешено.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-163">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="d7c4c-164">✔️ **РАЗРЕШЕНО. Изменение [абстрактного](../../csharp/language-reference/keywords/abstract.md) элемента на [виртуальный](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-164">✔️ **ALLOWED: Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="d7c4c-165">✔️ **РАЗРЕШЕНО. Изменение возвращаемого значения с `ref readonly` на `ref` (за исключением виртуальных методов или интерфейсов)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-165">✔️ **ALLOWED: Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="d7c4c-166">✔️ **РАЗРЕШЕНО. Удаление из поля метки [readonly](../../csharp/language-reference/keywords/readonly.md), за исключением полей со статическим типом изменяемого значения**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-166">✔️ **ALLOWED: Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="d7c4c-167">✔️ **РАЗРЕШЕНО. Вызов нового события, которое не было определено ранее**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-167">✔️ **ALLOWED: Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="d7c4c-168">❓ **ТРЕБУЕТСЯ ОЦЕНКА. Добавление нового поля экземпляра к типу**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-168">❓ **REQUIRES JUDGMENT: Adding a new instance field to a type**</span></span>

   <span data-ttu-id="d7c4c-169">Это изменение влияет на сериализацию.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-169">This change impacts serialization.</span></span>

- <span data-ttu-id="d7c4c-170">❌ **ЗАПРЕЩЕНО. Переименование или удаление открытого типа или параметра**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-170">❌ **DISALLOWED: Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="d7c4c-171">Это изменение нарушает весь код, в котором использовался переименованный или удаленный элемент либо параметр.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-171">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="d7c4c-172">Сюда относятся удаление и переименование методов получения и определения свойств, а также элементов перечисления.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-172">This includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="d7c4c-173">❌ **ЗАПРЕЩЕНО. Добавление элемента к интерфейсу**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-173">❌ **DISALLOWED: Adding a member to an interface**</span></span>

- <span data-ttu-id="d7c4c-174">❌ **ЗАПРЕЩЕНО. Изменение значения общедоступной константы или элемента перечисления**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-174">❌ **DISALLOWED: Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="d7c4c-175">❌ **ЗАПРЕЩЕНО. Изменение типа для свойства, поля, параметра или возвращаемого значения**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-175">❌ **DISALLOWED: Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="d7c4c-176">❌ **ЗАПРЕЩЕНО. Добавление, удаление параметров или изменение их порядка**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-176">❌ **DISALLOWED: Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="d7c4c-177">❌ **ЗАПРЕЩЕНО. Добавление или удаление ключевого слова [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) или [ref](../../csharp/language-reference/keywords/ref.md) для параметра**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-177">❌ **DISALLOWED: Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="d7c4c-178">❌ **ЗАПРЕЩЕНО. Переименование параметра (в том числе изменение регистра символов)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-178">❌ **DISALLOWED: Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="d7c4c-179">Такое изменение считается критическим по двум причинам:</span><span class="sxs-lookup"><span data-stu-id="d7c4c-179">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="d7c4c-180">Оно нарушает сценарии с поздним связыванием, например функцию поздней привязки в Visual Basic и функцию [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) в C#.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-180">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="d7c4c-181">Оно нарушает [совместимость на уровне кода](categories.md#source-compatibility), если разработчик использует [именованные аргументы](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span><span class="sxs-lookup"><span data-stu-id="d7c4c-181">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="d7c4c-182">❌ **ЗАПРЕЩЕНО. Изменение возвращаемого значения с `ref` на `ref readonly`**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-182">❌ **DISALLOWED: Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="d7c4c-183">❌️ **ЗАПРЕЩЕНО. Изменение возвращаемого значения с `ref readonly` на `ref` для виртуальных методов или интерфейсов**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-183">❌️ **DISALLOWED: Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="d7c4c-184">❌ **ЗАПРЕЩЕНО. Добавление или удаление ключевого слова [abstract](../../csharp/language-reference/keywords/abstract.md) для элемента**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-184">❌ **DISALLOWED: Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="d7c4c-185">❌ **ЗАПРЕЩЕНО. Удаление ключевого слова [virtual](../../csharp/language-reference/keywords/virtual.md) для элемента**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-185">❌ **DISALLOWED: Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

- <span data-ttu-id="d7c4c-186">❌ **ЗАПРЕЩЕНО. Добавление ключевого слова [virtual](../../csharp/language-reference/keywords/virtual.md) к элементу**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-186">❌ **DISALLOWED: Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

  <span data-ttu-id="d7c4c-187">Такое изменение часто не является критическим, так как компилятор C# обычно выдает инструкции [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) на промежуточном языке (IL) для вызова невиртуальных методов (`callvirt`, в отличие об обычного кода, выполняет проверку значений null). При этом такое поведение не может считаться стабильным по следующим причинам:</span><span class="sxs-lookup"><span data-stu-id="d7c4c-187">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  
  - <span data-ttu-id="d7c4c-188">.NET используется не только с C#, но и с другими языками.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-188">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="d7c4c-189">Компилятор C# продолжает попытки оптимизировать `callvirt` в обычный вызов, если целевой метод не является виртуальным и с высокой вероятностью не имеет значения null (например, метод с доступом с использованием [оператора распространения значений null ?.](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span><span class="sxs-lookup"><span data-stu-id="d7c4c-189">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="d7c4c-190">Преобразование метода в виртуальный означает, что код объекта-получателя будет часто вызывать его не виртуально.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-190">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="d7c4c-191">❌ **ЗАПРЕЩЕНО. Преобразование виртуального элемента в абстрактный**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-191">❌ **DISALLOWED: Making a virtual member abstract**</span></span>

  <span data-ttu-id="d7c4c-192">[Виртуальный элемент](../../csharp/language-reference/keywords/virtual.md) предоставляет реализацию метода, которую *можно* переопределить производным классом.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-192">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="d7c4c-193">[Абстрактный элемент](../../csharp/language-reference/keywords/abstract.md) не предоставляет реализацию и *должен быть* переопределен.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-193">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="d7c4c-194">❌ **ЗАПРЕЩЕНО. Добавление абстрактного элемента в общедоступный тип с доступными конструкторами (открытыми или защищенными) и [незапечатанный тип](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-194">❌ **DISALLOWED: Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="d7c4c-195">❌ **ЗАПРЕЩЕНО. Добавление в элемент ключевого слова [static](../../csharp/language-reference/keywords/static.md) или его удаление**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-195">❌ **DISALLOWED: Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="d7c4c-196">❌ **ЗАПРЕЩЕНО. Добавление перегрузки, которая исключает существующую перегрузку и определяет другое поведение**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-196">❌ **DISALLOWED: Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="d7c4c-197">Такое изменение нарушает логику существующих клиентов, которые зависели от предыдущей перегрузки.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-197">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="d7c4c-198">Например, если у класса есть одна версия метода, которая принимает <xref:System.UInt32>, существующий получатель будет успешно привязан к этой перегрузке при отправке значения <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-198">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="d7c4c-199">Но если вы добавите перегрузку, которая принимает <xref:System.Int32>, при повторной компиляции или при использовании позднего связывания компилятор будет выполнять привязку к новой перегрузке.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-199">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="d7c4c-200">Любые изменения, приводящие к разным реакциям на события, считаются критическими.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-200">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="d7c4c-201">❌ **ЗАПРЕЩЕНО. Добавление конструктора в класс, ранее не имевший конструкторов, без добавления конструктора без параметров**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-201">❌ **DISALLOWED: Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="d7c4c-202">❌️ **ЗАПРЕЩЕНО. Добавление ключевого слова [readonly](../../csharp/language-reference/keywords/readonly.md) в поле**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-202">❌️ **DISALLOWED: Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="d7c4c-203">❌ **ЗАПРЕЩЕНО. Снижение видимости элемента**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-203">❌ **DISALLOWED: Reducing the visibility of a member**</span></span>

   <span data-ttu-id="d7c4c-204">Сюда входит ограничение видимости [защищенного](../../csharp/language-reference/keywords/protected.md) элемента, если имеются *доступные* (`public` или `protected`) конструкторы, но тип *не* является [запечатанным](../../csharp/language-reference/keywords/sealed.md).</span><span class="sxs-lookup"><span data-stu-id="d7c4c-204">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (`public` or `protected`) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="d7c4c-205">Если это не так, снижение видимости защищенного элемента разрешено.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-205">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="d7c4c-206">Увеличение видимости типа разрешено.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-206">Increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="d7c4c-207">❌ **ЗАПРЕЩЕНО. Изменение типа элемента**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-207">❌ **DISALLOWED: Changing the type of a member**</span></span>

   <span data-ttu-id="d7c4c-208">Возвращаемое значение метода или типа свойства или поля изменить нельзя.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-208">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="d7c4c-209">Например, сигнатуру метода, который возвращает <xref:System.Object>, нельзя изменить так, чтобы он возвращал <xref:System.String>, или наоборот.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-209">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="d7c4c-210">❌ **ЗАПРЕЩЕНО. Добавление поля к структуре, у которой ранее не было состояний**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-210">❌ **DISALLOWED: Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="d7c4c-211">Правила определенного назначения допускают использование неинициализированных переменных, если переменная имеет тип структуры без отслеживания состояния.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-211">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="d7c4c-212">Если этой структуре добавить отслеживание состояния, код может получить неинициализированные данные.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-212">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="d7c4c-213">Такое изменение может быть критическим на уровне источника и двоичного кода.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-213">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="d7c4c-214">❌ **ЗАПРЕЩЕНО. Вызов существующего события, которое ранее никогда не срабатывало**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-214">❌ **DISALLOWED: Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="d7c4c-215">Изменения поведения</span><span class="sxs-lookup"><span data-stu-id="d7c4c-215">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="d7c4c-216">Сборки</span><span class="sxs-lookup"><span data-stu-id="d7c4c-216">Assemblies</span></span>

- <span data-ttu-id="d7c4c-217">✔️ **РАЗРЕШЕНО. Преобразование сборки в переносимую при сохранении поддержки тех же платформ**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-217">✔️ **ALLOWED: Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="d7c4c-218">❌ **ЗАПРЕЩЕНО. Изменение имени сборки**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-218">❌ **DISALLOWED: Changing the name of an assembly**</span></span>
- <span data-ttu-id="d7c4c-219">❌ **ЗАПРЕЩЕНО. Изменение открытого ключа сборки**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-219">❌ **DISALLOWED: Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="d7c4c-220">Свойства, поля, параметры и возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7c4c-220">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="d7c4c-221">✔️ **РАЗРЕШЕНО. Изменение значения для свойства, поля, возвращаемого значения или параметра [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) на более производный тип**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-221">✔️ **ALLOWED: Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="d7c4c-222">Например, метод, возвращающий тип <xref:System.Object>, может возвращать экземпляр <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-222">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="d7c4c-223">(Но при этом сигнатура метода не должна изменяться.)</span><span class="sxs-lookup"><span data-stu-id="d7c4c-223">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="d7c4c-224">✔️ **РАЗРЕШЕНО. Увеличение диапазона допустимых значений для свойства или параметра, если элемент не является [виртуальным](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-224">✔️ **ALLOWED: Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="d7c4c-225">Можно расширять диапазон значений, которые передаются методу или возвращаются из него, но нельзя расширять тип параметра или элемента.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-225">While the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="d7c4c-226">Например, диапазон передаваемых методу значений можно расширить с 0–124 до 0–255, но нельзя изменить тип параметра с <xref:System.Byte> на <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-226">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="d7c4c-227">❌ **ЗАПРЕЩЕНО. Увеличение диапазона допустимых значений для свойства или параметра, если элемент является [виртуальным](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-227">❌ **DISALLOWED: Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="d7c4c-228">Такое изменение нарушает существующие переопределенные элементы, которые не будут правильно работать с расширенным диапазоном значений.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-228">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="d7c4c-229">❌ **ЗАПРЕЩЕНО. Уменьшение диапазона допустимых значений для свойства или параметра**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-229">❌ **DISALLOWED: Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="d7c4c-230">❌ **ЗАПРЕЩЕНО. Увеличение диапазона допустимых значений для свойства, поля, возвращаемого значения или параметра [out](../../csharp/language-reference/keywords/out-parameter-modifier.md)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-230">❌ **DISALLOWED: Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="d7c4c-231">❌ **ЗАПРЕЩЕНО. Изменение возвращаемых значений для свойства, поля, возвращаемого значения метода или параметра [out](../../csharp/language-reference/keywords/out-parameter-modifier.md)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-231">❌ **DISALLOWED: Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="d7c4c-232">❌ **ЗАПРЕЩЕНО. Изменение значения по умолчанию для свойства, поля или параметра**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-232">❌ **DISALLOWED: Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="d7c4c-233">❌ **ЗАПРЕЩЕНО. Изменение точности числового возвращаемого значения**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-233">❌ **DISALLOWED: Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="d7c4c-234">❓ **ТРЕБУЕТСЯ ОЦЕНКА. Изменение логики синтаксического анализа входных данных и создание новых исключений (даже если поведение синтаксического анализа не указано в документации**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-234">❓ **REQUIRES JUDGMENT: A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="d7c4c-235">Исключения</span><span class="sxs-lookup"><span data-stu-id="d7c4c-235">Exceptions</span></span>

- <span data-ttu-id="d7c4c-236">✔️ **РАЗРЕШЕНО. Вызов более производного исключения, чем существующие исключения**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-236">✔️ **ALLOWED: Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="d7c4c-237">Так как новое исключение является подклассом существующего исключения, существующий код обработки исключений будет обрабатывать это исключение.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-237">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="d7c4c-238">Например, в .NET Framework 4 методы создания и получения языка и региональных параметров теперь вызывают исключение <xref:System.Globalization.CultureNotFoundException> вместо <xref:System.ArgumentException>, если не могут найти язык и региональные параметры.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-238">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="d7c4c-239">Так как <xref:System.Globalization.CultureNotFoundException> является производным от <xref:System.ArgumentException>, это изменение считается допустимым.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-239">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="d7c4c-240">✔️ **РАЗРЕШЕНО. Вызов более конкретного исключения, чем <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-240">✔️ **ALLOWED: Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="d7c4c-241">✔️ **РАЗРЕШЕНО. Вызов исключения, которое считается неустранимым**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-241">✔️ **ALLOWED: Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="d7c4c-242">Неустранимые исключения не нужно перехватывать, они попадают в обработчик catch-all на верхнем уровне.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-242">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="d7c4c-243">Это означает, что у пользователей нет кода, который перехватывает эти явные исключения.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-243">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="d7c4c-244">Неустранимыми считаются следующие исключения:</span><span class="sxs-lookup"><span data-stu-id="d7c4c-244">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="d7c4c-245">✔️ **РАЗРЕШЕНО. Вызов нового исключения в новом пути кода**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-245">✔️ **ALLOWED: Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="d7c4c-246">Исключения должны применяться только к новому пути кода, который выполняется с новыми значениями параметров или состоянием и который невозможно выполнить в существующем коде, ориентированном на предыдущую версию.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-246">The exception must apply only to a new code-path that's executed with new parameter values or state and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="d7c4c-247">✔️ **РАЗРЕШЕНО. Удаление исключения для более надежной работы или для нового сценария**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-247">✔️ **ALLOWED: Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="d7c4c-248">Например, метод `Divide`, который ранее обрабатывал только положительные значения и вызвал исключение <xref:System.ArgumentOutOfRangeException>, можно изменить так, чтобы он поддерживал положительные и отрицательные значения без вызова исключения.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-248">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="d7c4c-249">✔️ **РАЗРЕШЕНО. Изменение текста сообщения об ошибке**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-249">✔️ **ALLOWED: Changing the text of an error message**</span></span>

  <span data-ttu-id="d7c4c-250">Разработчикам не следует полагаться на текст сообщения об ошибках, который изменяется еще и в зависимости от языка и региональных параметров пользователя.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-250">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="d7c4c-251">❌ **ЗАПРЕЩЕНО. Вызов исключения в любом случае, кроме перечисленных выше**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-251">❌ **DISALLOWED: Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="d7c4c-252">❌ **ЗАПРЕЩЕНО. Удаление исключения в любом случае, кроме перечисленных выше**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-252">❌ **DISALLOWED: Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="d7c4c-253">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d7c4c-253">Attributes</span></span>

- <span data-ttu-id="d7c4c-254">✔️ **РАЗРЕШЕНО. Изменение значения атрибута, который *не* является наблюдаемым**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-254">✔️ **ALLOWED: Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="d7c4c-255">❌ **ЗАПРЕЩЕНО. Изменение значения атрибута, который *является* наблюдаемым**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-255">❌ **DISALLOWED: Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="d7c4c-256">❓ **ТРЕБУЕТСЯ ОЦЕНКА. Удаление атрибута**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-256">❓ **REQUIRES JUDGMENT: Removing an attribute**</span></span>

  <span data-ttu-id="d7c4c-257">В большинстве случаев удаление атрибута (например, <xref:System.NonSerializedAttribute>) является критическим изменением.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-257">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="d7c4c-258">Поддержка платформ</span><span class="sxs-lookup"><span data-stu-id="d7c4c-258">Platform support</span></span>

- <span data-ttu-id="d7c4c-259">✔️ **РАЗРЕШЕНО. Поддержка операции для платформы, которая ранее не поддерживалась**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-259">✔️ **ALLOWED: Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="d7c4c-260">❌ **ЗАПРЕЩЕНО. Прекращение поддержки или требование конкретного пакета обновления для операции, которая ранее поддерживалась для платформы**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-260">❌ **DISALLOWED: Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="d7c4c-261">Изменения внутренней реализации</span><span class="sxs-lookup"><span data-stu-id="d7c4c-261">Internal implementation changes</span></span>

- <span data-ttu-id="d7c4c-262">❓ **ТРЕБУЕТСЯ ОЦЕНКА. Изменение контактной зоны внутреннего типа**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-262">❓ **REQUIRES JUDGMENT: Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="d7c4c-263">Такие изменения обычно разрешены, хотя они изменяют закрытое отражение.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-263">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="d7c4c-264">Эти изменения могут быть не разрешены в некоторых случаях, если популярные сторонние библиотеки или большое количество разработчиков полагаются на внутренние API.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-264">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="d7c4c-265">❓ **ТРЕБУЕТСЯ ОЦЕНКА. Изменение внутренней реализации элемента**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-265">❓ **REQUIRES JUDGMENT: Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="d7c4c-266">Такие изменения обычно разрешены, хотя они изменяют закрытое отражение.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-266">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="d7c4c-267">Эти изменения могут быть не разрешены в некоторых случаях, если код клиента часто зависит от закрытого отражения или если изменения связаны с нежелательными побочными эффектами.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-267">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="d7c4c-268">✔️ **РАЗРЕШЕНО. Повышение производительности операции**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-268">✔️ **ALLOWED: Improving the performance of an operation**</span></span>

   <span data-ttu-id="d7c4c-269">Возможность изменять производительность операции очень важна, но такие изменения могут нарушить код, который зависит от текущей скорости операции.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-269">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="d7c4c-270">Это особенно важно для кода, который зависит от скорости выполнения асинхронных операций.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-270">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="d7c4c-271">Изменение производительности не должно влиять на другие аспекты поведения API, в противном случае изменение будет считаться критическим.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-271">The performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="d7c4c-272">✔️ **РАЗРЕШЕНО. Косвенное (и обычно отрицательное) изменение производительности операции**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-272">✔️ **ALLOWED: Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="d7c4c-273">Если изменение не относится к категории критических по другим причинам, оно считается допустимым.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-273">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="d7c4c-274">Зачастую требуются дополнительные действия, включая дополнительные операции или операции, которые добавляют новые функции.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-274">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="d7c4c-275">Это почти всегда влияет на производительность, но может требоваться для правильной работы API.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-275">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="d7c4c-276">❌ **ЗАПРЕЩЕНО. Преобразование синхронного API в асинхронный (и наоборот)**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-276">❌ **DISALLOWED: Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="d7c4c-277">Изменения кода</span><span class="sxs-lookup"><span data-stu-id="d7c4c-277">Code changes</span></span>

- <span data-ttu-id="d7c4c-278">✔️ **РАЗРЕШЕНО. Добавление [params](../../csharp/language-reference/keywords/params.md) в параметр**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-278">✔️ **ALLOWED: Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="d7c4c-279">❌ **ЗАПРЕЩЕНО. Замена [структуры](../../csharp/language-reference/builtin-types/struct.md) на [класс](../../csharp/language-reference/keywords/class.md) и наоборот**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-279">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="d7c4c-280">❌ **ЗАПРЕЩЕНО. Добавление ключевого слова [checked](../../csharp/language-reference/keywords/virtual.md) в блок кода**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-280">❌ **DISALLOWED: Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="d7c4c-281">Такое изменение может привести к тому, что ранее правильно выполнявшийся код будет вызывать исключение <xref:System.OverflowException>, что является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-281">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="d7c4c-282">❌ **ЗАПРЕЩЕНО. Удаление [params](../../csharp/language-reference/keywords/params.md) из параметра**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-282">❌ **DISALLOWED: Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="d7c4c-283">❌ **ЗАПРЕЩЕНО. Изменение порядка возникновения событий**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-283">❌ **DISALLOWED: Changing the order in which events are fired**</span></span>

  <span data-ttu-id="d7c4c-284">Разработчики могут рассчитывать на то, что события будут срабатывать в определенном порядке, и создаваемый ими код часто зависит от этого порядка.</span><span class="sxs-lookup"><span data-stu-id="d7c4c-284">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="d7c4c-285">❌ **ЗАПРЕЩЕНО. Удаление вызова события для конкретного действия**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-285">❌ **DISALLOWED: Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="d7c4c-286">❌ **ЗАПРЕЩЕНО. Изменение количества вызовов определенных событий**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-286">❌ **DISALLOWED: Changing the number of times given events are called**</span></span>

- <span data-ttu-id="d7c4c-287">❌ **ЗАПРЕЩЕНО. Добавление <xref:System.FlagsAttribute> к типу перечисления**</span><span class="sxs-lookup"><span data-stu-id="d7c4c-287">❌ **DISALLOWED: Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
