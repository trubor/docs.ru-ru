---
title: Объявления импорта. Ключевое слово open
description: 'Сведения об объявлениях импорта F # и о том, как они указывают модуль или пространство имен, на элементы которых можно ссылаться без использования полного имени.'
ms.date: 08/15/2020
ms.openlocfilehash: 4d3fd159aa4b334e9db0d7f756047470ad9c0829
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739689"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="926a3-103">Объявления импорта: `open` ключевое слово</span><span class="sxs-lookup"><span data-stu-id="926a3-103">Import declarations: The `open` keyword</span></span>

<span data-ttu-id="926a3-104">В *объявлении импорта* указан модуль или пространство имен, элементы которого можно ссылаться без использования полного имени.</span><span class="sxs-lookup"><span data-stu-id="926a3-104">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="926a3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="926a3-105">Syntax</span></span>

```fsharp
open module-or-namespace-name
open type type-name
```

## <a name="remarks"></a><span data-ttu-id="926a3-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="926a3-106">Remarks</span></span>

<span data-ttu-id="926a3-107">Создание ссылки на код с помощью полного пространства имен или пути к модулю каждый раз может создать код, который трудно писать, читать и обслуживать.</span><span class="sxs-lookup"><span data-stu-id="926a3-107">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="926a3-108">Вместо этого можно использовать `open` ключевое слово для часто используемых модулей и пространств имен, чтобы при ссылке на член этого модуля или пространства имен можно было использовать краткую форму имени вместо полного имени.</span><span class="sxs-lookup"><span data-stu-id="926a3-108">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="926a3-109">Это ключевое слово похоже на `using` ключевое слово в C#, `using namespace` в Visual C++ и `Imports` в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="926a3-109">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="926a3-110">Предоставленный модуль или пространство имен должен находиться в том же проекте или в проекте или сборке, на которую имеется ссылка.</span><span class="sxs-lookup"><span data-stu-id="926a3-110">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="926a3-111">Если это не так, можно добавить ссылку на проект или использовать `-reference` параметр командной строки (или его сокращение `-r` ).</span><span class="sxs-lookup"><span data-stu-id="926a3-111">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="926a3-112">Дополнительные сведения см. в разделе [параметры компилятора](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="926a3-112">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="926a3-113">Объявление импорта делает имена доступными в коде, который следует за объявлением, вплоть до конца включающего пространства имен, модуля или файла.</span><span class="sxs-lookup"><span data-stu-id="926a3-113">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="926a3-114">При использовании нескольких объявлений импорта они должны отображаться в разных строках.</span><span class="sxs-lookup"><span data-stu-id="926a3-114">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="926a3-115">В следующем коде показано использование `open` ключевого слова для упрощения кода.</span><span class="sxs-lookup"><span data-stu-id="926a3-115">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="926a3-116">Компилятор F # не выдает ошибку или предупреждение, если неоднозначность возникает, когда одно и то же имя встречается в нескольких открытых модулях или пространствах имен.</span><span class="sxs-lookup"><span data-stu-id="926a3-116">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="926a3-117">При возникновении неоднозначности F # дает предпочтение более последнему открытому модулю или пространству имен.</span><span class="sxs-lookup"><span data-stu-id="926a3-117">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="926a3-118">Например, в следующем коде `empty` это означает, что, несмотря на то, что находится `Seq.empty` `empty` в `List` обоих `Seq` модулях и.</span><span class="sxs-lookup"><span data-stu-id="926a3-118">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn %"{empty}"
```

<span data-ttu-id="926a3-119">Поэтому будьте внимательны при открытии модулей или пространств имен, таких как `List` или `Seq` , которые содержат элементы с одинаковыми именами. вместо этого рекомендуется использовать полные имена.</span><span class="sxs-lookup"><span data-stu-id="926a3-119">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="926a3-120">Следует избегать ситуаций, в которых код зависит от порядка объявлений импорта.</span><span class="sxs-lookup"><span data-stu-id="926a3-120">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="open-type-declarations"></a><span data-ttu-id="926a3-121">Открытые объявления типов</span><span class="sxs-lookup"><span data-stu-id="926a3-121">Open type declarations</span></span>

<span data-ttu-id="926a3-122">F # поддерживает `open` для типа следующим образом:</span><span class="sxs-lookup"><span data-stu-id="926a3-122">F# supports `open` on a type like so:</span></span>

```fsharp
open type System.Math
PI
```

<span data-ttu-id="926a3-123">Это обеспечит доступ ко всем доступным статическим полям и элементам типа.</span><span class="sxs-lookup"><span data-stu-id="926a3-123">This will expose all accessible static fields and members on the type.</span></span>

<span data-ttu-id="926a3-124">`open`Для предоставления статических членов можно также использовать F # с определенными типами [записей](records.md) и [размеченных объединений](discriminated-unions.md) .</span><span class="sxs-lookup"><span data-stu-id="926a3-124">You can also `open` F#-defined [record](records.md) and [discriminated union](discriminated-unions.md) types to expose static members.</span></span> <span data-ttu-id="926a3-125">В случае размеченных объединений можно также предоставить варианты объединения.</span><span class="sxs-lookup"><span data-stu-id="926a3-125">In the case of discriminated unions, you can also expose the union cases.</span></span> <span data-ttu-id="926a3-126">Это может быть полезно для доступа к вариантам объединения в типе, объявленном внутри модуля, который вы не хотите открывать, например так:</span><span class="sxs-lookup"><span data-stu-id="926a3-126">This can be helpful for accessing union cases in a type declared inside of a module that you may not want to open, like so:</span></span>

```fsharp
module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="926a3-127">Пространства имен, открытые по умолчанию</span><span class="sxs-lookup"><span data-stu-id="926a3-127">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="926a3-128">Некоторые пространства имен часто используются в коде F #, поэтому они открыты неявно без необходимости явного объявления импорта.</span><span class="sxs-lookup"><span data-stu-id="926a3-128">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="926a3-129">В следующей таблице показаны пространства имен, открытые по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="926a3-129">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="926a3-130">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="926a3-130">Namespace</span></span>|<span data-ttu-id="926a3-131">Описание</span><span class="sxs-lookup"><span data-stu-id="926a3-131">Description</span></span>|
|---------|-----------|
|`FSharp.Core`|<span data-ttu-id="926a3-132">Содержит основные определения типов F # для встроенных типов, таких как `int` и `float` .</span><span class="sxs-lookup"><span data-stu-id="926a3-132">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`FSharp.Core.Operators`|<span data-ttu-id="926a3-133">Содержит базовые арифметические операции, такие как `+` и `*` .</span><span class="sxs-lookup"><span data-stu-id="926a3-133">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`FSharp.Collections`|<span data-ttu-id="926a3-134">Содержит неизменяемые классы коллекций, такие как `List` и `Array` .</span><span class="sxs-lookup"><span data-stu-id="926a3-134">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`FSharp.Control`|<span data-ttu-id="926a3-135">Содержит типы для конструкций элементов управления, таких как отложенная оценка и асинхронные рабочие процессы.</span><span class="sxs-lookup"><span data-stu-id="926a3-135">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`FSharp.Text`|<span data-ttu-id="926a3-136">Содержит функции для форматированного ввода-вывода, например `printf` функции.</span><span class="sxs-lookup"><span data-stu-id="926a3-136">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="926a3-137">Атрибут Автооткрытия</span><span class="sxs-lookup"><span data-stu-id="926a3-137">AutoOpen Attribute</span></span>

