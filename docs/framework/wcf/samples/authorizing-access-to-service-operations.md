---
description: 'Дополнительные сведения: авторизация доступа к операциям службы'
title: Авторизация доступа к операциям службы
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 052adc6104b75884c90c266e2e0e7a045032c457
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732700"
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="cb3f9-103">Авторизация доступа к операциям службы</span><span class="sxs-lookup"><span data-stu-id="cb3f9-103">Authorizing Access to Service Operations</span></span>

<span data-ttu-id="cb3f9-104">В этом примере показано, как использовать [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) атрибут, чтобы разрешить использование <xref:System.Security.Permissions.PrincipalPermissionAttribute> атрибута для авторизации доступа к операциям службы.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-104">This sample demonstrates how to use the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="cb3f9-105">Этот пример основан на образце [Начало работы](getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="cb3f9-105">This sample is based on the [Getting Started](getting-started-sample.md) sample.</span></span> <span data-ttu-id="cb3f9-106">Служба и клиент настраиваются с помощью [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="cb3f9-106">The service and client are configured using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="cb3f9-107">`mode`Атрибут [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) имеет значение `Message` и было `clientCredentialType` установлено в значение `Windows` .</span><span class="sxs-lookup"><span data-stu-id="cb3f9-107">The `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="cb3f9-108">К каждому методу службы применяется <xref:System.Security.Permissions.PrincipalPermissionAttribute> и используется для ограничения доступа к каждой операции.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-108">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="cb3f9-109">Чтобы получить доступ к каждой операции, вызывающий объект должен быть администратором Windows.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-109">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="cb3f9-110">В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb3f9-111">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cb3f9-112">Файл конфигурации службы использует [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) для задания `principalPermissionMode` атрибута:</span><span class="sxs-lookup"><span data-stu-id="cb3f9-112">The service configuration file uses the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="cb3f9-113">Настройка `principalPermissionMode` как `UseWindowsGroups` позволяет использовать <xref:System.Security.Permissions.PrincipalPermissionAttribute> на основе имен групп Windows.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-113">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="cb3f9-114"><xref:System.Security.Permissions.PrincipalPermissionAttribute> применяется к каждой операции, чтобы вызывающий объект входил в группу администраторов Windows, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-114">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="cb3f9-115">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="cb3f9-116">Клиент успешно связывается с каждой операцией, если он работает в учетной записи, входящей в группу «Администраторы». В противном случае доступ запрещен.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-116">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="cb3f9-117">Чтобы поэкспериментировать со сбоем авторизации, запустите клиент в учетной записи, не входящей в группу "Администраторы".</span><span class="sxs-lookup"><span data-stu-id="cb3f9-117">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="cb3f9-118">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-118">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="cb3f9-119">Службу можно уведомить о сбоях авторизации, реализовав <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-119">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="cb3f9-120">Сведения о реализации см. в разделе [расширение управления обработкой ошибок и создание отчетов](extending-control-over-error-handling-and-reporting.md) `IErrorHandler` .</span><span class="sxs-lookup"><span data-stu-id="cb3f9-120">See [Extending Control Over Error Handling and Reporting](extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cb3f9-121">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="cb3f9-121">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cb3f9-122">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb3f9-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cb3f9-123">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb3f9-123">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cb3f9-124">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb3f9-124">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
