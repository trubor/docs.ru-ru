---
description: 'Узнайте подробнее о: Разработка полей'
title: Разработка полей
ms.date: 10/22/2008
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 88df60c3050035221dc65429bbd543c71d5d69b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642049"
---
# <a name="field-design"></a><span data-ttu-id="1b67a-103">Разработка полей</span><span class="sxs-lookup"><span data-stu-id="1b67a-103">Field Design</span></span>

<span data-ttu-id="1b67a-104">Принцип инкапсуляции — одна из наиболее важных концепций объектно-ориентированного проектирования.</span><span class="sxs-lookup"><span data-stu-id="1b67a-104">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="1b67a-105">Этот принцип указывает, что данные, хранящиеся внутри объекта, должны быть доступны только для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="1b67a-105">This principle states that data stored inside an object should be accessible only to that object.</span></span>

 <span data-ttu-id="1b67a-106">Чтобы истолковать принцип, достаточно сказать, что тип должен быть спроектирован таким образом, чтобы изменения полей этого типа (изменения имени или типа) можно было выполнять без нарушения кода, не относящегося к элементам типа.</span><span class="sxs-lookup"><span data-stu-id="1b67a-106">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="1b67a-107">Такая интерпретация подразумевает, что все поля должны быть закрытыми.</span><span class="sxs-lookup"><span data-stu-id="1b67a-107">This interpretation immediately implies that all fields must be private.</span></span>

 <span data-ttu-id="1b67a-108">Мы исключили константные и статические поля только для чтения из этого строгого ограничения, так как такие поля практически по определению не требуют изменения.</span><span class="sxs-lookup"><span data-stu-id="1b67a-108">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>

 <span data-ttu-id="1b67a-109">❌ НЕ следует предоставлять открытые или защищенные поля экземпляров.</span><span class="sxs-lookup"><span data-stu-id="1b67a-109">❌ DO NOT provide instance fields that are public or protected.</span></span>

 <span data-ttu-id="1b67a-110">Необходимо предоставить свойства для доступа к полям вместо того, чтобы сделать их открытыми или защищенными.</span><span class="sxs-lookup"><span data-stu-id="1b67a-110">You should provide properties for accessing fields instead of making them public or protected.</span></span>

 <span data-ttu-id="1b67a-111">✔️ ИСПОЛЬЗУЙТЕ константные поля для констант, которые никогда не изменятся.</span><span class="sxs-lookup"><span data-stu-id="1b67a-111">✔️ DO use constant fields for constants that will never change.</span></span>

 <span data-ttu-id="1b67a-112">Компилятор записывает значения константных полей непосредственно в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="1b67a-112">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="1b67a-113">Поэтому значения-константы невозможно изменить без риска нарушения совместимости.</span><span class="sxs-lookup"><span data-stu-id="1b67a-113">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>

 <span data-ttu-id="1b67a-114">✔️ ИСПОЛЬЗУЙТЕ открытые статические поля `readonly` для предопределенных экземпляров объектов.</span><span class="sxs-lookup"><span data-stu-id="1b67a-114">✔️ DO use public static `readonly` fields for predefined object instances.</span></span>

 <span data-ttu-id="1b67a-115">При наличии предопределенных экземпляров типа объявите их как открытые статические поля только для чтения самого типа.</span><span class="sxs-lookup"><span data-stu-id="1b67a-115">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>

 <span data-ttu-id="1b67a-116">❌ НЕ присваивайте полям `readonly` экземпляры изменяемых типов.</span><span class="sxs-lookup"><span data-stu-id="1b67a-116">❌ DO NOT assign instances of mutable types to `readonly` fields.</span></span>

 <span data-ttu-id="1b67a-117">Изменяемый тип — это тип с экземплярами, которые можно изменить после создания экземпляра.</span><span class="sxs-lookup"><span data-stu-id="1b67a-117">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="1b67a-118">Например, массивы, большинство коллекций и потоки являются изменяемыми типами, но <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType> и <xref:System.String?displayProperty=nameWithType> являются неизменяемыми.</span><span class="sxs-lookup"><span data-stu-id="1b67a-118">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="1b67a-119">Модификатор только для чтения в поле ссылочного типа предотвращает замену экземпляра, хранящегося в поле, но не предотвращает изменение данных экземпляра поля путем вызова элементов, изменяющих экземпляр.</span><span class="sxs-lookup"><span data-stu-id="1b67a-119">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>

 <span data-ttu-id="1b67a-120">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="1b67a-120">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1b67a-121">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1b67a-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1b67a-122">См. также</span><span class="sxs-lookup"><span data-stu-id="1b67a-122">See also</span></span>

- [<span data-ttu-id="1b67a-123">Правила разработки членов</span><span class="sxs-lookup"><span data-stu-id="1b67a-123">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="1b67a-124">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="1b67a-124">Framework Design Guidelines</span></span>](index.md)
