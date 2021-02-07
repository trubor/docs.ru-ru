---
description: Дополнительные сведения см. в статье как использовать средство настройки модели службы COM+.
title: Практическое руководство. Использование программы командной строки настройки модели служб COM+
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 2047604f327cd871629bbdac403e9acd816bbdb1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734091"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="0f8b7-103">Практическое руководство. Использование программы командной строки настройки модели служб COM+</span><span class="sxs-lookup"><span data-stu-id="0f8b7-103">How to: Use the COM+ Service Model Configuration Tool</span></span>

<span data-ttu-id="0f8b7-104">Выбрав нужный режим размещения, с помощью программы командной строки настройки модели служб COM+ (ComSvcConfig.exe) сконфигурируйте интерфейсы приложения, предоставляемые как веб-службы.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-104">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>

> [!NOTE]
> <span data-ttu-id="0f8b7-105">Для выполнения каждой из следующих задач необходимо быть администратором компьютера.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-105">You must be an administrator on the machine to perform any of the following tasks.</span></span>

 <span data-ttu-id="0f8b7-106">При использовании ComSvcConfig.exe на компьютере под управлением Windows 7 для настройки веб-службы на использование последней версии модели службы (в настоящее время v4.5) выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-106">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>

1. <span data-ttu-id="0f8b7-107">Присвойте разделу реестра  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` значение DWORD 0x00000001.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-107">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>

2. <span data-ttu-id="0f8b7-108">Запустите comsvcconfig.exe</span><span class="sxs-lookup"><span data-stu-id="0f8b7-108">Run comsvcconfig.exe</span></span>

3. <span data-ttu-id="0f8b7-109">Верните ключу реестра, добавленному на шаге 1, исходное значение или удалите его, если нет.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-109">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f8b7-110">Восстановление значения ключа - важно.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-110">Reverting this registry key is important.</span></span> <span data-ttu-id="0f8b7-111">Это ключ совместимости.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-111">This is a compatibility key.</span></span> <span data-ttu-id="0f8b7-112">Если не восстановить значение ключа, могут возникнуть проблемы в работе других приложений .NET на данном компьютере.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-112">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>

> [!WARNING]
> <span data-ttu-id="0f8b7-113">При использовании ComSvcConfig.exe/Install на компьютере под управлением Windows 8 появляется диалоговое окно "для приложения на вашем компьютере требуется следующая функция Windows: платформа .NET Framework 3,5 (включая .NET 2,0 и .NET 3,0", если платформа .NET Framework 3,5 не установлен.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-113">When using ComSvcConfig.exe  /install on a Windows 8 machine, a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="0f8b7-114">Это диалоговое окно можно пропустить.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-114">This dialog may be ignored.</span></span> <span data-ttu-id="0f8b7-115">В качестве альтернативы можно задать ключу реестра OnlyUseLatestCLR значение DWORD 0x00000001</span><span class="sxs-lookup"><span data-stu-id="0f8b7-115">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>

## <a name="add-an-interface-using-the-com-hosting-mode"></a><span data-ttu-id="0f8b7-116">Добавление интерфейса с помощью режима размещения COM+</span><span class="sxs-lookup"><span data-stu-id="0f8b7-116">Add an interface using the COM+ hosting mode</span></span>

- <span data-ttu-id="0f8b7-117">Выполните программу ComSvcConfig с параметрами `/install` и `/hosting:complus`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-117">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose
    ```

     <span data-ttu-id="0f8b7-118">Эта команда добавляет интерфейс `IFinances` компонента `ItemOrders.IFinancial` (из приложения COM+ OnlineStore) в набор интерфейсов, предоставляемых как веб-службы.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-118">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="0f8b7-119">Данная служба использует режим размещения COM+, а потому для нее требуется явное включение приложения.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-119">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>

     <span data-ttu-id="0f8b7-120">Хотя символ-звездочка ( \* ) можно использовать для компонента и интерфейса, старайтесь не использовать его, так как может потребоваться предоставить только выбранные функциональные возможности в качестве Web Service.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-120">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="0f8b7-121">При использовании с более новой версией компонента подстановочный знак может (вопреки замыслу разработчика) предоставить интерфейсы, отсутствовавшие на момент определения синтаксиса конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-121">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>

     <span data-ttu-id="0f8b7-122">При использовании параметра /verbose программа отображает предупреждения (помимо ошибок).</span><span class="sxs-lookup"><span data-stu-id="0f8b7-122">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>

     <span data-ttu-id="0f8b7-123">Контракт для предоставленной службы содержит все методы интерфейса `IFinances`.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-123">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>

## <a name="add-specific-methods-from-an-interface-using-the-com-hosting-mode"></a><span data-ttu-id="0f8b7-124">Добавление конкретных методов из интерфейса с помощью режима размещения COM+</span><span class="sxs-lookup"><span data-stu-id="0f8b7-124">Add specific methods from an interface using the COM+ hosting mode</span></span>

