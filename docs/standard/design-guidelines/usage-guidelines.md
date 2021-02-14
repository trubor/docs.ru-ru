---
description: 'Узнайте подробнее о: Рекомендации по использованию'
title: Рекомендации по использованию
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: a435fab2adb00f671dfde1619a3c1f8db719d9df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641802"
---
# <a name="usage-guidelines"></a><span data-ttu-id="89ceb-103">Рекомендации по использованию</span><span class="sxs-lookup"><span data-stu-id="89ceb-103">Usage guidelines</span></span>

<span data-ttu-id="89ceb-104">В этом разделе приведены рекомендации по использованию распространенных типов в общедоступных API.</span><span class="sxs-lookup"><span data-stu-id="89ceb-104">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="89ceb-105">В нем описано прямое использование встроенных типов платформ (например, атрибутов сериализации) и перегрузки стандартных операторов.</span><span class="sxs-lookup"><span data-stu-id="89ceb-105">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="89ceb-106">Интерфейс <xref:System.IDisposable?displayProperty=nameWithType> рассматривается в разделе [Шаблон освобождения](../garbage-collection/implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="89ceb-106">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../garbage-collection/implementing-dispose.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="89ceb-107">Рекомендации и дополнительные сведения о других стандартных встроенных типах .NET Framework см. в следующих справочных разделах , посвященных следующим темам: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="89ceb-107">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="89ceb-108">Содержание раздела</span><span class="sxs-lookup"><span data-stu-id="89ceb-108">In this section</span></span>

[<span data-ttu-id="89ceb-109">Массивы</span><span class="sxs-lookup"><span data-stu-id="89ceb-109">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="89ceb-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="89ceb-110">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="89ceb-111">Коллекции</span><span class="sxs-lookup"><span data-stu-id="89ceb-111">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="89ceb-112">Сериализация</span><span class="sxs-lookup"><span data-stu-id="89ceb-112">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="89ceb-113">Использование System.Xml</span><span class="sxs-lookup"><span data-stu-id="89ceb-113">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="89ceb-114">Операторы равенства</span><span class="sxs-lookup"><span data-stu-id="89ceb-114">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="89ceb-115">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="89ceb-115">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="89ceb-116">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="89ceb-116">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="89ceb-117">См. также</span><span class="sxs-lookup"><span data-stu-id="89ceb-117">See also</span></span>

- [<span data-ttu-id="89ceb-118">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="89ceb-118">Framework Design Guidelines</span></span>](index.md)
