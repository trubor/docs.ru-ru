---
description: Дополнительные сведения см. в статье Создание примеров Windows Communication Foundation
title: Построение примеров Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: a53073ac92369574b204dbce998bebb8844fce8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704190"
---
# <a name="building-the-windows-communication-foundation-samples"></a><span data-ttu-id="d6681-103">Построение примеров Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d6681-103">Building the Windows Communication Foundation Samples</span></span>

<span data-ttu-id="d6681-104">Примеры Windows Communication Foundation (WCF) можно построить с помощью Visual Studio IDE или с помощью команды **MSBuild** из командной строки.</span><span class="sxs-lookup"><span data-stu-id="d6681-104">The Windows Communication Foundation (WCF) samples can be built using the Visual Studio IDE or using the **msbuild** command from the command line.</span></span> <span data-ttu-id="d6681-105">В этом разделе описаны обе эти процедуры.</span><span class="sxs-lookup"><span data-stu-id="d6681-105">Both procedures are described in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="d6681-106">Перед сборкой или запуском любого из примеров WCF убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d6681-106">Before building or running any of the WCF samples, ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

## <a name="to-build-the-sample-using-a-command-prompt"></a><span data-ttu-id="d6681-107">Сборка образца с использованием командной строки</span><span class="sxs-lookup"><span data-stu-id="d6681-107">To build the sample using a command prompt</span></span>

1. <span data-ttu-id="d6681-108">Откройте Командная строка разработчика для Visual Studio и перейдите к вложенному каталогу, зависящему от языка, в папке, в которой был установлен пример.</span><span class="sxs-lookup"><span data-stu-id="d6681-108">Open Developer Command Prompt for Visual Studio and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="d6681-109">Введите `msbuild` в командной строке.</span><span class="sxs-lookup"><span data-stu-id="d6681-109">Type `msbuild` at the command line.</span></span> <span data-ttu-id="d6681-110">Файлы клиентской программы создаются в *клиент\бин* , а файлы служебной программы — в *сервице\бин*.</span><span class="sxs-lookup"><span data-stu-id="d6681-110">The client program files are built to *client\bin* and the service program files are built to *service\bin*.</span></span> <span data-ttu-id="d6681-111">Если служба размещена службы IIS (IIS), файлы служебной программы также копируются в каталог *servicemodelsamples* и в подкаталог *\bin* .</span><span class="sxs-lookup"><span data-stu-id="d6681-111">If the service is hosted by Internet Information Services (IIS), the service program files are also copied to the *servicemodelsamples* directory and its *\bin* subdirectory.</span></span>

> [!NOTE]
> <span data-ttu-id="d6681-112">Необходимо задать списки управления доступом на *%системдриве%\инетпуб\ввврут* , чтобы предоставить разрешения на изменение учетной записи, под которой выполняется.</span><span class="sxs-lookup"><span data-stu-id="d6681-112">You must set the ACLs on *%systemdrive%\inetpub\wwwroot* to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="d6681-113">В противном случае некоторые события построения могут завершиться сбоем.</span><span class="sxs-lookup"><span data-stu-id="d6681-113">Otherwise some post build events fail.</span></span> <span data-ttu-id="d6681-114">Либо можно оставить списки управления доступом неизменными и запускать командную строку пакета SDK от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="d6681-114">Alternatively, you can leave the ACLs as they are and run the SDK command prompt as administrator.</span></span>

## <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="d6681-115">Сборка образца с использованием Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d6681-115">To build the sample using Visual Studio</span></span>

1. <span data-ttu-id="d6681-116">В меню **файл** в Visual Studio выберите пункт **Открыть**  >  **проект или решение**.</span><span class="sxs-lookup"><span data-stu-id="d6681-116">From the **File** menu in Visual Studio, select **Open** > **Project/Solution**.</span></span> <span data-ttu-id="d6681-117">Перейдите в подкаталог, зависящий от языка, в каталоге, в котором был установлен образец, и дважды щелкните значок SLN-файла, чтобы открыть решение в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d6681-117">Navigate to the language-specific subdirectory under the directory in which you installed the sample, and double-click the .sln file icon to open the solution in Visual Studio.</span></span>

1. <span data-ttu-id="d6681-118">В меню **Сборка** выберите **Перестроить решение**.</span><span class="sxs-lookup"><span data-stu-id="d6681-118">From the **Build** menu, select **Rebuild Solution**.</span></span>

   <span data-ttu-id="d6681-119">Файлы построения клиентской программы сохраняются в папке client\bin, а файлы построения служебной программы - в папке service\bin.</span><span class="sxs-lookup"><span data-stu-id="d6681-119">The client program files are built to client\bin and the service program files are built to service\bin.</span></span> <span data-ttu-id="d6681-120">Если служба размещена в службах IIS, файлы служебной программы также копируются в каталог *servicemodelsamples* и в подкаталог *\bin* .</span><span class="sxs-lookup"><span data-stu-id="d6681-120">If the service is hosted in IIS, the service program files are also copied to the *servicemodelsamples* directory and its *\bin* subdirectory.</span></span>