<span data-ttu-id="926a3-138">Атрибут можно применить `AutoOpen` к сборке, если необходимо автоматически открывать пространство имен или модуль при ссылке на сборку.</span><span class="sxs-lookup"><span data-stu-id="926a3-138">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="926a3-139">Можно также применить `AutoOpen` атрибут к модулю для автоматического открытия этого модуля при открытии родительского модуля или пространства имен.</span><span class="sxs-lookup"><span data-stu-id="926a3-139">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="926a3-140">Дополнительные сведения см. в разделе [AutoOpenAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html).</span><span class="sxs-lookup"><span data-stu-id="926a3-140">For more information, see [AutoOpenAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="926a3-141">Атрибут Рекуирекуалифиедакцесс</span><span class="sxs-lookup"><span data-stu-id="926a3-141">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="926a3-142">Некоторые модули, записи или типы объединений могут задавать `RequireQualifiedAccess` атрибут.</span><span class="sxs-lookup"><span data-stu-id="926a3-142">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="926a3-143">При ссылке на элементы этих модулей, записей или объединений необходимо использовать полное имя независимо от того, включено ли объявление импорта.</span><span class="sxs-lookup"><span data-stu-id="926a3-143">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="926a3-144">Если этот атрибут используется стратегически для типов, определяющих часто используемые имена, можно избежать конфликтов имен и, таким образом, сделать код более устойчивым к изменениям в библиотеках.</span><span class="sxs-lookup"><span data-stu-id="926a3-144">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="926a3-145">Дополнительные сведения см. в разделе [рекуирекуалифиедакцессаттрибуте](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html).</span><span class="sxs-lookup"><span data-stu-id="926a3-145">For more information, see [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="926a3-146">См. также</span><span class="sxs-lookup"><span data-stu-id="926a3-146">See also</span></span>

- [<span data-ttu-id="926a3-147">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="926a3-147">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="926a3-148">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="926a3-148">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="926a3-149">Модули</span><span class="sxs-lookup"><span data-stu-id="926a3-149">Modules</span></span>](modules.md)
