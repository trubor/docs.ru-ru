---
description: 'Подробнее о следующем: Практическое руководство. Установка политики кэша для приложения на основе времени по умолчанию'
title: Практическое руководство. Установка политики кэша для приложения на основе времени по умолчанию
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: 1ca9504d8a6df20d3824230d5fb96eb0f13636eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662771"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="135d4-103">Практическое руководство. Установка политики кэша для приложения на основе времени по умолчанию</span><span class="sxs-lookup"><span data-stu-id="135d4-103">How to: Set the Default Time-Based Cache Policy for an Application</span></span>

<span data-ttu-id="135d4-104">Политики кэша на основе времени по умолчанию позволяют приложению определить поведение кэширования с помощью заголовков, которые отправляются с кэшируемым ресурсом. Поведение кэширования определяется в разделах 13 и 14 стандарта RFC 2616, который доступен на веб-сайте [IETF](https://www.ietf.org/).</span><span class="sxs-lookup"><span data-stu-id="135d4-104">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="135d4-105">Это поведение кэширования подходит для большинства приложений.</span><span class="sxs-lookup"><span data-stu-id="135d4-105">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="135d4-106">Установка политики кэша по умолчанию для приложения</span><span class="sxs-lookup"><span data-stu-id="135d4-106">To set the default automatic policy for an application</span></span>  
  
1. <span data-ttu-id="135d4-107">Создайте объект политики на основе времени по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="135d4-107">Create a default time-based policy object.</span></span>  
  
2. <span data-ttu-id="135d4-108">Установите этот объект политики как объект по умолчанию для домена приложения.</span><span class="sxs-lookup"><span data-stu-id="135d4-108">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="135d4-109">Пример</span><span class="sxs-lookup"><span data-stu-id="135d4-109">Example</span></span>  

 <span data-ttu-id="135d4-110">В двух примерах в этом разделе формируются идентичные политики.</span><span class="sxs-lookup"><span data-stu-id="135d4-110">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="135d4-111">В следующем примере создается политика на основе времени по умолчанию. Затем эта политика устанавливается в качестве политики по умолчанию для домена приложения.</span><span class="sxs-lookup"><span data-stu-id="135d4-111">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 <span data-ttu-id="135d4-112">Политику кэша на основе времени по умолчанию также можно создать с помощью класса <xref:System.Net.Cache.RequestCachePolicy>, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="135d4-112">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="135d4-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="135d4-113">See also</span></span>

- [<span data-ttu-id="135d4-114">Управление кэшем для сетевых приложений</span><span class="sxs-lookup"><span data-stu-id="135d4-114">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="135d4-115">Политика кэша</span><span class="sxs-lookup"><span data-stu-id="135d4-115">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="135d4-116">Политики кэша на основе расположения</span><span class="sxs-lookup"><span data-stu-id="135d4-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="135d4-117">Политики кэша на основе времени</span><span class="sxs-lookup"><span data-stu-id="135d4-117">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="135d4-118">Элемент \<requestCaching> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="135d4-118">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
