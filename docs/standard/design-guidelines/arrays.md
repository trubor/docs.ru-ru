---
description: 'Узнайте подробнее о: Массивы'
title: Массивы
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: 2d919d5e13a03ed1c5d090339f8f0fd9c1a79190
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642451"
---
# <a name="arrays"></a><span data-ttu-id="76741-103">Массивы</span><span class="sxs-lookup"><span data-stu-id="76741-103">Arrays</span></span>

<span data-ttu-id="76741-104">✔️ СЛЕДУЕТ отдавать предпочтение использованию в общедоступных API коллекций, а не массивов.</span><span class="sxs-lookup"><span data-stu-id="76741-104">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="76741-105">В разделе [Коллекции](guidelines-for-collections.md) приведены сведения о том, как выбрать между коллекциями и массивами.</span><span class="sxs-lookup"><span data-stu-id="76741-105">The [Collections](guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="76741-106">❌ НЕ СЛЕДУЕТ использовать поля массивов, доступные только для чтения.</span><span class="sxs-lookup"><span data-stu-id="76741-106">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="76741-107">Само поле доступно только для чтения и не может быть изменено, но элементы массива можно изменять.</span><span class="sxs-lookup"><span data-stu-id="76741-107">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="76741-108">✔️ РЕКОМЕНДУЕТСЯ использовать массивы массивов, а не многомерные массивы.</span><span class="sxs-lookup"><span data-stu-id="76741-108">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="76741-109">Массив массивов — это массив с элементами, которые также являются массивами.</span><span class="sxs-lookup"><span data-stu-id="76741-109">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="76741-110">Массивы, которые составляют элементы, могут иметь различные размеры, что позволяет экономить пространство для некоторых наборов данных (например, разреженных матриц) по сравнению с многомерными массивами.</span><span class="sxs-lookup"><span data-stu-id="76741-110">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="76741-111">Более того, среда CLR оптимизирует операции с индексами в массивах массивов, что позволяет повысить производительность в некоторых сценариях.</span><span class="sxs-lookup"><span data-stu-id="76741-111">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="76741-112">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="76741-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="76741-113">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="76741-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="76741-114">См. также</span><span class="sxs-lookup"><span data-stu-id="76741-114">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="76741-115">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="76741-115">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="76741-116">Правила использования</span><span class="sxs-lookup"><span data-stu-id="76741-116">Usage Guidelines</span></span>](usage-guidelines.md)
