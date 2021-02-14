---
description: 'Узнайте подробнее о: Перегрузка членов'
title: Перегрузка членов
ms.date: 10/22/2008
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: d3a545bfec552686e55c9f713d58784497946819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641958"
---
# <a name="member-overloading"></a><span data-ttu-id="7346a-103">Перегрузка членов</span><span class="sxs-lookup"><span data-stu-id="7346a-103">Member Overloading</span></span>

<span data-ttu-id="7346a-104">Перегрузка элементов означает создание двух или более элементов одного типа, которые отличаются только числом или типом параметров, но имеют одинаковые имена.</span><span class="sxs-lookup"><span data-stu-id="7346a-104">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="7346a-105">Например, в следующем примере метод `WriteLine` перегружен.</span><span class="sxs-lookup"><span data-stu-id="7346a-105">For example, in the following, the `WriteLine` method is overloaded:</span></span>

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 <span data-ttu-id="7346a-106">Так как только методы, конструкторы и индексированные свойства могут иметь параметры, только эти элементы могут быть перегружены.</span><span class="sxs-lookup"><span data-stu-id="7346a-106">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>

 <span data-ttu-id="7346a-107">Перегрузка является одним из наиболее важных методов для повышения удобства использования, производительности и удобочитаемости многократно используемых библиотек.</span><span class="sxs-lookup"><span data-stu-id="7346a-107">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="7346a-108">Перегрузка по количеству параметров позволяет предоставить более простые версии конструкторов и методов.</span><span class="sxs-lookup"><span data-stu-id="7346a-108">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="7346a-109">Перегрузка по типу параметра позволяет использовать одно и то же имя для элементов, выполняющих идентичные операции с выбранным набором различных типов.</span><span class="sxs-lookup"><span data-stu-id="7346a-109">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>

 <span data-ttu-id="7346a-110">✔️ ПОПЫТАЙТЕСЬ использовать описательные имена параметров, чтобы указать значение по умолчанию, используемое более короткими перегрузками.</span><span class="sxs-lookup"><span data-stu-id="7346a-110">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>

 <span data-ttu-id="7346a-111">❌ Избегайте произвольного изменения имен параметров в перегрузках.</span><span class="sxs-lookup"><span data-stu-id="7346a-111">❌ AVOID arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="7346a-112">Если параметр в одной перегрузке представляет те же входные данные, что и параметр в другой перегрузке, параметры должны иметь одинаковые имена.</span><span class="sxs-lookup"><span data-stu-id="7346a-112">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>

 <span data-ttu-id="7346a-113">❌ Избегайте несоответствия в упорядочении параметров в перегруженных элементах.</span><span class="sxs-lookup"><span data-stu-id="7346a-113">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="7346a-114">Параметры с одинаковыми именами должны отображаться в одной и той же позиции во всех перегрузках.</span><span class="sxs-lookup"><span data-stu-id="7346a-114">Parameters with the same name should appear in the same position in all overloads.</span></span>

 <span data-ttu-id="7346a-115">✔️ СДЕЛАЙТЕ виртуальной только самую длинную перегрузку (если требуется расширяемость).</span><span class="sxs-lookup"><span data-stu-id="7346a-115">✔️ DO make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="7346a-116">Более короткие перегрузки должны просто вызывать более длинную перегрузку.</span><span class="sxs-lookup"><span data-stu-id="7346a-116">Shorter overloads should simply call through to a longer overload.</span></span>

 <span data-ttu-id="7346a-117">❌ НЕ используйте модификаторы `ref` или `out` для перегрузки элементов.</span><span class="sxs-lookup"><span data-stu-id="7346a-117">❌ DO NOT use `ref` or `out` modifiers to overload members.</span></span>

 <span data-ttu-id="7346a-118">Некоторые языки не могут разрешать вызовы к подобным перегрузкам.</span><span class="sxs-lookup"><span data-stu-id="7346a-118">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="7346a-119">Кроме того, такие перегрузки обычно имеют совершенно другую семантику и, вероятно, являются не перегрузками, а двумя отдельными методами.</span><span class="sxs-lookup"><span data-stu-id="7346a-119">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>

 <span data-ttu-id="7346a-120">❌ НЕ применяйте перегрузки с параметрами в одной и той же позиции и с аналогичными типами, но с разной семантикой.</span><span class="sxs-lookup"><span data-stu-id="7346a-120">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span></span>

 <span data-ttu-id="7346a-121">✔ РАЗРЕШИТЕ передачу значения `null` для необязательных аргументов.</span><span class="sxs-lookup"><span data-stu-id="7346a-121">✔️ DO  allow `null` to be passed for optional arguments.</span></span>

 <span data-ttu-id="7346a-122">✔️ ИСПОЛЬЗУЙТЕ перегрузку элементов вместо определения членов с помощью аргументов по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="7346a-122">✔️ DO use member overloading rather than defining members with default arguments.</span></span>

 <span data-ttu-id="7346a-123">Аргументы по умолчанию несовместимы с CLS.</span><span class="sxs-lookup"><span data-stu-id="7346a-123">Default arguments are not CLS compliant.</span></span>

 <span data-ttu-id="7346a-124">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="7346a-124">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="7346a-125">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="7346a-125">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7346a-126">См. также</span><span class="sxs-lookup"><span data-stu-id="7346a-126">See also</span></span>

- [<span data-ttu-id="7346a-127">Правила разработки членов</span><span class="sxs-lookup"><span data-stu-id="7346a-127">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="7346a-128">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="7346a-128">Framework Design Guidelines</span></span>](index.md)
