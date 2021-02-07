---
description: Дополнительные сведения см. в статье как использовать Svcutil.exe для проверки скомпилированного кода службы.
title: Практическое руководство. Использование программы Svcutil.exe для проверки скомпилированного кода службы
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: b68cdeb61ac1f42cacdcf7d1468623acb8542abe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734169"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="6f712-103">Практическое руководство. Использование программы Svcutil.exe для проверки скомпилированного кода службы</span><span class="sxs-lookup"><span data-stu-id="6f712-103">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>

<span data-ttu-id="6f712-104">Можно использовать [средство служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) для обнаружения ошибок в реализациях и конфигурациях служб без размещения службы.</span><span class="sxs-lookup"><span data-stu-id="6f712-104">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="6f712-105">Проверка службы</span><span class="sxs-lookup"><span data-stu-id="6f712-105">To validate a service</span></span>  
  
1. <span data-ttu-id="6f712-106">Скомпилируйте службу в исполняемый файл и одну или более зависимых сборок.</span><span class="sxs-lookup"><span data-stu-id="6f712-106">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2. <span data-ttu-id="6f712-107">Откройте окно командной строки SDK.</span><span class="sxs-lookup"><span data-stu-id="6f712-107">Open an SDK command prompt</span></span>  
  
3. <span data-ttu-id="6f712-108">Из командной строки запустите средство Svcutil.exe, используя следующий формат.</span><span class="sxs-lookup"><span data-stu-id="6f712-108">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="6f712-109">Дополнительные сведения о различных параметрах см. в разделе Service Валидатионсектион [(Svcutil.exe) средства служебной программы метаданных ServiceModel](../servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="6f712-109">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```console
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="6f712-110">Чтобы указать имя конфигурации службы для проверки, необходимо использовать параметр `/serviceName`.</span><span class="sxs-lookup"><span data-stu-id="6f712-110">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="6f712-111">Аргумент `assemblyPath` задает путь к исполняемому файлу для службы и одной или более сборок, которые содержат типы службы для проверки.</span><span class="sxs-lookup"><span data-stu-id="6f712-111">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="6f712-112">Исполняемая сборка должна содержать связанный файл конфигурации для предоставления конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="6f712-112">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="6f712-113">Для предоставления нескольких сборок можно использовать стандартные подстановочные знаки командной строки.</span><span class="sxs-lookup"><span data-stu-id="6f712-113">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f712-114">Пример</span><span class="sxs-lookup"><span data-stu-id="6f712-114">Example</span></span>  

 <span data-ttu-id="6f712-115">Следующая команда проверяет службу myServiceName, реализованную в исполняемом файле myServiceHost.exe.</span><span class="sxs-lookup"><span data-stu-id="6f712-115">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="6f712-116">Автоматически загружается файл конфигурации для этой службы (myServiceHost.exe.config).</span><span class="sxs-lookup"><span data-stu-id="6f712-116">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```console  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f712-117">См. также</span><span class="sxs-lookup"><span data-stu-id="6f712-117">See also</span></span>

- [<span data-ttu-id="6f712-118">Служебное средство ServiceModel Metadata Utility Tool (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="6f712-118">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
