---
description: 'Узнайте подробнее о: Защищенные члены'
title: Защищенные члены
ms.date: 10/22/2008
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 5860828a5a469c77fbee001d01460a488fda4edf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731764"
---
# <a name="protected-members"></a><span data-ttu-id="db9f9-103">Защищенные члены</span><span class="sxs-lookup"><span data-stu-id="db9f9-103">Protected Members</span></span>

<span data-ttu-id="db9f9-104">Защищенные члены сами по себе не обеспечивают какую-либо расширяемость, но они могут сделать ее более эффективной с помощью подклассов.</span><span class="sxs-lookup"><span data-stu-id="db9f9-104">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="db9f9-105">Они могут использоваться для предоставления расширенных параметров настройки, не усложняя при этом основной общедоступный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="db9f9-105">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="db9f9-106">Разработчикам платформ необходимо соблюдать осторожность при использовании защищенных членов, так как слово "защищенный" дает ложное ощущение безопасности.</span><span class="sxs-lookup"><span data-stu-id="db9f9-106">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="db9f9-107">Любой пользователь может создать подкласс незапечатанного класса и получить доступ к защищенным членам, поэтому к ним применяются те же практики безопасного кодирования, что и для общедоступных членов.</span><span class="sxs-lookup"><span data-stu-id="db9f9-107">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="db9f9-108">✔️ РЕКОМЕНДУЕТСЯ использовать защищенные члены для расширенной настройки.</span><span class="sxs-lookup"><span data-stu-id="db9f9-108">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="db9f9-109">✔️ СЛЕДУЕТ работать с защищенными членами в незапечатанных классах как с общедоступными в аспектах безопасности, документирования и анализа совместимости.</span><span class="sxs-lookup"><span data-stu-id="db9f9-109">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="db9f9-110">Любой пользователь может создать наследование от класса и получить доступ к защищенным членам.</span><span class="sxs-lookup"><span data-stu-id="db9f9-110">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="db9f9-111">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="db9f9-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="db9f9-112">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="db9f9-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="db9f9-113">См. также</span><span class="sxs-lookup"><span data-stu-id="db9f9-113">See also</span></span>

- [<span data-ttu-id="db9f9-114">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="db9f9-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="db9f9-115">Разработка с обеспечением расширяемости</span><span class="sxs-lookup"><span data-stu-id="db9f9-115">Designing for Extensibility</span></span>](designing-for-extensibility.md)
