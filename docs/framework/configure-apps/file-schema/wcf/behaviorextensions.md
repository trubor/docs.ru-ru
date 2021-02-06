---
description: 'Дополнительные сведения: <behaviorExtensions>'
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: 0bd641f8e26d309c592c07bcc19ff02897fe71cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639527"
---
# \<behaviorExtensions>

<span data-ttu-id="40351-102">Расширения поведений позволяют пользователям создавать пользовательские элементы поведений.</span><span class="sxs-lookup"><span data-stu-id="40351-102">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="40351-103">Эти элементы могут использоваться вместе со стандартными элементами поведений Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="40351-103">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="40351-104">В разделе `behaviorExtensions` определяется элемент, который может использоваться в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="40351-104">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="40351-105">Далее приведен пример типичного расширения поведения.</span><span class="sxs-lookup"><span data-stu-id="40351-105">Here is an example of a typical behavior extension.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <behaviorExtensions>
      <add name="myBehavior"
           type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </behaviorExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="40351-106">Чтобы добавить в элемент возможности конфигурации, нужно записать и зарегистрировать элемент конфигурации.</span><span class="sxs-lookup"><span data-stu-id="40351-106">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="40351-107">Дополнительные сведения об этом см. в документации по <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="40351-107">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="40351-108">После определения элемента и его типа конфигурации поведение можно использовать, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="40351-108">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
```xml  
<behaviors>
  <behavior configurationName="testChannelBehavior">
    <myBehavior />
    <channelSecurity cacheCookies="false"
                     detectReplays="false"
                     maxCachedNonces="9"
                     maxClockSkew="00:00:03"
                     maxCookieCachingTime="00:07:24"
                     replayWindow="00:07:22.2190000" />
  </behavior>
</behaviors>
```  
  
## <a name="security"></a><span data-ttu-id="40351-109">Безопасность</span><span class="sxs-lookup"><span data-stu-id="40351-109">Security</span></span>  

 <span data-ttu-id="40351-110">Настоятельно рекомендуется использовать полные имена сборок при регистрации типов в файлах `machine.config` и `app.config`.</span><span class="sxs-lookup"><span data-stu-id="40351-110">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="40351-111">Если тип определен неоднозначно, загрузчик типов среды CLR ищет его в следующих местоположениях в заданном порядке:</span><span class="sxs-lookup"><span data-stu-id="40351-111">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="40351-112">Если сборка типа известна, загрузчик ищет в местах перенаправления файла конфигурации, в глобальном кэше сборок, в текущей сборке, используя данные конфигурации, и в базовой папке приложения.</span><span class="sxs-lookup"><span data-stu-id="40351-112">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="40351-113">Если сборка неизвестна, загрузчик ищет в текущей сборке, в библиотеке mscorlib и в месте, возвращаемом обработчиком событий `TypeResolve`.</span><span class="sxs-lookup"><span data-stu-id="40351-113">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="40351-114">Порядок поиска в среде CLR может быть изменен с помощью таких средств, как механизм пересылки типа и событие AppDomain.TypeResolve.</span><span class="sxs-lookup"><span data-stu-id="40351-114">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="40351-115">Злоумышленник может использовать порядок поиска в среде CLR и выполнить неавторизованный код.</span><span class="sxs-lookup"><span data-stu-id="40351-115">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="40351-116">Использование полных (надежных) имен однозначно определяет тип и повышает безопасность системы.</span><span class="sxs-lookup"><span data-stu-id="40351-116">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="40351-117">Дополнительные сведения см. [в разделе как среда выполнения находит сборки](../../../deployment/how-the-runtime-locates-assemblies.md) и <xref:System.AppDomain.TypeResolve> .</span><span class="sxs-lookup"><span data-stu-id="40351-117">For more information, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40351-118">См. также</span><span class="sxs-lookup"><span data-stu-id="40351-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [<span data-ttu-id="40351-119">Настройка и расширение среды выполнения с помощью поведений</span><span class="sxs-lookup"><span data-stu-id="40351-119">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
