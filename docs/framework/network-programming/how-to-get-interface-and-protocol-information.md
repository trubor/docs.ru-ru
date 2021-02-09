---
description: 'Подробнее о следующем: Практическое руководство. Получение информации об интерфейсах и протоколах'
title: Практическое руководство. Получение информации об интерфейсах и протоколах
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: fd88d26c-4063-495e-a253-736ac3e6b23f
ms.openlocfilehash: 8db91bbd556a3d145674b00cd017d7c068936995
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785774"
---
# <a name="how-to-get-interface-and-protocol-information"></a><span data-ttu-id="8e5c9-103">Практическое руководство. Получение информации об интерфейсах и протоколах</span><span class="sxs-lookup"><span data-stu-id="8e5c9-103">How to: Get Interface and Protocol Information</span></span>

<span data-ttu-id="8e5c9-104">В этом примере показано, как считать статистику TCP сетевого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8e5c9-104">This sample shows how to read the TCP statistics of a network interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e5c9-105">Пример</span><span class="sxs-lookup"><span data-stu-id="8e5c9-105">Example</span></span>  
  
```csharp
public static void ShowTcpStatistics(NetworkInterfaceComponent version)  
{  
    IPGlobalProperties properties =  
          IPGlobalProperties.GetIPGlobalProperties();  
    TcpStatistics tcpstat = null;  
    Console.WriteLine("");  
    switch (version)  
    {  
        case NetworkInterfaceComponent.IPv4:  
             tcpstat = properties.GetTcpIPv4Statistics();  
            Console.WriteLine("TCP/IPv4 Statistics:");  
            break;  
        case NetworkInterfaceComponent.IPv6:  
            tcpstat = properties.GetTcpIPv6Statistics();  
            Console.WriteLine("TCP/IPv6 Statistics:");  
            break;  
        default:  
            throw new ArgumentException("version");  
            break;  
    }  
    Console.WriteLine("  Minimum Transmission Timeout. : {0}",
        tcpstat.MinimumTransmissionTimeout);  
    Console.WriteLine("  Maximum Transmission Timeout. : {0}",
        tcpstat.MaximumTransmissionTimeout);  
  
    Console.WriteLine("  Connection Data:");  
    Console.WriteLine("      Current : {0}",
    tcpstat.CurrentConnections);  
    Console.WriteLine("      Cumulative : {0}",
        tcpstat.CumulativeConnections);  
    Console.WriteLine("      Initiated  : {0}",
        tcpstat.ConnectionsInitiated);  
    Console.WriteLine("      Accepted : {0}",
        tcpstat.ConnectionsAccepted);  
    Console.WriteLine("      Failed Attempts : {0}",
        tcpstat.FailedConnectionAttempts);  
    Console.WriteLine("      Reset : {0}",
        tcpstat.ResetConnections);  
  
    Console.WriteLine("");  
    Console.WriteLine("  Segment Data:");  
    Console.WriteLine("      Received  ................... : {0}",
        tcpstat.SegmentsReceived);  
    Console.WriteLine("      Sent : {0}",
        tcpstat.SegmentsSent);  
    Console.WriteLine("      Retransmitted : {0}",
        tcpstat.SegmentsResent);  
  
    Console.WriteLine("");  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8e5c9-106">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="8e5c9-106">Compiling the Code</span></span>  

 <span data-ttu-id="8e5c9-107">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="8e5c9-107">This example requires:</span></span>  
  
- <span data-ttu-id="8e5c9-108">Ссылки на пространство имен **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="8e5c9-108">References to the **System.Net** namespace.</span></span>
