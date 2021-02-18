---
description: 'Дополнительные сведения: -optioncompare'
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: 9be4867c75cc16a8f699cf492dc41e9d08b96495
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475933"
---
# <a name="-optioncompare"></a><span data-ttu-id="36660-103">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="36660-103">-optioncompare</span></span>

<span data-ttu-id="36660-104">Задает способ сравнения строк.</span><span class="sxs-lookup"><span data-stu-id="36660-104">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="36660-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="36660-105">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="36660-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="36660-106">Remarks</span></span>

<span data-ttu-id="36660-107">Вы можете определить `-optioncompare` в одной из двух форм: `-optioncompare:binary`, чтобы использовать сравнения двоичных строк, и `-optioncompare:text`, чтобы использовать сравнения текстовых строк.</span><span class="sxs-lookup"><span data-stu-id="36660-107">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="36660-108">По умолчанию компилятор использует `-optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="36660-108">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="36660-109">В Microsoft Windows текущая кодовая страница определяет порядок сортировки двоичных строк.</span><span class="sxs-lookup"><span data-stu-id="36660-109">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="36660-110">Типичный порядок сортировки двоичных строк выглядит так:</span><span class="sxs-lookup"><span data-stu-id="36660-110">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="36660-111">Сравнение текстовых строк основано на порядке сортировки текста без учета регистра, что определяется языковым стандартом системы.</span><span class="sxs-lookup"><span data-stu-id="36660-111">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="36660-112">Типичный порядок сортировки текстовых строк выглядит так:</span><span class="sxs-lookup"><span data-stu-id="36660-112">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="36660-113">Чтобы определить параметр -optioncompare в среде Visual Studio IDE, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="36660-113">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="36660-114">Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="36660-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="36660-115">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="36660-115">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="36660-116">Откройте вкладку **Компиляция**.</span><span class="sxs-lookup"><span data-stu-id="36660-116">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="36660-117">Измените значение поля **Сравнение параметров**.</span><span class="sxs-lookup"><span data-stu-id="36660-117">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="36660-118">Чтобы определить параметр-optioncompare программными средствами, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="36660-118">To set -optioncompare programmatically</span></span>

<span data-ttu-id="36660-119">См. сведения об [операторе Option Compare](../../language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="36660-119">See [Option Compare Statement](../../language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="36660-120">Пример</span><span class="sxs-lookup"><span data-stu-id="36660-120">Example</span></span>

<span data-ttu-id="36660-121">Следующий код компилирует `ProjFile.vb` и использует сравнение двоичных строк.</span><span class="sxs-lookup"><span data-stu-id="36660-121">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="36660-122">См. также</span><span class="sxs-lookup"><span data-stu-id="36660-122">See also</span></span>

- [<span data-ttu-id="36660-123">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="36660-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="36660-124">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="36660-124">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="36660-125">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="36660-125">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="36660-126">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="36660-126">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="36660-127">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="36660-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="36660-128">Оператор Option Compare</span><span class="sxs-lookup"><span data-stu-id="36660-128">Option Compare Statement</span></span>](../../language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="36660-129">Страница "Параметры Visual Basic по умолчанию", папка "Проекты", диалоговое окно "Параметры"</span><span class="sxs-lookup"><span data-stu-id="36660-129">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
