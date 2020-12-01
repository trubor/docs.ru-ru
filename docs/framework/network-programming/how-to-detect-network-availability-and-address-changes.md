---
title: Практическое руководство. Определение доступности сети и изменений адреса
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
ms.openlocfilehash: 8f5eef7b6ba41f1ac4050fbc9168fafea31b103f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287318"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="a1494-102">Практическое руководство. Определение доступности сети и изменений адреса</span><span class="sxs-lookup"><span data-stu-id="a1494-102">How to: Detect Network Availability and Address Changes</span></span>

<span data-ttu-id="a1494-103">В этом примере показано, как обнаружить изменения в сетевом адресе интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a1494-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1494-104">Пример</span><span class="sxs-lookup"><span data-stu-id="a1494-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="a1494-105">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="a1494-105">Compiling the Code</span></span>  

 <span data-ttu-id="a1494-106">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="a1494-106">This example requires:</span></span>  
  
- <span data-ttu-id="a1494-107">Ссылки на пространство имен **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="a1494-107">References to the **System.Net** namespace.</span></span>