> [!NOTE]
> <span data-ttu-id="d6681-121">Необходимо задать списки управления доступом для каталога %systemdrive%\inetpub\wwwroot, чтобы предоставить разрешения на изменение учетной записи, от имени которой выполняются операции.</span><span class="sxs-lookup"><span data-stu-id="d6681-121">You must set the ACLs on %systemdrive%\inetpub\wwwroot to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="d6681-122">В противном случае некоторые события построения могут завершиться сбоем.</span><span class="sxs-lookup"><span data-stu-id="d6681-122">Otherwise some post build events fail.</span></span> <span data-ttu-id="d6681-123">Либо можно оставить списки управления доступом неизменными и запускать командную строку SDK или Visual Studio от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="d6681-123">Alternatively, you can leave the ACLs as they are and run the SDK command prompt or Visual Studio as administrator.</span></span> <span data-ttu-id="d6681-124">Некоторые действия Visual Studio (например, присоединение отладчика к рабочему процессу ASP.NET) также требуют прав администратора.</span><span class="sxs-lookup"><span data-stu-id="d6681-124">Some Visual Studio actions (such as attaching a debugger to the ASP.NET worker process) also require administrative privileges.</span></span>

## <a name="setup-batch-files-and-scripts"></a><span data-ttu-id="d6681-125">Пакетные файлы и скрипты установки</span><span class="sxs-lookup"><span data-stu-id="d6681-125">Setup Batch Files and Scripts</span></span>

 <span data-ttu-id="d6681-126">Setup.exe и Cleanup.exe пакетные файлы и скрипты следует запускать из Командная строка разработчика для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d6681-126">Setup.exe and Cleanup.exe batch files and scripts should be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="d6681-127">Некоторые файлы установки и очистки выполняют задачи, требующие прав администратора, и должны запускаться с этими правами.</span><span class="sxs-lookup"><span data-stu-id="d6681-127">Several set up and clean up files perform tasks that require administrative privileges and should be launched with administrator privileges.</span></span>

## <a name="important-security-information-about-metadata-endpoints"></a><span data-ttu-id="d6681-128">Важные сведения по безопасности конечных точек метаданных</span><span class="sxs-lookup"><span data-stu-id="d6681-128">Important Security Information about Metadata Endpoints</span></span>

 <span data-ttu-id="d6681-129">Чтобы предотвратить непреднамеренное раскрытие потенциально конфиденциальных метаданных службы, конфигурация по умолчанию для служб Windows Communication Foundation (WCF) отключает публикацию метаданных.</span><span class="sxs-lookup"><span data-stu-id="d6681-129">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="d6681-130">Такое расширение функциональности по умолчанию защищено, но это также означает, что при этом невозможно использовать средство импорта метаданных (например, Svcutil.exe) для создания клиентского кода, необходимого для вызова службы, если поведение публикации не включено явно в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d6681-130">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="d6681-131">Чтобы испытывать образец было проще, почти все образцы предоставляют незащищенную конечную точку публикации метаданных.</span><span class="sxs-lookup"><span data-stu-id="d6681-131">To make experimenting with the samples easier, almost all samples expose an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="d6681-132">Такие конечные точки являются потенциально доступными для анонимных не прошедших проверку подлинности потребителей, поэтому перед развертыванием таких конечных точек следует соблюдать осторожность и убедиться, что публичное раскрытие метаданных службы уместно.</span><span class="sxs-lookup"><span data-stu-id="d6681-132">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="d6681-133">Дополнительные сведения о публикации метаданных службы см. в статье пример [поведения публикации метаданных](metadata-publishing-behavior.md) .</span><span class="sxs-lookup"><span data-stu-id="d6681-133">For more information about publishing service metadata, see the [Metadata Publishing Behavior](metadata-publishing-behavior.md) sample.</span></span> <span data-ttu-id="d6681-134">Пример защиты конечной точки метаданных см. в примере [пользовательской конечной точки защищенных метаданных](custom-secure-metadata-endpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="d6681-134">See the [Custom Secure Metadata Endpoint](custom-secure-metadata-endpoint.md) sample for a sample securing a metadata endpoint.</span></span>

