---
description: 'Дополнительные сведения: Visual Basic соглашения об именовании'
title: Соглашения об именах
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 058d3b06ca1da71c4d8993c6bd451531ec758dbd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461012"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="e8d6e-103">Соглашения об именах Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e8d6e-103">Visual Basic Naming Conventions</span></span>

<span data-ttu-id="e8d6e-104">При именовании элемента в Visual Basic приложении первым символом этого имени должна быть буква или символ подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-104">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="e8d6e-105">Однако обратите внимание, что имена, начинающиеся с символа подчеркивания, не соответствуют [языку и Language-Independent компонентам](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="e8d6e-105">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="e8d6e-106">Следующие рекомендации применимы к именованию.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-106">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="e8d6e-107">Начинайте каждое отдельное слово в имени с заглавной буквой, как в `FindLastRecord` и `RedrawMyForm` .</span><span class="sxs-lookup"><span data-stu-id="e8d6e-107">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="e8d6e-108">Начинайте имена функций и методов с помощью глагола, как в `InitNameArray` или `CloseDialog` .</span><span class="sxs-lookup"><span data-stu-id="e8d6e-108">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="e8d6e-109">Имена классов, структур, модулей и свойств следует начинать с существительных, как в `EmployeeName` или `CarAccessory` .</span><span class="sxs-lookup"><span data-stu-id="e8d6e-109">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="e8d6e-110">Имена интерфейсов начинаются с префикса "I", за которым следует существительное или субстантивные словосочетания, например `IComponent` , или с прилагательным, описывающим поведение интерфейса, например `IPersistable` .</span><span class="sxs-lookup"><span data-stu-id="e8d6e-110">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="e8d6e-111">Не используйте символ подчеркивания и используйте сокращения экономно, поскольку аббревиатуры могут вызвать путаницу.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-111">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="e8d6e-112">Передайте имена обработчиков событий с существительным, описывающим тип события, за которым следует суффикс "" `EventHandler` , как в " `MouseEventHandler` ".</span><span class="sxs-lookup"><span data-stu-id="e8d6e-112">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="e8d6e-113">В именах классов аргументов событий включите `EventArgs` суффикс "".</span><span class="sxs-lookup"><span data-stu-id="e8d6e-113">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="e8d6e-114">Если событие имеет концепцию "до" или "после", используйте суффикс в настоящем или прошлом прошедшем, как в " `ControlAdd` " или " `ControlAdded` ".</span><span class="sxs-lookup"><span data-stu-id="e8d6e-114">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="e8d6e-115">Для длинных или часто используемых терминов используйте аббревиатуры, чтобы обеспечить приемлемую длину имен, например "HTML", а не "HTML".</span><span class="sxs-lookup"><span data-stu-id="e8d6e-115">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="e8d6e-116">В общем случае имена переменных, длина которых превышает 32 символов, трудно прочитать на мониторе, для которого задано низкое разрешение.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-116">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="e8d6e-117">Кроме того, убедитесь, что аббревиатуры согласованы во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-117">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="e8d6e-118">Случайное переключение в проект между "HTML" и "HTML" может привести к путанице.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-118">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="e8d6e-119">Старайтесь не использовать имена во внутренней области, имена которых совпадают с именами во внешней области.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-119">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="e8d6e-120">Если доступ к неправильной переменной будет осуществлен, могут возникнуть ошибки.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-120">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="e8d6e-121">Если возникает конфликт между переменной и ключевым словом с тем же именем, необходимо сначала обозначить ключевое слово, указав его перед соответствующей библиотекой типов.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-121">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="e8d6e-122">Например, если имеется переменная с именем `Date` , можно использовать встроенную `Date` функцию только путем вызова <xref:System.DateTime.Date%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e8d6e-122">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d6e-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e8d6e-123">See also</span></span>

- [<span data-ttu-id="e8d6e-124">Ключевые слова как имена элементов в коде</span><span class="sxs-lookup"><span data-stu-id="e8d6e-124">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)
- [<span data-ttu-id="e8d6e-125">Me, My, MyBase и MyClass</span><span class="sxs-lookup"><span data-stu-id="e8d6e-125">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)
- [<span data-ttu-id="e8d6e-126">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="e8d6e-126">Declared Element Names</span></span>](../language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="e8d6e-127">Соглашения о структуре программы и коде</span><span class="sxs-lookup"><span data-stu-id="e8d6e-127">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="e8d6e-128">Справочник по языку Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e8d6e-128">Visual Basic Language Reference</span></span>](../../language-reference/index.md)
