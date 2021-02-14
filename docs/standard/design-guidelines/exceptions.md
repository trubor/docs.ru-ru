---
description: 'Узнайте подробнее о: Правила разработки исключений'
title: Правила разработки исключений
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
ms.openlocfilehash: 0845f06dca0ee83d7315c3b0b4b6ae090b24a875
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642114"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="5ebd7-103">Правила разработки исключений</span><span class="sxs-lookup"><span data-stu-id="5ebd7-103">Design Guidelines for Exceptions</span></span>

<span data-ttu-id="5ebd7-104">Обработка исключений имеет множество преимуществ по сравнению с отчетами об ошибках на основе возвращаемых значений.</span><span class="sxs-lookup"><span data-stu-id="5ebd7-104">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="5ebd7-105">Эффективная структура платформы помогает разработчику приложений использовать все преимущества исключений.</span><span class="sxs-lookup"><span data-stu-id="5ebd7-105">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="5ebd7-106">В этом разделе рассматриваются преимущества исключений и приводятся рекомендации по их использованию.</span><span class="sxs-lookup"><span data-stu-id="5ebd7-106">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ebd7-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="5ebd7-107">In This Section</span></span>  

 [<span data-ttu-id="5ebd7-108">Создание исключений</span><span class="sxs-lookup"><span data-stu-id="5ebd7-108">Exception Throwing</span></span>](exception-throwing.md)  
 [<span data-ttu-id="5ebd7-109">Использование исключений стандартных типов</span><span class="sxs-lookup"><span data-stu-id="5ebd7-109">Using Standard Exception Types</span></span>](using-standard-exception-types.md)  
 [<span data-ttu-id="5ebd7-110">Исключения и производительность</span><span class="sxs-lookup"><span data-stu-id="5ebd7-110">Exceptions and Performance</span></span>](exceptions-and-performance.md)  
 <span data-ttu-id="5ebd7-111">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="5ebd7-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5ebd7-112">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="5ebd7-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ebd7-113">См. также</span><span class="sxs-lookup"><span data-stu-id="5ebd7-113">See also</span></span>

- [<span data-ttu-id="5ebd7-114">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="5ebd7-114">Framework Design Guidelines</span></span>](index.md)
