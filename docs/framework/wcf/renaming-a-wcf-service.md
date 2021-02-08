---
description: 'Дополнительные сведения: переименование службы WCF'
title: Переименование службы WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 8d75e43f4bda97e8ee6de34b039eb1236d6c4a6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779170"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="b8ce0-103">Переименование службы WCF</span><span class="sxs-lookup"><span data-stu-id="b8ce0-103">Renaming a WCF Service</span></span>

<span data-ttu-id="b8ce0-104">В этом разделе описывается, как можно переименовать службу Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b8ce0-104">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="b8ce0-105">Переименование службы WCF</span><span class="sxs-lookup"><span data-stu-id="b8ce0-105">Renaming a WCF Service</span></span>  

 <span data-ttu-id="b8ce0-106">Чтобы переименовать службу в шаблоне Windows Communication Foundation (WCF), выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="b8ce0-106">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="b8ce0-107">Измените имя класса, реализующего службу.</span><span class="sxs-lookup"><span data-stu-id="b8ce0-107">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="b8ce0-108">В файле конфигурации службы измените имя службы на новое выбранное имя, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b8ce0-108">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="b8ce0-109">В зависимости от модели размещения файлом конфигурации может быть файл app.config или файл web.config.</span><span class="sxs-lookup"><span data-stu-id="b8ce0-109">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="b8ce0-110">Если служба размещена на веб-узле, то она использует *\* SVC* -файл.</span><span class="sxs-lookup"><span data-stu-id="b8ce0-110">If your service is webhosted, it uses an *\*.svc* file.</span></span> <span data-ttu-id="b8ce0-111">Откройте SVC-файл и измените имя службы, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b8ce0-111">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="b8ce0-112">Этот шаг необязателен для резидентных приложений, так как у них нет SVC-файла.</span><span class="sxs-lookup"><span data-stu-id="b8ce0-112">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="b8ce0-113">Переименование контракта службы WCF</span><span class="sxs-lookup"><span data-stu-id="b8ce0-113">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="b8ce0-114">Выполните следующие действия для переименования контракта службы.</span><span class="sxs-lookup"><span data-stu-id="b8ce0-114">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="b8ce0-115">Измените имя контракта службы.</span><span class="sxs-lookup"><span data-stu-id="b8ce0-115">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="b8ce0-116">В файле конфигурации службы измените имя контракта службы на новое выбранное имя, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b8ce0-116">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="b8ce0-117">В зависимости от модели размещения файлом конфигурации может быть файл app.config или файл web.config.</span><span class="sxs-lookup"><span data-stu-id="b8ce0-117">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
