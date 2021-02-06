---
description: Дополнительные сведения о том, как использовать моникер службы с контрактами обмена метаданными.
title: Практическое руководство. Использование моникера службы с контрактами обмена метаданными
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 220132a10cb637be9e3724232d0ddaf80a13551a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643102"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="65fa5-103">Практическое руководство. Использование моникера службы с контрактами обмена метаданными</span><span class="sxs-lookup"><span data-stu-id="65fa5-103">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>

<span data-ttu-id="65fa5-104">После разработки некоторых новых служб WCF вы можете решить, что они могут вызывать эти службы из сценария или приложения Visual Basic 6,0.</span><span class="sxs-lookup"><span data-stu-id="65fa5-104">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="65fa5-105">Одним из способов является создание клиентской сборки WCF, регистрация сборки в COM, установка сборки в GAC, а также ссылки на типы COM из кода Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="65fa5-105">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="65fa5-106">При распространении приложения потребуется также распространять клиентскую сборку WCF.</span><span class="sxs-lookup"><span data-stu-id="65fa5-106">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="65fa5-107">Затем пользователь должен будет зарегистрировать клиентскую сборку WCF с помощью COM и разместить ее в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="65fa5-107">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="65fa5-108">COM-взаимодействие WCF также позволяет выполнять одни и те же вызовы служб, не полагаясь на клиентскую сборку WCF.</span><span class="sxs-lookup"><span data-stu-id="65fa5-108">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="65fa5-109">Моникер WCF позволяет вызывать любую службу WCF из любого совместимого с COM языка (Visual Basic, VBScript, Visual Basic для приложений (VBA) и т. д.), указывая URI конечной точки обмена метаданными (MEX), который используется моникером службы для извлечения сведений о типе службы.</span><span class="sxs-lookup"><span data-stu-id="65fa5-109">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="65fa5-110">В этом разделе описывается, как вызвать пример начало работы WCF с помощью моникера WCF, который указывает конечную точку обмена метаданными.</span><span class="sxs-lookup"><span data-stu-id="65fa5-110">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65fa5-111">Типы, определенные клиентской сборкой WCF, никогда не создаются.</span><span class="sxs-lookup"><span data-stu-id="65fa5-111">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="65fa5-112">Сборка используется только для метаданных.</span><span class="sxs-lookup"><span data-stu-id="65fa5-112">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="65fa5-113">Использование моникера службы с адресом обмена метаданными (Mex)</span><span class="sxs-lookup"><span data-stu-id="65fa5-113">Using the service moniker with a Mex address</span></span>  
  
1. <span data-ttu-id="65fa5-114">Создайте пример начало работы и используйте Internet Explorer, чтобы перейти к своему URL-адресу ( `http://localhost/ServiceModelSamples/Service.svc` ), чтобы убедиться, что служба работает.</span><span class="sxs-lookup"><span data-stu-id="65fa5-114">Build the Getting Started sample and use Internet Explorer to browse to its URL (`http://localhost/ServiceModelSamples/Service.svc`) to ensure that the service is working.</span></span>  
  
2. <span data-ttu-id="65fa5-115">Создайте скрипт Visual Basic или приложение Visual Basic, содержащее следующий код:</span><span class="sxs-lookup"><span data-stu-id="65fa5-115">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```vb
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="65fa5-116">Запустите приложение или скрипт Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="65fa5-116">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="65fa5-117">Вызываемая служба должна экспонировать конечную точку обмена метаданными (Mex) в моникер, чтобы прочитать метаданные из службы.</span><span class="sxs-lookup"><span data-stu-id="65fa5-117">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="65fa5-118">Дополнительные сведения см. [в разделе инструкции. Публикация метаданных для службы с помощью файла конфигурации](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="65fa5-118">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="65fa5-119">Если моникер сформирован неправильно или служба недоступна, при вызове `GetObject` будет возвращена ошибка "Синтаксическая ошибка".</span><span class="sxs-lookup"><span data-stu-id="65fa5-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="65fa5-120">При получении этой ошибки убедитесь, что используется правильный моникер, а служба доступна.</span><span class="sxs-lookup"><span data-stu-id="65fa5-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65fa5-121">См. также</span><span class="sxs-lookup"><span data-stu-id="65fa5-121">See also</span></span>

- [<span data-ttu-id="65fa5-122">Практическое руководство. Использование моникера службы Windows Communication Foundation без регистрации</span><span class="sxs-lookup"><span data-stu-id="65fa5-122">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="65fa5-123">Практическое руководство. Использование моникера службы с контрактами WSDL</span><span class="sxs-lookup"><span data-stu-id="65fa5-123">How to: Use a Service Moniker with WSDL Contracts</span></span>](how-to-use-a-service-moniker-with-wsdl-contracts.md)
