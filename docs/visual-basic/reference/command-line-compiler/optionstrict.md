---
description: 'Дополнительные сведения: -optionstrict'
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: ad58c7775eaa77c1bf693629cf12cc70e4222920
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475907"
---
# <a name="-optionstrict"></a><span data-ttu-id="e97db-103">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="e97db-103">-optionstrict</span></span>

<span data-ttu-id="e97db-104">Применяет строгую семантику типа, чтобы ограничить неявные преобразования типов.</span><span class="sxs-lookup"><span data-stu-id="e97db-104">Enforces strict type semantics to restrict implicit type conversions.</span></span>

## <a name="syntax"></a><span data-ttu-id="e97db-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e97db-105">Syntax</span></span>

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a><span data-ttu-id="e97db-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="e97db-106">Arguments</span></span>

<span data-ttu-id="e97db-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e97db-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="e97db-108">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e97db-108">Optional.</span></span> <span data-ttu-id="e97db-109">Параметр `-optionstrict+` ограничивает неявное преобразование типов.</span><span class="sxs-lookup"><span data-stu-id="e97db-109">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="e97db-110">Значение этого параметра по умолчанию равно `-optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="e97db-110">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="e97db-111">Параметр `-optionstrict+` совпадает с `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="e97db-111">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="e97db-112">Для нестрогой семантики типов можно использовать и тот, и другой.</span><span class="sxs-lookup"><span data-stu-id="e97db-112">You can use both for permissive type semantics.</span></span>

`custom`  
<span data-ttu-id="e97db-113">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="e97db-113">Required.</span></span> <span data-ttu-id="e97db-114">Предупреждать, когда не накладывается ограничение на строгую семантику языка.</span><span class="sxs-lookup"><span data-stu-id="e97db-114">Warn when strict language semantics are not respected.</span></span>

## <a name="remarks"></a><span data-ttu-id="e97db-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="e97db-115">Remarks</span></span>

<span data-ttu-id="e97db-116">Если применяется `-optionstrict+`, только расширяющие преобразования типов могут быть выполнены неявно.</span><span class="sxs-lookup"><span data-stu-id="e97db-116">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="e97db-117">Неявные сужающие преобразования типов, такие как назначение объекта типа `Decimal` объекту целочисленного типа, регистрируются как ошибки.</span><span class="sxs-lookup"><span data-stu-id="e97db-117">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>

<span data-ttu-id="e97db-118">Чтобы создать предупреждения для неявных сужающих преобразований типов, используйте `-optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="e97db-118">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="e97db-119">Используйте `-nowarn:numberlist`, чтобы пропускать определенные предупреждения, и `-warnaserror:numberlist`, чтобы обрабатывать определенные предупреждения как ошибки.</span><span class="sxs-lookup"><span data-stu-id="e97db-119">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="e97db-120">Порядок задания параметра -optionstrict в среде Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="e97db-120">To set -optionstrict in the Visual Studio IDE</span></span>

1. <span data-ttu-id="e97db-121">Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="e97db-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e97db-122">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="e97db-122">On the **Project** menu, click **Properties.**</span></span>

2. <span data-ttu-id="e97db-123">Откройте вкладку **Компиляция**.</span><span class="sxs-lookup"><span data-stu-id="e97db-123">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="e97db-124">Измените значение в поле **Option Strict**.</span><span class="sxs-lookup"><span data-stu-id="e97db-124">Modify the value in the **Option Strict** box.</span></span>

### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="e97db-125">Порядок задания параметра -optionstrict программным образом</span><span class="sxs-lookup"><span data-stu-id="e97db-125">To set -optionstrict programmatically</span></span>

<span data-ttu-id="e97db-126">См. раздел [Оператор Option Strict](../../language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e97db-126">See [Option Strict Statement](../../language-reference/statements/option-strict-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="e97db-127">Пример</span><span class="sxs-lookup"><span data-stu-id="e97db-127">Example</span></span>

<span data-ttu-id="e97db-128">Следующий код компилирует `Test.vb` с использованием строгой семантики типов.</span><span class="sxs-lookup"><span data-stu-id="e97db-128">The following code compiles `Test.vb` using strict type semantics.</span></span>

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a><span data-ttu-id="e97db-129">См. также</span><span class="sxs-lookup"><span data-stu-id="e97db-129">See also</span></span>

- [<span data-ttu-id="e97db-130">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="e97db-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="e97db-131">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="e97db-131">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="e97db-132">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="e97db-132">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="e97db-133">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="e97db-133">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="e97db-134">-nowarn</span><span class="sxs-lookup"><span data-stu-id="e97db-134">-nowarn</span></span>](nowarn.md)
- [<span data-ttu-id="e97db-135">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e97db-135">-warnaserror (Visual Basic)</span></span>](warnaserror.md)
- [<span data-ttu-id="e97db-136">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="e97db-136">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="e97db-137">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="e97db-137">Option Strict Statement</span></span>](../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="e97db-138">Страница "Параметры Visual Basic по умолчанию", папка "Проекты", диалоговое окно "Параметры"</span><span class="sxs-lookup"><span data-stu-id="e97db-138">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
