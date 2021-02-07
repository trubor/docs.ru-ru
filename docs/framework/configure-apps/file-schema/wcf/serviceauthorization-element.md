---
description: 'Дополнительные сведения о: <serviceAuthorization> element'
title: <serviceAuthorization> - элемент
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: ee447f487027ed12f829dd0fd364556ce095d7d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682934"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="b2ce4-103">Элемент \<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="b2ce4-103">\<serviceAuthorization> element</span></span>

<span data-ttu-id="b2ce4-104">Задает параметры авторизации доступа к операциям службы.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-104">Specifies settings that authorize access to service operations</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**  

## <a name="syntax"></a><span data-ttu-id="b2ce4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b2ce4-105">Syntax</span></span>

```xml
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2ce4-106">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="b2ce4-106">Attributes and elements</span></span>

<span data-ttu-id="b2ce4-107">В следующих разделах описываются атрибуты, дочерние элементы и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-107">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="b2ce4-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b2ce4-108">Attributes</span></span>

|<span data-ttu-id="b2ce4-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b2ce4-109">Attribute</span></span>|<span data-ttu-id="b2ce4-110">Описание</span><span class="sxs-lookup"><span data-stu-id="b2ce4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2ce4-111">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="b2ce4-111">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="b2ce4-112">Логическое значение, которое определяет, должны ли все операции службы олицетворять вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-112">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="b2ce4-113">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="b2ce4-114">Если конкретная операция службы олицетворяет вызывающий объект, контекст потока переключается на контекст вызывающего объекта перед выполнением указанной службы.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-114">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="b2ce4-115">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="b2ce4-115">principalPermissionMode</span></span>|<span data-ttu-id="b2ce4-116">Определяет участников, используемых для выполнения операций на сервере.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-116">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="b2ce4-117">В эти значения входят:</span><span class="sxs-lookup"><span data-stu-id="b2ce4-117">Values include the following:</span></span><br /><br /> <span data-ttu-id="b2ce4-118">— Нет</span><span class="sxs-lookup"><span data-stu-id="b2ce4-118">-   None</span></span><br /><span data-ttu-id="b2ce4-119">-Усевиндовсграупс</span><span class="sxs-lookup"><span data-stu-id="b2ce4-119">-   UseWindowsGroups</span></span><br /><span data-ttu-id="b2ce4-120">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="b2ce4-120">-   UseAspNetRoles</span></span><br /><span data-ttu-id="b2ce4-121">— Пользовательский</span><span class="sxs-lookup"><span data-stu-id="b2ce4-121">-   Custom</span></span><br /><br /> <span data-ttu-id="b2ce4-122">Значение по умолчанию - «UseWindowsGroups».</span><span class="sxs-lookup"><span data-stu-id="b2ce4-122">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="b2ce4-123">Это значение типа <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-123">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="b2ce4-124">Дополнительные сведения об использовании этого атрибута см. в разделе [как ограничить доступ с помощью класса PrincipalPermissionAttribute](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="b2ce4-124">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="b2ce4-125">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="b2ce4-125">roleProviderName</span></span>|<span data-ttu-id="b2ce4-126">Строка, указывающая имя поставщика роли, который предоставляет сведения о роли для приложения Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b2ce4-126">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="b2ce4-127">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="b2ce4-128">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="b2ce4-128">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="b2ce4-129">Строка, содержащая имя типа диспетчера авторизации служб.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-129">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="b2ce4-130">Для получения дополнительной информации см. <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-130">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="b2ce4-131">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b2ce4-131">Child elements</span></span>

|<span data-ttu-id="b2ce4-132">Элемент</span><span class="sxs-lookup"><span data-stu-id="b2ce4-132">Element</span></span>|<span data-ttu-id="b2ce4-133">Описание</span><span class="sxs-lookup"><span data-stu-id="b2ce4-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2ce4-134">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="b2ce4-134">authorizationPolicies</span></span>|<span data-ttu-id="b2ce4-135">Содержит коллекцию типов политик авторизации, которые можно добавить с помощью ключевого слова`add`.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-135">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="b2ce4-136">Каждая политика авторизации содержит один обязательный атрибут `policyType`, который имеет строковый тип.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-136">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="b2ce4-137">Данный атрибут определяет политику авторизации, которая позволяет преобразовывать один набор входных требований в другой набор требований.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-137">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="b2ce4-138">В зависимости от этого может быть предоставлено управление доступом или отказано в предоставлении управления доступом.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-138">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="b2ce4-139">Для получения дополнительной информации см. <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-139">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="b2ce4-140">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b2ce4-140">Parent elements</span></span>

|<span data-ttu-id="b2ce4-141">Элемент</span><span class="sxs-lookup"><span data-stu-id="b2ce4-141">Element</span></span>|<span data-ttu-id="b2ce4-142">Описание</span><span class="sxs-lookup"><span data-stu-id="b2ce4-142">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b2ce4-143">Содержит коллекцию параметров для поведения службы.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-143">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="b2ce4-144">Remarks</span><span class="sxs-lookup"><span data-stu-id="b2ce4-144">Remarks</span></span>

<span data-ttu-id="b2ce4-145">Этот раздел содержит элементы, влияющие на авторизацию, поставщики пользовательских ролей и олицетворение.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-145">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="b2ce4-146">Атрибут `principalPermissionMode` указывает группы пользователей, которые следует использовать при авторизации использования защищенного метода.</span><span class="sxs-lookup"><span data-stu-id="b2ce4-146">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="b2ce4-147">Значение по умолчанию - `UseWindowsGroups`. Оно указывает, что при попытке доступа к ресурсу поиск удостоверения выполняется в таких группах Windows, как «Администраторы» или «Пользователи».</span><span class="sxs-lookup"><span data-stu-id="b2ce4-147">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="b2ce4-148">Можно также указать, `UseAspNetRoles` чтобы использовать пользовательский поставщик ролей, настроенный под \<system.web> элементом, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="b2ce4-148">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

```xml
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
           type="System.Web.Security.SqlMembershipProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipProvider"
           enablePasswordRetrieval="false"
           enablePasswordReset="false"
           requiresQuestionAndAnswer="false"
           requiresUniqueEmail="true"
           passwordFormat="Hashed" />
    </providers>
  </membership>
  <!-- Other configuration code not shown. -->
</system.web>
```
  
<span data-ttu-id="b2ce4-149">В следующем коде показан объект, `roleProviderName` используемый с `principalPermissionMode` атрибутом:</span><span class="sxs-lookup"><span data-stu-id="b2ce4-149">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="b2ce4-150">Подробный пример использования этого элемента конфигурации см. в разделе [авторизация доступа к операциям службы](../../../wcf/samples/authorizing-access-to-service-operations.md) и [политикам авторизации](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="b2ce4-150">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b2ce4-151">См. также</span><span class="sxs-lookup"><span data-stu-id="b2ce4-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="b2ce4-152">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="b2ce4-152">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b2ce4-153">Авторизация доступа к операциям службы</span><span class="sxs-lookup"><span data-stu-id="b2ce4-153">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="b2ce4-154">Практическое руководство. Создание пользовательского диспетчера авторизации для службы</span><span class="sxs-lookup"><span data-stu-id="b2ce4-154">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="b2ce4-155">Практическое руководство. Ограничение доступа с использованием класса PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="b2ce4-155">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="b2ce4-156">Политика авторизации</span><span class="sxs-lookup"><span data-stu-id="b2ce4-156">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
