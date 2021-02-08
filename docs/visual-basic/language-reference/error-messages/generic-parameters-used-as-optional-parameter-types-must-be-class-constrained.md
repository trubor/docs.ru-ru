---
description: 'Дополнительные сведения о: BC32124: универсальные параметры, используемые в качестве необязательных типов параметров, должны быть ограничены классом'
title: Универсальные параметры, используемые как типы необязательных параметров, должны быть ограничены классом
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 0014720d55dc4395178186b5e183d5b0279d7029
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796149"
---
# <a name="bc32124-generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="0b93c-103">BC32124: универсальные параметры, используемые как необязательные типы параметров, должны быть ограничены классом</span><span class="sxs-lookup"><span data-stu-id="0b93c-103">BC32124: Generic parameters used as optional parameter types must be class constrained</span></span>

<span data-ttu-id="0b93c-104">Процедура объявлена с необязательным параметром, который использует параметр типа, который не ограничивается ссылочным типом.</span><span class="sxs-lookup"><span data-stu-id="0b93c-104">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>

 <span data-ttu-id="0b93c-105">Для каждого необязательного параметра всегда необходимо указывать значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0b93c-105">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="0b93c-106">Если параметр имеет ссылочный тип, необязательное значение должно быть `Nothing` допустимым значением для любого ссылочного типа.</span><span class="sxs-lookup"><span data-stu-id="0b93c-106">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="0b93c-107">Однако если параметр имеет тип значения, то этот тип должен быть простейшим типом данных, предопределенным Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0b93c-107">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="0b93c-108">Это обусловлено тем, что тип составного значения, например определяемая пользователем структура, не имеет допустимого значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0b93c-108">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>

 <span data-ttu-id="0b93c-109">При использовании параметра типа для необязательного параметра необходимо гарантировать, что он имеет ссылочный тип, чтобы избежать возможности типа значения, не имеющего допустимого значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0b93c-109">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="0b93c-110">Это означает, что необходимо ограничить параметр типа либо с помощью `Class` ключевого слова, либо с помощью имени определенного класса.</span><span class="sxs-lookup"><span data-stu-id="0b93c-110">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>

 <span data-ttu-id="0b93c-111">**Идентификатор ошибки:** BC32124</span><span class="sxs-lookup"><span data-stu-id="0b93c-111">**Error ID:** BC32124</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0b93c-112">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="0b93c-112">To correct this error</span></span>

- <span data-ttu-id="0b93c-113">Ограничьте параметр типа, чтобы он принимал только ссылочный тип, или не используйте его для необязательного параметра.</span><span class="sxs-lookup"><span data-stu-id="0b93c-113">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b93c-114">См. также</span><span class="sxs-lookup"><span data-stu-id="0b93c-114">See also</span></span>

- [<span data-ttu-id="0b93c-115">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0b93c-115">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="0b93c-116">Type List</span><span class="sxs-lookup"><span data-stu-id="0b93c-116">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="0b93c-117">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="0b93c-117">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="0b93c-118">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="0b93c-118">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="0b93c-119">Структуры</span><span class="sxs-lookup"><span data-stu-id="0b93c-119">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0b93c-120">Nothing</span><span class="sxs-lookup"><span data-stu-id="0b93c-120">Nothing</span></span>](../nothing.md)
