---
title: Интерпретация сетевой трассировки
description: Узнайте, как использовать трассировку для захвата вызовов, которые приложение выполняет для различных элементов класса System.Net в .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 63d7e36bb95054303fc4f26b0fd14dc3d10dbb7d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241568"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="0b005-103">Интерпретация сетевой трассировки</span><span class="sxs-lookup"><span data-stu-id="0b005-103">Interpreting Network Tracing</span></span>

<span data-ttu-id="0b005-104">Если включена трассировка сети, ее можно использовать для записи вызовов, осуществляемых приложением к различным членам класса <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="0b005-104">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="0b005-105">Выходные данные этих вызовов могут быть аналогичны приведенным далее.</span><span class="sxs-lookup"><span data-stu-id="0b005-105">The output from these calls may be similar to the following examples.</span></span>  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 <span data-ttu-id="0b005-106">В приведенном выше примере [588] — уникальный идентификатор текущего потока.</span><span class="sxs-lookup"><span data-stu-id="0b005-106">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="0b005-107">(4357) и (4387) — метки времени, обозначающие количество миллисекунд, прошедших с момента запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="0b005-107">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="0b005-108">Данные, которые идут за меткой времени, указывают на приложение, начинающее и завершающее метод **Socket.Send**.</span><span class="sxs-lookup"><span data-stu-id="0b005-108">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="0b005-109">Объект, выполняющий метод **Send**, имеет уникальный идентификатор 33574638.</span><span class="sxs-lookup"><span data-stu-id="0b005-109">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="0b005-110">Трассировка завершения метода содержит возвращаемое значение (61 в предыдущем примере).</span><span class="sxs-lookup"><span data-stu-id="0b005-110">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="0b005-111">Сетевая трассировка может записывать сетевой трафик, отправленный из приложения или полученный им с помощью протоколов уровня приложения, таких как HTTP.</span><span class="sxs-lookup"><span data-stu-id="0b005-111">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="0b005-112">Эти данные могут захватываться как текст и шестнадцатеричные данные.</span><span class="sxs-lookup"><span data-stu-id="0b005-112">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="0b005-113">Шестнадцатеричные данные доступны при указании **includehex** в качестве значения атрибута **tracemode**.</span><span class="sxs-lookup"><span data-stu-id="0b005-113">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="0b005-114">(Подробные сведения об этом атрибуте см. в разделе [Практическое руководство. Настройка трассировки сети](how-to-configure-network-tracing.md).) Следующий пример трассировки был создан с помощью **includehex**.</span><span class="sxs-lookup"><span data-stu-id="0b005-114">(For detailed information about this attribute, see [How to: Configure Network Tracing](how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="0b005-115">Чтобы опустить шестнадцатеричные данные, укажите **protocolonly** в качестве значения атрибута **tracemode**.</span><span class="sxs-lookup"><span data-stu-id="0b005-115">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="0b005-116">В следующем примере показана трассировка с указанным значением **protocolonly**.</span><span class="sxs-lookup"><span data-stu-id="0b005-116">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="0b005-117">См. также</span><span class="sxs-lookup"><span data-stu-id="0b005-117">See also</span></span>

- [<span data-ttu-id="0b005-118">Включение трассировки сети</span><span class="sxs-lookup"><span data-stu-id="0b005-118">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="0b005-119">Практическое руководство. Настройка трассировки сети</span><span class="sxs-lookup"><span data-stu-id="0b005-119">How to: Configure Network Tracing</span></span>](how-to-configure-network-tracing.md)
- [<span data-ttu-id="0b005-120">Трассировка сети в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0b005-120">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
