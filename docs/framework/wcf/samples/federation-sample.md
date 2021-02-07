---
description: 'Дополнительные сведения: пример Федерации'
title: Пример федерации
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: a85a290988b6cbb4b30a1098f3558ec34ead1d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704086"
---
# <a name="federation-sample"></a><span data-ttu-id="552d1-103">Пример федерации</span><span class="sxs-lookup"><span data-stu-id="552d1-103">Federation Sample</span></span>

<span data-ttu-id="552d1-104">В данном примере демонстрируется федеративная безопасность.</span><span class="sxs-lookup"><span data-stu-id="552d1-104">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="552d1-105">Подробные сведения об образце</span><span class="sxs-lookup"><span data-stu-id="552d1-105">Sample Details</span></span>  

 <span data-ttu-id="552d1-106">Windows Communication Foundation (WCF) обеспечивает поддержку развертывания федеративных архитектур безопасности с помощью `wsFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="552d1-106">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="552d1-107">Привязка `wsFederationHttpBinding` обеспечивает наличие безопасной и надежной привязки, которая поддерживает возможность взаимодействия. Данная привязка предполагает использование протокола HTTP в качестве базового транспортного механизма для взаимодействия типа "запрос-ответ" и текста/XML в качестве формата подключения для кодирования.</span><span class="sxs-lookup"><span data-stu-id="552d1-107">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="552d1-108">Дополнительные сведения о Федерации в WCF см. в разделе [Федерация](../feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="552d1-108">For more information about Federation in WCF, see [Federation](../feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="552d1-109">Сценарий состоит из 4 частей:</span><span class="sxs-lookup"><span data-stu-id="552d1-109">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="552d1-110">служба BookStore;</span><span class="sxs-lookup"><span data-stu-id="552d1-110">BookStore service</span></span>  
  
- <span data-ttu-id="552d1-111">служба маркеров безопасности BookStore;</span><span class="sxs-lookup"><span data-stu-id="552d1-111">BookStore STS</span></span>  
  
- <span data-ttu-id="552d1-112">служба маркеров безопасности HomeRealm;</span><span class="sxs-lookup"><span data-stu-id="552d1-112">HomeRealm STS</span></span>  
  
- <span data-ttu-id="552d1-113">клиент BookStore.</span><span class="sxs-lookup"><span data-stu-id="552d1-113">BookStore Client</span></span>  
  
 <span data-ttu-id="552d1-114">Служба BookStore поддерживает две операции: `BrowseBooks` и `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="552d1-114">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="552d1-115">Служба позволяет выполнять анонимный доступ к операции `BrowseBooks`, но требует доступ с проверкой подлинности к операции `BuyBooks` .</span><span class="sxs-lookup"><span data-stu-id="552d1-115">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="552d1-116">Проверка подлинности принимает форму маркера, выданного службой маркеров безопасности BookStore.</span><span class="sxs-lookup"><span data-stu-id="552d1-116">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="552d1-117">Файл конфигурации службы BookStore указывает клиентам на службу маркеров безопасности BookStore с помощью `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="552d1-117">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="552d1-118">Затем служба маркеров безопасности BookStore требует, чтобы проверка подлинности клиента выполнялась с помощью маркера, выданного службой маркеров безопасности HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="552d1-118">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="552d1-119">И снова файл конфигурации службы маркеров безопасности BookStore указывает клиентам на службу маркеров безопасности HomeRealm с помощью `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="552d1-119">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="552d1-120">Ниже приведена последовательность событий при получении доступа к операции `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="552d1-120">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="552d1-121">Клиент проходит проверку подлинности в службе маркеров безопасности HomeRealm с использованием учетных данных Windows.</span><span class="sxs-lookup"><span data-stu-id="552d1-121">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="552d1-122">Служба маркеров безопасности HomeRealm выдает маркер, который может использоваться для проверки подлинности в службе маркеров безопасности BookStore.</span><span class="sxs-lookup"><span data-stu-id="552d1-122">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="552d1-123">Клиент проходит проверку подлинности в службе маркеров безопасности BookStore с использованием маркера, выданного службой маркеров безопасности HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="552d1-123">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="552d1-124">Служба маркеров безопасности BookStore выдает маркер, который может использоваться для проверки подлинности в службе BookStore.</span><span class="sxs-lookup"><span data-stu-id="552d1-124">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="552d1-125">Клиент проходит проверку подлинности в службе BookStore с использованием маркера, выданного службой маркеров безопасности BookStore.</span><span class="sxs-lookup"><span data-stu-id="552d1-125">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="552d1-126">Клиент получает доступ к операции `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="552d1-126">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="552d1-127">В приведенных ниже инструкциях описаны настройка и запуск данного образца.</span><span class="sxs-lookup"><span data-stu-id="552d1-127">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="552d1-128">Для запуска этого образца необходимо иметь разрешения на запись в каталог **wwwroot** .</span><span class="sxs-lookup"><span data-stu-id="552d1-128">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="552d1-129">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="552d1-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="552d1-130">Откройте окно командной строки SDK.</span><span class="sxs-lookup"><span data-stu-id="552d1-130">Open the SDK command window.</span></span> <span data-ttu-id="552d1-131">Выполните Setup.bat в пути образца.</span><span class="sxs-lookup"><span data-stu-id="552d1-131">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="552d1-132">При этом будут созданы требуемые для образца виртуальные каталоги и установлены необходимые сертификаты с соответствующими разрешениями.</span><span class="sxs-lookup"><span data-stu-id="552d1-132">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="552d1-133">Пакетный файл Setup.bat предназначен для запуска из командной строки Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="552d1-133">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="552d1-134">Требуется, чтобы переменная среды MSSDK указывала на каталог, в котором установлен пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="552d1-134">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="552d1-135">Эта переменная среды автоматически устанавливается в командной строке Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="552d1-135">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="552d1-136">В Windows Vista необходимо убедиться, что установлена совместимость управления IIS 6,0, так как для установки используются сценарии администратора IIS.</span><span class="sxs-lookup"><span data-stu-id="552d1-136">On Windows Vista, you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="552d1-137">Для выполнения сценария установки в Windows Vista требуются права администратора.</span><span class="sxs-lookup"><span data-stu-id="552d1-137">Running the set-up script on Windows Vista requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="552d1-138">Откройте Федератионсампле. sln в Visual Studio и выберите в меню **Сборка** пункт **построить решение** .</span><span class="sxs-lookup"><span data-stu-id="552d1-138">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="552d1-139">При этом будут построены и развернуты в IIS общие файлы проекта, служба Bookstore, служба маркеров безопасности Bookstore, служба маркеров безопасности HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="552d1-139">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="552d1-140">Кроме того, при этом будет построено клиентское приложение Bookstore. Его исполняемый файл BookStoreClient.exe будет размещен в папке FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="552d1-140">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="552d1-141">Дважды щелкните BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="552d1-141">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="552d1-142">Отобразится окно BookStoreClient.</span><span class="sxs-lookup"><span data-stu-id="552d1-142">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="552d1-143">Чтобы просмотреть книги, доступные в книжном магазине, щелкните **Обзор книг**.</span><span class="sxs-lookup"><span data-stu-id="552d1-143">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="552d1-144">Чтобы приобрести конкретную книгу, выберите книгу в списке и щелкните **купить книгу**.</span><span class="sxs-lookup"><span data-stu-id="552d1-144">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="552d1-145">Приложение запустится и пройдет проверку подлинности с использованием проверки подлинности Windows со службой маркеров безопасности HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="552d1-145">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="552d1-146">Конфигурация данного примера позволяет пользователям приобретать книги, которые стоят 15 долларов США или меньше.</span><span class="sxs-lookup"><span data-stu-id="552d1-146">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="552d1-147">Попытка приобрести книгу, стоимость которой превышает 15 долларов США, приводит к тому, что клиент получает сообщение «Доступ запрещен» от службы Book Store.</span><span class="sxs-lookup"><span data-stu-id="552d1-147">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="552d1-148">В данном примере кредитный лимит пользователя после покупки не обновляется.</span><span class="sxs-lookup"><span data-stu-id="552d1-148">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="552d1-149">Вы можете повторно приобрести книги на сумму в пределах пользовательского (фиксированного) кредитного лимита.</span><span class="sxs-lookup"><span data-stu-id="552d1-149">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="552d1-150">Очистка</span><span class="sxs-lookup"><span data-stu-id="552d1-150">To clean up</span></span>  
  
1. <span data-ttu-id="552d1-151">Запустите Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="552d1-151">Run Cleanup.bat.</span></span> <span data-ttu-id="552d1-152">При этом будут удалены виртуальные каталоги и сертификаты, созданные во время установки.</span><span class="sxs-lookup"><span data-stu-id="552d1-152">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="552d1-153">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="552d1-153">The samples may already be installed on your machine.</span></span> <span data-ttu-id="552d1-154">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="552d1-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="552d1-155">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="552d1-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="552d1-156">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="552d1-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