## <a name="exception-handling"></a><span data-ttu-id="d6681-135">Обработка исключений</span><span class="sxs-lookup"><span data-stu-id="d6681-135">Exception Handling</span></span>

 <span data-ttu-id="d6681-136">В целом эти образцы не включают обработку исключений для того, чтобы код был сконцентрирован на теме образца.</span><span class="sxs-lookup"><span data-stu-id="d6681-136">Generally speaking these samples do not include exception handling to keep the code focused on the subject of the sample.</span></span> <span data-ttu-id="d6681-137">Дополнительные сведения об обработке исключений см. в разделе пример [ожидаемых исключений](expected-exceptions.md) .</span><span class="sxs-lookup"><span data-stu-id="d6681-137">For more information about exception handling, see the [Expected Exceptions](expected-exceptions.md) sample.</span></span>

## <a name="regenerating-clients-and-configuration-with-svcutil"></a><span data-ttu-id="d6681-138">Восстановление клиентов и конфигурации с помощью средства Svcutil</span><span class="sxs-lookup"><span data-stu-id="d6681-138">Regenerating Clients and Configuration with Svcutil</span></span>

 <span data-ttu-id="d6681-139">Чтобы повторно создать код клиента и конфигурацию для большинства примеров, можно использовать [средство служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="d6681-139">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to regenerate client code and configuration for most of the samples.</span></span> <span data-ttu-id="d6681-140">Некоторые образцах требуют редактирования конфигурации вручную.</span><span class="sxs-lookup"><span data-stu-id="d6681-140">Some samples require manually edited configuration.</span></span> <span data-ttu-id="d6681-141">Например, если средство Svcutil.exe используется для восстановления конфигурации образца, использующего учетные данные сертификата клиента, необходимо вручную указать ранее заданные учетные данные.</span><span class="sxs-lookup"><span data-stu-id="d6681-141">For example, if you use Svcutil.exe to regenerate the configuration for a sample that uses client certificate credentials, you must manually specify the credentials previously configured.</span></span> <span data-ttu-id="d6681-142">В некоторых образцах используются особые параметры средства Svcutil.exe, влияющие на создаваемый код; эти параметры описаны в соответствующих разделах образце.</span><span class="sxs-lookup"><span data-stu-id="d6681-142">Some samples use specific Svcutil.exe options to affect the generated code, these options are specified in the specific sample topics.</span></span>

### <a name="to-regenerate-the-client-and-configuration-files"></a><span data-ttu-id="d6681-143">Восстановление клиента и файлов конфигурации</span><span class="sxs-lookup"><span data-stu-id="d6681-143">To regenerate the client and configuration files</span></span>

1. <span data-ttu-id="d6681-144">Откройте окно командной строки SDK и перейдите к языковому подкаталогу в каталоге, где установлен образец.</span><span class="sxs-lookup"><span data-stu-id="d6681-144">Open an SDK command prompt and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="d6681-145">Если служба размещается на веб-сервере, воспользуйтесь следующей командой.</span><span class="sxs-lookup"><span data-stu-id="d6681-145">If the service is a Web-hosted type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     <span data-ttu-id="d6681-146">Если служба размещается резидентно, воспользуйтесь следующей командой.</span><span class="sxs-lookup"><span data-stu-id="d6681-146">If the service is a self-hosted type the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     <span data-ttu-id="d6681-147">Замените на `http://localhost:8000/ServiceModelSamples/service.svc/mex` адрес конечной точки обмена метаданными саморазмещенной службы.</span><span class="sxs-lookup"><span data-stu-id="d6681-147">Replace `http://localhost:8000/ServiceModelSamples/service.svc/mex` with the address of the self-hosted service's mex endpoint.</span></span>

     <span data-ttu-id="d6681-148">Чтобы создать клиент на языке Visual Basic, воспользуйтесь следующей командой.</span><span class="sxs-lookup"><span data-stu-id="d6681-148">To generate the client in a Visual Basic type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     <span data-ttu-id="d6681-149">Если служба размещается резидентно, воспользуйтесь следующей командой.</span><span class="sxs-lookup"><span data-stu-id="d6681-149">If the service is a self-hosted type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > <span data-ttu-id="d6681-150">Чтобы пропустить создание конфигурации клиента, добавьте параметр **/noconfig** .</span><span class="sxs-lookup"><span data-stu-id="d6681-150">To skip the generation of client configuration add the **/noConfig** option.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6681-151">См. также</span><span class="sxs-lookup"><span data-stu-id="d6681-151">See also</span></span>

- [<span data-ttu-id="d6681-152">Выполнение примеров Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d6681-152">Running the Windows Communication Foundation Samples</span></span>](running-the-samples.md)
- [<span data-ttu-id="d6681-153">Служебное средство ServiceModel Metadata Utility Tool (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d6681-153">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
