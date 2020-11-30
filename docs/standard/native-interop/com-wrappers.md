---
title: Оболочки COM
description: Клиенты COM и объекты .NET взаимодействуют с помощью вызываемой оболочки COM и вызываемой оболочки времени выполнения. Среда CLR создает оболочки автоматически.
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
ms.openlocfilehash: 17a303cde5fa51cd940b0375d2c6657fcd354dc5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706337"
---
# <a name="com-wrappers"></a><span data-ttu-id="9d058-104">Оболочки COM</span><span class="sxs-lookup"><span data-stu-id="9d058-104">COM Wrappers</span></span>

<span data-ttu-id="9d058-105">Модель COM имеет несколько важных отличий от объектной модели среды выполнения .NET:</span><span class="sxs-lookup"><span data-stu-id="9d058-105">COM differs from the .NET runtime object model in several important ways:</span></span>  
  
- <span data-ttu-id="9d058-106">Клиенты COM-объектов должны управлять временем существования этих объектов. В общеязыковой среде выполнения управление временем существования объектов осуществляет сама среда.</span><span class="sxs-lookup"><span data-stu-id="9d058-106">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
- <span data-ttu-id="9d058-107">Клиенты COM-объектов определяют доступность службы, запрашивая интерфейс, который ее предоставляет, в результате чего возвращается или не возвращается указатель на интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9d058-107">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="9d058-108">Клиенты объектов .NET могут получать описание функциональных возможностей объекта с помощью отражения.</span><span class="sxs-lookup"><span data-stu-id="9d058-108">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
- <span data-ttu-id="9d058-109">Объекты .NET располагаются в памяти под управлением среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="9d058-109">NET objects reside in memory managed by the .NET runtime execution environment.</span></span> <span data-ttu-id="9d058-110">Среда выполнения может перемещать объекты в памяти в целях оптимизации производительности и обновлять все ссылки на перемещаемые объекты.</span><span class="sxs-lookup"><span data-stu-id="9d058-110">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="9d058-111">Неуправляемые клиенты после получения указателя на объект работают с объектом, находящимся в указанном расположении.</span><span class="sxs-lookup"><span data-stu-id="9d058-111">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="9d058-112">У этих клиентов отсутствуют механизмы для работы с объектами, не имеющими фиксированного расположения.</span><span class="sxs-lookup"><span data-stu-id="9d058-112">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="9d058-113">Чтобы обойти эти различия, среда выполнения предоставляет классы-оболочки, которые моделируют вызов объектов в соответствующих им средах для управляемых и неуправляемых клиентов.</span><span class="sxs-lookup"><span data-stu-id="9d058-113">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="9d058-114">Каждый раз, когда управляемый клиент вызывает метод для COM-объекта, среда выполнения создает [вызываемую оболочку времени выполнения](runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="9d058-114">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="9d058-115">Помимо прочего, вызываемая оболочка времени выполнения позволяет абстрагировать различия между управляемыми и неуправляемыми механизмами ссылок.</span><span class="sxs-lookup"><span data-stu-id="9d058-115">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="9d058-116">Среда выполнения также создает [вызываемую оболочку COM](com-callable-wrapper.md) (CCW) для работы в обратном направлении, когда COM-клиенту требуется вызвать метод для объекта .NET.</span><span class="sxs-lookup"><span data-stu-id="9d058-116">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="9d058-117">Как показано на следующем рисунке, класс-оболочка, который создается средой выполнения, зависит от контекста вызывающего кода.</span><span class="sxs-lookup"><span data-stu-id="9d058-117">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 ![Общие сведения об оболочках COM](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 <span data-ttu-id="9d058-119">В большинстве случаев стандартная вызываемая оболочка времени выполнения или вызываемая оболочка COM, создаваемая средой выполнения, реализует маршалинг вызовов, которые выполняются между средами выполнения COM и .NET.</span><span class="sxs-lookup"><span data-stu-id="9d058-119">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET runtime.</span></span> <span data-ttu-id="9d058-120">С помощью настраиваемых атрибутов при необходимости можно определить способ представления управляемого и неуправляемого кода в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="9d058-120">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d058-121">См. также</span><span class="sxs-lookup"><span data-stu-id="9d058-121">See also</span></span>

- <span data-ttu-id="9d058-122">[Расширенное COM-взаимодействие в .NET Framework](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9d058-122">[Advanced COM Interoperability in .NET Framework](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="9d058-123">Вызываемая оболочка времени выполнения</span><span class="sxs-lookup"><span data-stu-id="9d058-123">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
- [<span data-ttu-id="9d058-124">Вызываемая оболочка COM</span><span class="sxs-lookup"><span data-stu-id="9d058-124">COM Callable Wrapper</span></span>](com-callable-wrapper.md)
- <span data-ttu-id="9d058-125">[Настройка стандартных оболочек в платформе .NET Framework](/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9d058-125">[Customizing Standard Wrappers in .NET Framework](/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="9d058-126">[Практическое руководство. Настройка вызываемых оболочек времени выполнения в платформе .NET Framework](/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9d058-126">[How to: Customize Runtime Callable Wrappers in .NET Framework](/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span></span>
