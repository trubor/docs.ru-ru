---
description: 'Дополнительные сведения о: службы IIS (IIS) инструкции по установке сертификата сервера'
title: Инструкции по установке сертификата сервера в службах IIS
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 1ac5209e9ff82911b0631c190e16ff457fea0db6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631857"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="8e40c-103">Инструкции по установке сертификата сервера в службах IIS</span><span class="sxs-lookup"><span data-stu-id="8e40c-103">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>

<span data-ttu-id="8e40c-104">Чтобы запускать примеры, которые безопасным образом взаимодействуют со службами IIS, необходимо создать и установить сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="8e40c-104">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="8e40c-105">Шаг 1.</span><span class="sxs-lookup"><span data-stu-id="8e40c-105">Step 1.</span></span> <span data-ttu-id="8e40c-106">Создание сертификатов</span><span class="sxs-lookup"><span data-stu-id="8e40c-106">Creating Certificates</span></span>  

 <span data-ttu-id="8e40c-107">Чтобы создать сертификат для компьютера, откройте Командная строка разработчика для Visual Studio с правами администратора и запустите Setup.bat, включенный в каждый из примеров, использующих безопасное соединение с IIS.</span><span class="sxs-lookup"><span data-stu-id="8e40c-107">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="8e40c-108">Перед запуском пакетного файла убедитесь, что путь включает папку, содержащую программу Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="8e40c-108">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="8e40c-109">Следующая команда служит для создания сертификата в файле Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="8e40c-109">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```console  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="8e40c-110">Шаг 2.</span><span class="sxs-lookup"><span data-stu-id="8e40c-110">Step 2.</span></span> <span data-ttu-id="8e40c-111">Установка сертификатов</span><span class="sxs-lookup"><span data-stu-id="8e40c-111">Installing Certificates</span></span>  

 <span data-ttu-id="8e40c-112">Шаги, необходимые для установки созданных сертификатов, зависят от используемой версии IIS.</span><span class="sxs-lookup"><span data-stu-id="8e40c-112">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="8e40c-113">Установка IIS в IIS 5.1 (Windows XP) и IIS 6.0 (Windows Server 2003)</span><span class="sxs-lookup"><span data-stu-id="8e40c-113">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1. <span data-ttu-id="8e40c-114">Откройте оснастку консоли MMC диспетчера служб IIS.</span><span class="sxs-lookup"><span data-stu-id="8e40c-114">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2. <span data-ttu-id="8e40c-115">Щелкните правой кнопкой мыши веб-сайт по умолчанию и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="8e40c-115">Right-click the default Web site and select **Properties**.</span></span>  
  
3. <span data-ttu-id="8e40c-116">Перейдите на вкладку **Безопасность каталога** .</span><span class="sxs-lookup"><span data-stu-id="8e40c-116">Select the **Directory Security** tab.</span></span>  
  
4. <span data-ttu-id="8e40c-117">Нажмите кнопку **сертификат сервера** .</span><span class="sxs-lookup"><span data-stu-id="8e40c-117">Click the **Server Certificate** button.</span></span> <span data-ttu-id="8e40c-118">Будет запущен мастер сертификатов веб-сервера.</span><span class="sxs-lookup"><span data-stu-id="8e40c-118">The Web Server Certificate Wizard starts.</span></span>  
  
5. <span data-ttu-id="8e40c-119">Завершите работу мастера.</span><span class="sxs-lookup"><span data-stu-id="8e40c-119">Complete the wizard.</span></span> <span data-ttu-id="8e40c-120">Выберите назначение сертификата.</span><span class="sxs-lookup"><span data-stu-id="8e40c-120">Select the option to assign a certificate.</span></span> <span data-ttu-id="8e40c-121">Из отображаемого списка сертификатов выберите сертификат ServiceModelSamples-HTTPS-Server.</span><span class="sxs-lookup"><span data-stu-id="8e40c-121">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="8e40c-122">![Мастер сертификатов IIS](media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="8e40c-122">![IIS Certificate Wizard](media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6. <span data-ttu-id="8e40c-123">Проверьте доступ к службе в браузере с помощью адреса HTTPS `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="8e40c-123">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="8e40c-124">Если до этого был настроен протокол SSL с помощью Httpcfg.exe</span><span class="sxs-lookup"><span data-stu-id="8e40c-124">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1. <span data-ttu-id="8e40c-125">С помощью программы Makecert.exe (или запустив файл Setup.bat) создайте сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="8e40c-125">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2. <span data-ttu-id="8e40c-126">Запустите диспетчер IIS и установите сертификат в соответствии с описанными выше действиями.</span><span class="sxs-lookup"><span data-stu-id="8e40c-126">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3. <span data-ttu-id="8e40c-127">Добавьте следующую строку кода в клиентскую программу.</span><span class="sxs-lookup"><span data-stu-id="8e40c-127">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8e40c-128">Этот код необходим только для тестовых сертификатов, наподобие созданных с помощью Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="8e40c-128">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="8e40c-129">Для кода производственного назначения это делать не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="8e40c-129">It is not recommended for production code.</span></span>  
  
```csharp  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="8e40c-130">Установка IIS в IIS 7.0 (Windows Vista и Windows Server 2008)</span><span class="sxs-lookup"><span data-stu-id="8e40c-130">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1. <span data-ttu-id="8e40c-131">В меню **Пуск** выберите пункт **выполнить**, а затем введите **inetmgr** , чтобы открыть оснастку MMC службы IIS (IIS).</span><span class="sxs-lookup"><span data-stu-id="8e40c-131">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="8e40c-132">Щелкните правой кнопкой мыши **веб-сайт по умолчанию** и выберите **изменить привязки...**</span><span class="sxs-lookup"><span data-stu-id="8e40c-132">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3. <span data-ttu-id="8e40c-133">Нажмите кнопку " **Добавить** " в диалоговом окне " **привязки сайта** ".</span><span class="sxs-lookup"><span data-stu-id="8e40c-133">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4. <span data-ttu-id="8e40c-134">В раскрывающемся списке **Тип** выберите **HTTPS** .</span><span class="sxs-lookup"><span data-stu-id="8e40c-134">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5. <span data-ttu-id="8e40c-135">Выберите **servicemodelsamples-HTTPS-Server** из раскрывающегося списка **SSL-сертификат** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="8e40c-135">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6. <span data-ttu-id="8e40c-136">Проверьте доступ к службе в браузере с помощью адреса HTTPS `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="8e40c-136">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e40c-137">Поскольку только что установленный тестовый сертификат не является доверенным сертификатом, при переходе по локальным веб-адресам, защищенным с помощью этого сертификата, могут появиться дополнительные предупреждения системы безопасности Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8e40c-137">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="8e40c-138">Удаление сертификатов</span><span class="sxs-lookup"><span data-stu-id="8e40c-138">Removing Certificates</span></span>  
  
- <span data-ttu-id="8e40c-139">Выполните с помощью диспетчера служб IIS действия, описанные выше, но вместо добавления сертификата или привязки удалите их.</span><span class="sxs-lookup"><span data-stu-id="8e40c-139">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
- <span data-ttu-id="8e40c-140">Удалите сертификат компьютера с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="8e40c-140">Remove the computer certificate by using the following command.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