- <span data-ttu-id="0f8b7-125">Запустите программу ComSvcConfig с параметрами `/install` и `/hosting:complus`, явно указав имена требуемых методов, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-125">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose
    ```

     <span data-ttu-id="0f8b7-126">Эта команда добавляет только методы `Credit` и `Debit` из интерфейса `IFinances` как операции в контракт предоставляемой службы.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-126">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="0f8b7-127">Все прочие методы интерфейса не добавляются в контракт и не вызываются клиентами веб-службы.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-127">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>

## <a name="add-an-interface-using-the-web-hosting-mode"></a><span data-ttu-id="0f8b7-128">Добавление интерфейса с помощью режима размещения в Интернете</span><span class="sxs-lookup"><span data-stu-id="0f8b7-128">Add an interface using the Web hosting mode</span></span>

- <span data-ttu-id="0f8b7-129">Выполните программу ComSvcConfig с параметрами `/install` и `/hosting:was`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-129">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose
    ```

     <span data-ttu-id="0f8b7-130">Эта команда добавляет интерфейс `IStockLevels` компонента `ItemInventory.Warehouse` (из приложения COM+ OnlineWarehouse) в набор интерфейсов, предоставляемых как веб-службы.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-130">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="0f8b7-131">Служба размещается на веб-сервере в виртуальном каталоге OnlineWarehouse службы IIS, а не COM+, а потому приложение включается автоматически по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-131">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>

     <span data-ttu-id="0f8b7-132">Чтобы воспользоваться конфигурацией с внутрипроцессным размещением на веб-сервере, приложение COM+ необходимо настроить для запуска как библиотечное приложение, а не серверное (с помощью консоли администрирования "Службы компонентов").</span><span class="sxs-lookup"><span data-stu-id="0f8b7-132">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="0f8b7-133">Приложения, настроенные как серверные, используют стандартный режим размещения на веб-сервере, что приводит к переходам процесса при обработке каждого запроса.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-133">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>

     <span data-ttu-id="0f8b7-134">Параметр `/mex` добавляет дополнительную конечную точку службы обмена метаданными (MEX), использующую тот же транспорт, что и конечная точка службы приложения, для поддержки клиентов, которым требуется извлечь определение контракта от службы.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-134">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>

## <a name="remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="0f8b7-135">Удаление веб-службы для указанного интерфейса</span><span class="sxs-lookup"><span data-stu-id="0f8b7-135">Remove a Web service for a specified interface</span></span>

- <span data-ttu-id="0f8b7-136">Выполните программу ComSvcConfig с параметром `/uninstall`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-136">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus
    ```

     <span data-ttu-id="0f8b7-137">Эта команда удаляет интерфейс `IFinances` компонента `ItemOrders.Financial` (из приложения COM+ OnlineStore).</span><span class="sxs-lookup"><span data-stu-id="0f8b7-137">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>

## <a name="list-currently-exposed-interfaces"></a><span data-ttu-id="0f8b7-138">Список предоставляемых в настоящее время интерфейсов</span><span class="sxs-lookup"><span data-stu-id="0f8b7-138">List currently exposed interfaces</span></span>

- <span data-ttu-id="0f8b7-139">Выполните программу ComSvcConfig с параметром `/list`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-139">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /list
    ```

     <span data-ttu-id="0f8b7-140">Эта команда выводит список предоставляемых в данный момент интерфейсов, а также соответствующий адрес и сведения о привязке, областью действия которых является локальный компьютер.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-140">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>

## <a name="list-specific-currently-exposed-interfaces"></a><span data-ttu-id="0f8b7-141">Вывод списка конкретных предоставляемых в данный момент интерфейсов</span><span class="sxs-lookup"><span data-stu-id="0f8b7-141">List specific currently exposed interfaces</span></span>

- <span data-ttu-id="0f8b7-142">Выполните программу ComSvcConfig с параметром `/list`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-142">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus
    ```

     <span data-ttu-id="0f8b7-143">Эта команда выводит список предоставляемых в данный момент интерфейсов, размещенных в COM+, а также соответствующий адрес и сведения о привязке для приложения COM+ OnlineStore на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-143">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>

## <a name="display-help-for-options"></a><span data-ttu-id="0f8b7-144">Отображение справки по параметрам</span><span class="sxs-lookup"><span data-stu-id="0f8b7-144">Display help for options</span></span>

- <span data-ttu-id="0f8b7-145">Запустите программу ComSvcConfig с параметром /?</span><span class="sxs-lookup"><span data-stu-id="0f8b7-145">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="0f8b7-146">как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-146">option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /?
    ```

## <a name="see-also"></a><span data-ttu-id="0f8b7-147">См. также</span><span class="sxs-lookup"><span data-stu-id="0f8b7-147">See also</span></span>

- [<span data-ttu-id="0f8b7-148">Общие сведения об интеграции с приложениями COM+</span><span class="sxs-lookup"><span data-stu-id="0f8b7-148">Integrating with COM+ Applications Overview</span></span>](integrating-with-com-plus-applications-overview.md)
