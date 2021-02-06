---
description: Дополнительные сведения о том, как защитить сообщения в надежных сеансах.
title: Практическое руководство. Защита сообщений с помощью надежных сеансов
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: 73ca0d543edc2445dc72264e7eccf6c1eb616313
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643362"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="95c79-103">Практическое руководство. Защита сообщений с помощью надежных сеансов</span><span class="sxs-lookup"><span data-stu-id="95c79-103">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="95c79-104">В этом разделе описывается обеспечение безопасности на уровне сообщения в ходе надежного сеанса обмена сообщениями с использованием одной из предоставляемых системой привязок, которые поддерживают такие сеансы, но не по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="95c79-104">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="95c79-105">Включите безопасный, надежный сеанс принудительно с помощью кода или декларативно в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="95c79-105">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="95c79-106">В этой процедуре для разрешения защищенного, надежного сеанса используются файлы конфигурации клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="95c79-106">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="95c79-107">Эта процедура включает выполнение трех основных задач, а именно:</span><span class="sxs-lookup"><span data-stu-id="95c79-107">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="95c79-108">необходимо задать, что клиент и служба обмениваются сообщениями в ходе надежного сеанса;</span><span class="sxs-lookup"><span data-stu-id="95c79-108">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="95c79-109">необходимо обеспечить безопасность на уровне сообщения в ходе надежного сеанса;</span><span class="sxs-lookup"><span data-stu-id="95c79-109">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="95c79-110">необходимо задать тип учетных данных клиента, который должен использоваться при проверке подлинности клиента в службе.</span><span class="sxs-lookup"><span data-stu-id="95c79-110">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="95c79-111">В первой задаче важно, чтобы элемент конфигурации конечной точки содержал `bindingConfiguration` атрибут, который ссылается на конфигурацию привязки с именем (в этом примере) `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="95c79-111">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="95c79-112">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Элемент Configuration затем ссылается на это имя, чтобы включить надежные сеансы, задав `enabled` атрибуту [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) элемента значение `true` .</span><span class="sxs-lookup"><span data-stu-id="95c79-112">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="95c79-113">Можно потребовать гарантии упорядоченной доставки сообщений в ходе надежного сеанса, присвоив атрибуту `ordered` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="95c79-113">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="95c79-114">Исходный экземпляр примера, на котором основана эта процедура конфигурации, см. в разделе [надежный сеанс WS](../samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="95c79-114">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="95c79-115">Ключевые элементы второй задачи выполняются путем установки `mode` атрибута **\<security>** элемента, содержащегося в **\<binding>** элементе клиента и службы, на `Message` .</span><span class="sxs-lookup"><span data-stu-id="95c79-115">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="95c79-116">Наиболее важными элементами третьей задачи является установка `clientCredentialType` атрибута **\<message>** элемента, содержащегося в **\<security>** элементе клиента и службы, в значение `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="95c79-116">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="95c79-117">При использовании безопасности сообщений с надежными сеансами надежный обмен сообщениями пытается проверить подлинность клиента, не прошедшего проверку подлинности, до тех пор, пока не будет вызвано исключение при первом сбое.</span><span class="sxs-lookup"><span data-stu-id="95c79-117">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="95c79-118">Настройка службы с помощью WSHttpBinding для использования надежного сеанса</span><span class="sxs-lookup"><span data-stu-id="95c79-118">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="95c79-119">Эта процедура описана в разделе [как обмениваться сообщениями в надежном сеансе](how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="95c79-119">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="95c79-120">Настройка клиента с помощью WSHttpBinding для использования надежного сеанса</span><span class="sxs-lookup"><span data-stu-id="95c79-120">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="95c79-121">Эта процедура описана в разделе [как обмениваться сообщениями в надежном сеансе](how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="95c79-121">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="95c79-122">Установка режима и ClientCredentialType в конфигурации</span><span class="sxs-lookup"><span data-stu-id="95c79-122">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="95c79-123">Добавьте соответствующий элемент привязки в [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) элемент файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="95c79-123">Add an appropriate binding element to the [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="95c79-124">В следующем примере добавляется [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="95c79-124">The following example adds a [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="95c79-125">Добавьте **\<binding>** элемент и присвойте его `name` атрибуту соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="95c79-125">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="95c79-126">В примере используется имя `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="95c79-126">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="95c79-127">Добавьте **\<security>** элемент и присвойте `mode` атрибуту значение `Message` .</span><span class="sxs-lookup"><span data-stu-id="95c79-127">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="95c79-128">В **\<security>** элементе добавьте **\<message>** элемент и присвойте `clientCredentialType` атрибуту значение `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="95c79-128">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
