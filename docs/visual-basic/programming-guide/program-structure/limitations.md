---
description: 'Дополнительные сведения: ограничения Visual Basic'
title: Ограничения
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 9182c5fe475e4350cb17ed3e4b734e3924bb9f7b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432849"
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="12369-103">Ограничения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12369-103">Visual Basic Limitations</span></span>

<span data-ttu-id="12369-104">Более ранние версии Visual Basic принудительно применяют границы кода, такие как длина имен переменных, количество переменных, допустимых в модулях, и размер модуля.</span><span class="sxs-lookup"><span data-stu-id="12369-104">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="12369-105">В Visual Basic .NET эти ограничения были ослаблены, что обеспечивает большую свободу при написании и упорядочении кода.</span><span class="sxs-lookup"><span data-stu-id="12369-105">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="12369-106">Физические ограничения зависят больше от объема памяти во время выполнения, чем в вопросах времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="12369-106">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="12369-107">Если вы используете разумные методики программирования и разбиваете крупные приложения на несколько классов и модулей, то вероятность возникновения внутренних ограничений на Visual Basic невелика.</span><span class="sxs-lookup"><span data-stu-id="12369-107">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="12369-108">Ниже перечислены некоторые ограничения, которые могут возникнуть в экстремальных случаях.</span><span class="sxs-lookup"><span data-stu-id="12369-108">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
- <span data-ttu-id="12369-109">**Длина имени.**</span><span class="sxs-lookup"><span data-stu-id="12369-109">**Name Length.**</span></span> <span data-ttu-id="12369-110">Существует максимальное число символов в имени каждого объявленного программного элемента.</span><span class="sxs-lookup"><span data-stu-id="12369-110">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="12369-111">Это максимальное значение применяется ко всей уточняющей строке, если имя элемента является полным.</span><span class="sxs-lookup"><span data-stu-id="12369-111">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="12369-112">См. раздел [Declared Element Names](../language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="12369-112">See [Declared Element Names](../language-features/declared-elements/declared-element-names.md).</span></span>  
  
- <span data-ttu-id="12369-113">**Длина строки.**</span><span class="sxs-lookup"><span data-stu-id="12369-113">**Line Length.**</span></span> <span data-ttu-id="12369-114">В физической строке исходного кода содержится не более 65535 символов.</span><span class="sxs-lookup"><span data-stu-id="12369-114">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="12369-115">Логическая строка исходного кода может быть длиннее, если используются символы продолжения строки.</span><span class="sxs-lookup"><span data-stu-id="12369-115">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="12369-116">См. раздел [как разрывать и объединять операторы в коде](how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="12369-116">See [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
- <span data-ttu-id="12369-117">**Размеры массива.**</span><span class="sxs-lookup"><span data-stu-id="12369-117">**Array Dimensions.**</span></span> <span data-ttu-id="12369-118">Существует максимальное количество измерений, которые можно объявить для массива.</span><span class="sxs-lookup"><span data-stu-id="12369-118">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="12369-119">Это ограничивает количество индексов, которые можно использовать для указания элемента массива.</span><span class="sxs-lookup"><span data-stu-id="12369-119">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="12369-120">См. раздел [измерения массива в Visual Basic](../language-features/arrays/array-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="12369-120">See [Array Dimensions in Visual Basic](../language-features/arrays/array-dimensions.md).</span></span>  
  
- <span data-ttu-id="12369-121">**Длина строки.**</span><span class="sxs-lookup"><span data-stu-id="12369-121">**String Length.**</span></span> <span data-ttu-id="12369-122">Существует максимальное число символов Юникода, которые можно хранить в одной строке.</span><span class="sxs-lookup"><span data-stu-id="12369-122">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="12369-123">См. [строковый тип данных](../../language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="12369-123">See [String Data Type](../../language-reference/data-types/string-data-type.md).</span></span>  
  
- <span data-ttu-id="12369-124">**Длина строки окружения.**</span><span class="sxs-lookup"><span data-stu-id="12369-124">**Environment String Length.**</span></span> <span data-ttu-id="12369-125">Для любой строки среды, используемой в качестве аргумента командной строки, можно использовать не более 32768 символов.</span><span class="sxs-lookup"><span data-stu-id="12369-125">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="12369-126">Это ограничение на всех платформах.</span><span class="sxs-lookup"><span data-stu-id="12369-126">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12369-127">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="12369-127">See also</span></span>

- [<span data-ttu-id="12369-128">Соглашения о структуре программы и коде</span><span class="sxs-lookup"><span data-stu-id="12369-128">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="12369-129">Соглашения об именах Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12369-129">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
