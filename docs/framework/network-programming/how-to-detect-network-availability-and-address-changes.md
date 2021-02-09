---
description: 'Подробнее о следующем: Практическое руководство. Определение доступности сети и изменений адреса'
title: Практическое руководство. Определение доступности сети и изменений адреса
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
ms.openlocfilehash: b9465cbfc538c551725d6510cac3c73d006b7b59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747443"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="ea94f-103">Практическое руководство. Определение доступности сети и изменений адреса</span><span class="sxs-lookup"><span data-stu-id="ea94f-103">How to: Detect Network Availability and Address Changes</span></span>

<span data-ttu-id="ea94f-104">В этом примере показано, как обнаружить изменения в сетевом адресе интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ea94f-104">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea94f-105">Пример</span><span class="sxs-lookup"><span data-stu-id="ea94f-105">Example</span></span>  
  
```csharp
using System;  
using System.Net;  
using System.Net.NetworkInformation;  
  
namespace Examples.Net.AddressChanges  
{  
    public class NetworkingExample  
    {  
        public static void Main()  
        {  
            NetworkChange.NetworkAddressChanged += new
             NetworkAddressChangedEventHandler(AddressChangedCallback);  
            Console.WriteLine("Listening for address changes. Press any key to exit.");  
            Console.ReadLine();  
        }  
        static void AddressChangedCallback(object sender, EventArgs e)  
        {  
  
            NetworkInterface[] adapters = NetworkInterface.GetAllNetworkInterfaces();  
            foreach(NetworkInterface n in adapters)  
            {  
                Console.WriteLine("   {0} is {1}", n.Name, n.OperationalStatus);  
            }  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ea94f-106">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="ea94f-106">Compiling the Code</span></span>  

 <span data-ttu-id="ea94f-107">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="ea94f-107">This example requires:</span></span>  
  
- <span data-ttu-id="ea94f-108">Ссылки на пространство имен **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="ea94f-108">References to the **System.Net** namespace.</span></span>
