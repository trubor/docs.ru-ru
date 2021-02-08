---
description: Дополнительные сведения см. в статье возможности безопасности с помощью пользовательских привязок.
title: Возможности безопасности при использовании пользовательских привязок
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 0d4298bcb0b22d607c4abb15d879e3b093394bad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779846"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="d95e7-103">Возможности безопасности при использовании пользовательских привязок</span><span class="sxs-lookup"><span data-stu-id="d95e7-103">Security Capabilities with Custom Bindings</span></span>

<span data-ttu-id="d95e7-104">Основные задачи обеспечения безопасности можно выполнить, используя одну из предоставляемых системой привязок.</span><span class="sxs-lookup"><span data-stu-id="d95e7-104">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="d95e7-105">Однако при необходимости в дополнительных элементах управления можно создать пользовательскую привязку с помощью элемента <xref:System.ServiceModel.Channels.SecurityBindingElement>, следуя объяснениям в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="d95e7-105">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="d95e7-106">Дополнительные сведения о пользовательских привязках см. в разделе [пользовательские привязки](../extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="d95e7-106">For more information about custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d95e7-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="d95e7-107">In This Section</span></span>  

 [<span data-ttu-id="d95e7-108">Режимы проверки подлинности SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d95e7-108">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="d95e7-109">Содержит описание режимов проверки подлинности, которые возможны для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="d95e7-109">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="d95e7-110">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d95e7-110">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="d95e7-111">Содержит описание основных шагов, которые необходимо предпринять для создания пользовательской привязки к элементу безопасности.</span><span class="sxs-lookup"><span data-stu-id="d95e7-111">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="d95e7-112">Практическое руководство. Создание SecurityBindingElement для заданного режима проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="d95e7-112">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="d95e7-113">Описывается, как создать элемент безопасности для заданного режима проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="d95e7-113">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="d95e7-114">Практическое руководство. Порядок отключения безопасных сеансов в WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d95e7-114">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="d95e7-115">Описывается, как отключить безопасные сеансы при создании службы федерации.</span><span class="sxs-lookup"><span data-stu-id="d95e7-115">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="d95e7-116">Практическое руководство. Включение обнаружения повтора сообщений</span><span class="sxs-lookup"><span data-stu-id="d95e7-116">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="d95e7-117">Описывается, как определить, когда будет осуществлена атака воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="d95e7-117">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="d95e7-118">Практическое руководство. Создание подтверждающих учетных данных</span><span class="sxs-lookup"><span data-stu-id="d95e7-118">How to: Create a Supporting Credential</span></span>](how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="d95e7-119">Описывается, как предоставить службе подтверждающие учетные данные при необходимости.</span><span class="sxs-lookup"><span data-stu-id="d95e7-119">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="d95e7-120">Практическое руководство. Настройка подтверждения сигнатуры</span><span class="sxs-lookup"><span data-stu-id="d95e7-120">How to: Set Up a Signature Confirmation</span></span>](how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="d95e7-121">Содержит описание шагов, которые необходимо предпринять для подтверждения подписей при использовании цифровых подписей сообщений.</span><span class="sxs-lookup"><span data-stu-id="d95e7-121">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="d95e7-122">Практическое руководство. Установка максимальной разницы в показаниях часов</span><span class="sxs-lookup"><span data-stu-id="d95e7-122">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="d95e7-123">Описывается, как настроить максимально допустимую разницу во времени между службой и клиентом.</span><span class="sxs-lookup"><span data-stu-id="d95e7-123">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="d95e7-124">Практическое руководство. Выключение шифрования цифровых сигнатур</span><span class="sxs-lookup"><span data-stu-id="d95e7-124">How to: Disable Encryption of Digital Signatures</span></span>](how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="d95e7-125">Описывается, как отключение шифрования цифровых подписей может увеличить производительность.</span><span class="sxs-lookup"><span data-stu-id="d95e7-125">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d95e7-126">Справочник</span><span class="sxs-lookup"><span data-stu-id="d95e7-126">Reference</span></span>  

 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="d95e7-127">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="d95e7-127">Related Sections</span></span>  

 [<span data-ttu-id="d95e7-128">Основные сведения об уровне защиты</span><span class="sxs-lookup"><span data-stu-id="d95e7-128">Understanding Protection Level</span></span>](../understanding-protection-level.md)  
  
 [<span data-ttu-id="d95e7-129">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="d95e7-129">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="d95e7-130">См. также</span><span class="sxs-lookup"><span data-stu-id="d95e7-130">See also</span></span>

- [<span data-ttu-id="d95e7-131">Привязки и безопасность</span><span class="sxs-lookup"><span data-stu-id="d95e7-131">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="d95e7-132">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="d95e7-132">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="d95e7-133">Привязки, предоставляемые системой</span><span class="sxs-lookup"><span data-stu-id="d95e7-133">System-Provided Bindings</span></span>](../system-provided-bindings.md)
