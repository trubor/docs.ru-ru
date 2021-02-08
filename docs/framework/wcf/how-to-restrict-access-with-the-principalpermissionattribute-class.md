---
description: Дополнительные сведения см. в статье как ограничить доступ с помощью класса PrincipalPermissionAttribute.
title: Практическое руководство. Ограничение доступа с использованием класса PrincipalPermissionAttribute
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: 533bd3358d5e337071c6419264d1dac03b8987ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779352"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="1adde-103">Практическое руководство. Ограничение доступа с использованием класса PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="1adde-103">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>

<span data-ttu-id="1adde-104">Управление доступом к ресурсам компьютера Windows-домена - это базовая задача обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="1adde-104">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="1adde-105">Например, только определенные пользователи должны иметь возможность просматривать конфиденциальные данные, такие как платежные ведомости.</span><span class="sxs-lookup"><span data-stu-id="1adde-105">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="1adde-106">В этом разделе рассматривается, как ограничить доступ к методу, потребовав, чтобы пользователь принадлежал к заранее заданной группе.</span><span class="sxs-lookup"><span data-stu-id="1adde-106">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="1adde-107">Рабочий пример см. в разделе [авторизация доступа к операциям службы](./samples/authorizing-access-to-service-operations.md).</span><span class="sxs-lookup"><span data-stu-id="1adde-107">For a working sample, see [Authorizing Access to Service Operations](./samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="1adde-108">Эта задача состоит из двух отдельных процедур.</span><span class="sxs-lookup"><span data-stu-id="1adde-108">The task consists of two separate procedures.</span></span> <span data-ttu-id="1adde-109">Первая создает группу и заносит в нее пользователей.</span><span class="sxs-lookup"><span data-stu-id="1adde-109">The first creates the group and populates it with users.</span></span> <span data-ttu-id="1adde-110">Вторая применяет класс <xref:System.Security.Permissions.PrincipalPermissionAttribute>, чтобы задать группу.</span><span class="sxs-lookup"><span data-stu-id="1adde-110">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="1adde-111">Создание группы Windows</span><span class="sxs-lookup"><span data-stu-id="1adde-111">To create a Windows group</span></span>  
  
1. <span data-ttu-id="1adde-112">Откройте консоль **управления компьютером** .</span><span class="sxs-lookup"><span data-stu-id="1adde-112">Open the **Computer Management** console.</span></span>  
  
2. <span data-ttu-id="1adde-113">На панели слева щелкните **Локальные пользователи и группы**.</span><span class="sxs-lookup"><span data-stu-id="1adde-113">In the left panel, click **Local Users and Groups**.</span></span>  
  
3. <span data-ttu-id="1adde-114">Щелкните правой кнопкой мыши элемент **группы** и выберите команду **создать группу**.</span><span class="sxs-lookup"><span data-stu-id="1adde-114">Right-click **Groups**, and click **New Group**.</span></span>  
  
4. <span data-ttu-id="1adde-115">В поле **имя группы** введите имя новой группы.</span><span class="sxs-lookup"><span data-stu-id="1adde-115">In the **Group Name** box, type a name for the new group.</span></span>  
  
5. <span data-ttu-id="1adde-116">В поле **Описание** введите описание новой группы.</span><span class="sxs-lookup"><span data-stu-id="1adde-116">In the **Description** box, type a description of the new group.</span></span>  
  
6. <span data-ttu-id="1adde-117">Нажмите кнопку **Добавить** , чтобы добавить новых членов в группу.</span><span class="sxs-lookup"><span data-stu-id="1adde-117">Click the **Add** button to add new members to the group.</span></span>  
  
7. <span data-ttu-id="1adde-118">Если вы добавили себя в группу и хотите протестировать приведенный ниже код, необходимо выйти из системы и снова войти в нее, чтобы быть включенным в группу.</span><span class="sxs-lookup"><span data-stu-id="1adde-118">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="1adde-119">Требование членства пользователя</span><span class="sxs-lookup"><span data-stu-id="1adde-119">To demand user membership</span></span>  
  
1. <span data-ttu-id="1adde-120">Откройте файл кода Windows Communication Foundation (WCF), содержащий реализованный код контракта службы.</span><span class="sxs-lookup"><span data-stu-id="1adde-120">Open the Windows Communication Foundation (WCF) code file that contains the implemented service contract code.</span></span> <span data-ttu-id="1adde-121">Дополнительные сведения о реализации контракта см. в разделе [реализация контрактов служб](implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="1adde-121">For more information about implementing a contract, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="1adde-122">Примените атрибут <xref:System.Security.Permissions.PrincipalPermissionAttribute> к каждому методу, доступ к которому необходимо ограничить определенной группой.</span><span class="sxs-lookup"><span data-stu-id="1adde-122">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="1adde-123">Задайте для свойства <xref:System.Security.Permissions.SecurityAttribute.Action%2A> значение <xref:System.Security.Permissions.SecurityAction.Demand>, а для свойства <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> задайте имя группы.</span><span class="sxs-lookup"><span data-stu-id="1adde-123">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="1adde-124">Пример:</span><span class="sxs-lookup"><span data-stu-id="1adde-124">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="1adde-125">Если применить атрибут <xref:System.Security.Permissions.PrincipalPermissionAttribute> к контракту, возникает исключение <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="1adde-125">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="1adde-126">Этот атрибут может применяться только на уровне метода.</span><span class="sxs-lookup"><span data-stu-id="1adde-126">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="1adde-127">Использование сертификата для управления доступом к методу</span><span class="sxs-lookup"><span data-stu-id="1adde-127">Using a Certificate to Control Access to a Method</span></span>  

 <span data-ttu-id="1adde-128">Для управления доступом к методу можно также использовать класс `PrincipalPermissionAttribute`, если типом учетных данных клиента является сертификат.</span><span class="sxs-lookup"><span data-stu-id="1adde-128">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="1adde-129">Для этого необходимо иметь субъект и отпечаток сертификата.</span><span class="sxs-lookup"><span data-stu-id="1adde-129">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="1adde-130">Сведения о проверке сертификата для его свойств см. в разделе [как просматривать сертификаты с помощью оснастки MMC](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="1adde-130">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="1adde-131">Чтобы найти значение отпечатка, см. статью [как получить отпечаток сертификата](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="1adde-131">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="1adde-132">Управление доступом с помощью сертификата</span><span class="sxs-lookup"><span data-stu-id="1adde-132">To control access using a certificate</span></span>  
  
1. <span data-ttu-id="1adde-133">Примените класс <xref:System.Security.Permissions.PrincipalPermissionAttribute> к методу, доступ к которому требуется ограничить.</span><span class="sxs-lookup"><span data-stu-id="1adde-133">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2. <span data-ttu-id="1adde-134">Задайте для действия атрибута значение <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1adde-134">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3. <span data-ttu-id="1adde-135">Задайте для свойства `Name` строку, состоящую из имени субъект и отпечатка сертификата.</span><span class="sxs-lookup"><span data-stu-id="1adde-135">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="1adde-136">Эти два значения должны разделяться точкой с запятой и пробелом, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="1adde-136">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. <span data-ttu-id="1adde-137">Задайте для свойства <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> значение <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, как показано в следующем примере конфигурации:</span><span class="sxs-lookup"><span data-stu-id="1adde-137">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="1adde-138">Задание для этого параметра значения `UseAspNetRoles` означает, что свойство `Name` атрибута `PrincipalPermissionAttribute` будет использоваться для строкового сравнения.</span><span class="sxs-lookup"><span data-stu-id="1adde-138">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="1adde-139">Если сертификат используется в качестве учетных данных клиента, по умолчанию WCF объединяет общее имя сертификата и отпечаток с точкой с запятой, чтобы создать уникальное значение для первичного удостоверения клиента.</span><span class="sxs-lookup"><span data-stu-id="1adde-139">When a certificate is used as a client credential, by default WCF concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="1adde-140">Если в службе для режима `UseAspNetRoles` задано значение `PrincipalPermissionMode`, для определения прав доступа пользователя это значение первичной идентификации сравнивается со значением свойства `Name`.</span><span class="sxs-lookup"><span data-stu-id="1adde-140">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="1adde-141">При создании резидентной службы можно также задать свойство <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> в коде, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="1adde-141">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="1adde-142">См. также</span><span class="sxs-lookup"><span data-stu-id="1adde-142">See also</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [<span data-ttu-id="1adde-143">Авторизация доступа к операциям службы</span><span class="sxs-lookup"><span data-stu-id="1adde-143">Authorizing Access to Service Operations</span></span>](./samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="1adde-144">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="1adde-144">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="1adde-145">Реализация контрактов служб</span><span class="sxs-lookup"><span data-stu-id="1adde-145">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
