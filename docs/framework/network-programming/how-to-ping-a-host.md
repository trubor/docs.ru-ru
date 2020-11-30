---
title: Практическое руководство. Проверка связи с узлом
description: Образец кода, демонстрирующий проверку связи с удаленным узлом в .NET Framework. Для данного примера требуются ссылки на пространство имен System.Net.
ms.date: 03/30/2017
helpviewer_keywords:
- Ping
ms.assetid: bbf20f5b-eca1-4661-af04-cb8837f9af05
ms.openlocfilehash: 1e77f7eb4dbb8a69848bc6b20e98e0df931f22c9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244032"
---
# <a name="how-to-ping-a-host"></a><span data-ttu-id="e7f1b-104">Практическое руководство. Проверка связи с узлом</span><span class="sxs-lookup"><span data-stu-id="e7f1b-104">How to: Ping a Host</span></span>

<span data-ttu-id="e7f1b-105">В этом примере показано, как проверить связь с удаленным узлом.</span><span class="sxs-lookup"><span data-stu-id="e7f1b-105">This sample shows how to ping a remote host.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7f1b-106">Пример</span><span class="sxs-lookup"><span data-stu-id="e7f1b-106">Example</span></span>  
  
```csharp
using System;  
using System.Text;  
using System.Net;  
using System.Net.NetworkInformation;  
using System.ComponentModel;  
using System.Threading;  
  
namespace Examples.System.Net.NetworkInformation.PingTest  
{  
    public class PingExample  
    {  
        public static void Main (string[] args)  
        {  
            if (args.Length == 0)  
                throw new ArgumentException ("Ping needs a host or IP Address.");  
  
            string who = args[0];  
            AutoResetEvent waiter = new AutoResetEvent (false);  
  
            Ping pingSender = new Ping ();  
  
            // When the PingCompleted event is raised,  
            // the PingCompletedCallback method is called.  
            pingSender.PingCompleted += new PingCompletedEventHandler (PingCompletedCallback);  
  
            // Create a buffer of 32 bytes of data to be transmitted.  
            string data = "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";  
            byte[] buffer = Encoding.ASCII.GetBytes (data);  
  
            // Wait 12 seconds for a reply.  
            int timeout = 12000;  
  
            // Set options for transmission:  
            // The data can go through 64 gateways or routers  
            // before it is destroyed, and the data packet  
            // cannot be fragmented.  
            PingOptions options = new PingOptions (64, true);  
  
            Console.WriteLine ("Time to live: {0}", options.Ttl);  
            Console.WriteLine ("Don't fragment: {0}", options.DontFragment);  
  
            // Send the ping asynchronously.  
            // Use the waiter as the user token.  
            // When the callback completes, it can wake up this thread.  
            pingSender.SendAsync(who, timeout, buffer, options, waiter);  
  
            // Prevent this example application from ending.  
            // A real application should do something useful  
            // when possible.  
            waiter.WaitOne ();  
            Console.WriteLine ("Ping example completed.");  
        }  
  
        public static void PingCompletedCallback (object sender, PingCompletedEventArgs e)  
        {  
            // If the operation was canceled, display a message to the user.  
            if (e.Cancelled)  
            {  
                Console.WriteLine ("Ping canceled.");  
  
                // Let the main thread resume.
                // UserToken is the AutoResetEvent object that the main thread
                // is waiting for.  
                ((AutoResetEvent)e.UserState).Set ();  
            }  
  
            // If an error occurred, display the exception to the user.  
            if (e.Error != null)  
            {  
                Console.WriteLine ("Ping failed:");  
                Console.WriteLine (e.Error.ToString ());  
  
                // Let the main thread resume.
                ((AutoResetEvent)e.UserState).Set();  
            }  
  
            PingReply reply = e.Reply;  
  
            DisplayReply (reply);  
  
            // Let the main thread resume.  
            ((AutoResetEvent)e.UserState).Set();  
        }  
  
        public static void DisplayReply (PingReply reply)  
        {  
            if (reply == null)  
                return;  
  
            Console.WriteLine ("ping status: {0}", reply.Status);  
            if (reply.Status == IPStatus.Success)  
            {  
                Console.WriteLine ("Address: {0}", reply.Address.ToString ());  
                Console.WriteLine ("RoundTrip time: {0}", reply.RoundtripTime);  
                Console.WriteLine ("Time to live: {0}", reply.Options.Ttl);  
                Console.WriteLine ("Don't fragment: {0}", reply.Options.DontFragment);  
                Console.WriteLine ("Buffer size: {0}", reply.Buffer.Length);  
            }  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7f1b-107">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="e7f1b-107">Compiling the Code</span></span>  

 <span data-ttu-id="e7f1b-108">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="e7f1b-108">This example requires:</span></span>  
  
- <span data-ttu-id="e7f1b-109">Ссылки на пространство имен **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="e7f1b-109">References to the **System.Net** namespace.</span></span>
