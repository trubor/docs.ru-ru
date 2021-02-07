---
description: Дополнительные сведения см. в статье как указать тип учетных данных клиента.
title: Практическое руководство. Указание типа учетных данных клиента
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: f6536778e8814a1b5a4c03e22c0fe4108f89b6eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752539"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="97bf2-103">Практическое руководство. Указание типа учетных данных клиента</span><span class="sxs-lookup"><span data-stu-id="97bf2-103">How to: Specify the Client Credential Type</span></span>

<span data-ttu-id="97bf2-104">После установки режима безопасности (на уровне транспорта или сообщений) можно установить тип учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="97bf2-104">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="97bf2-105">Это свойство определяет тип учетных данных, которые клиент должен предоставить службе для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="97bf2-105">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="97bf2-106">Дополнительные сведения о настройке режима безопасности (необходимого шага перед настройкой типа учетных данных клиента) см. [в разделе как задать режим безопасности](how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="97bf2-106">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="97bf2-107">Установка типа учетных данных клиента в коде</span><span class="sxs-lookup"><span data-stu-id="97bf2-107">To set the client credential type in code</span></span>  
  
1. <span data-ttu-id="97bf2-108">Создайте экземпляр привязки, который будет использовать служба.</span><span class="sxs-lookup"><span data-stu-id="97bf2-108">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="97bf2-109">В этом примере используется привязка <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="97bf2-109">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2. <span data-ttu-id="97bf2-110">Присвойте свойству <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="97bf2-110">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="97bf2-111">В этом примере используется режим Message.</span><span class="sxs-lookup"><span data-stu-id="97bf2-111">This example uses the Message mode.</span></span>  
  
3. <span data-ttu-id="97bf2-112">Присвойте свойству <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="97bf2-112">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="97bf2-113">В этом примере используется проверка подлинности Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span><span class="sxs-lookup"><span data-stu-id="97bf2-113">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="97bf2-114">Установка типа учетных данных клиента в файле конфигурации</span><span class="sxs-lookup"><span data-stu-id="97bf2-114">To set the client credential type in configuration</span></span>  
  
1. <span data-ttu-id="97bf2-115">Добавьте [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) элемент в файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="97bf2-115">Add a [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2. <span data-ttu-id="97bf2-116">Добавьте элемент в качестве дочернего элемента [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="97bf2-116">As a child element, add a [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3. <span data-ttu-id="97bf2-117">Добавьте соответствующую привязку.</span><span class="sxs-lookup"><span data-stu-id="97bf2-117">Add an appropriate binding.</span></span> <span data-ttu-id="97bf2-118">В этом примере используется [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="97bf2-118">This example uses the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4. <span data-ttu-id="97bf2-119">Добавьте [\<binding>](../configure-apps/file-schema/wcf/bindings.md) элемент и присвойте `name` атрибуту соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="97bf2-119">Add a [\<binding>](../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="97bf2-120">В этом примере используется имя "SecureBinding".</span><span class="sxs-lookup"><span data-stu-id="97bf2-120">This example uses the name "SecureBinding".</span></span>  
  
5. <span data-ttu-id="97bf2-121">Добавьте привязку `<security>`.</span><span class="sxs-lookup"><span data-stu-id="97bf2-121">Add a `<security>` binding.</span></span> <span data-ttu-id="97bf2-122">Присвойте атрибуту `mode` соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="97bf2-122">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="97bf2-123">В данном примере используется значение `"Message"`.</span><span class="sxs-lookup"><span data-stu-id="97bf2-123">This example sets it to `"Message"`.</span></span>  
  
6. <span data-ttu-id="97bf2-124">Добавьте элемент `<message>` или `<transport>` в зависимости от режима безопасности.</span><span class="sxs-lookup"><span data-stu-id="97bf2-124">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="97bf2-125">Присвойте атрибуту `clientCredentialType` соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="97bf2-125">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="97bf2-126">В этом примере используется `"Windows"`.</span><span class="sxs-lookup"><span data-stu-id="97bf2-126">This example uses `"Windows"`.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="97bf2-127">См. также</span><span class="sxs-lookup"><span data-stu-id="97bf2-127">See also</span></span>

- [<span data-ttu-id="97bf2-128">Защита служб</span><span class="sxs-lookup"><span data-stu-id="97bf2-128">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="97bf2-129">Практическое руководство. Задание режима безопасности</span><span class="sxs-lookup"><span data-stu-id="97bf2-129">How to: Set the Security Mode</span></span>](how-to-set-the-security-mode.md)
