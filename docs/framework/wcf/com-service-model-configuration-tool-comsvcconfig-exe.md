---
description: 'Дополнительные сведения: средство настройки модели службы COM+ (ComSvcConfig.exe)'
title: Программа командной строки настройки модели служб COM+ (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 81bfcbd468cb5401646a49967b6381b48e2f7cf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781068"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="531dc-103">Программа командной строки настройки модели служб COM+ (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="531dc-103">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>

<span data-ttu-id="531dc-104">Программа командной строки для настройки модели служб COM+ (ComSvcConfig.exe) позволяет настраивать интерфейсы COM+, которые нужно предоставить как веб-службы.</span><span class="sxs-lookup"><span data-stu-id="531dc-104">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="531dc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="531dc-105">Syntax</span></span>  
  
```console  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="531dc-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="531dc-106">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="531dc-107">Для использования ComSvcConfig.exe на компьютере под управлением ОС Windows Vista требуются права администратора.</span><span class="sxs-lookup"><span data-stu-id="531dc-107">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="531dc-108">Это средство можно найти в следующей папке:</span><span class="sxs-lookup"><span data-stu-id="531dc-108">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="531dc-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="531dc-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
 <span data-ttu-id="531dc-110">Дополнительные сведения о ComSvcConfig.exe см. в разделе [как использовать средство настройки модели службы COM+](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="531dc-110">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="531dc-111">В следующей таблице представлены режимы, которые могут использоваться с ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="531dc-111">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="531dc-112">Параметр</span><span class="sxs-lookup"><span data-stu-id="531dc-112">Option</span></span>|<span data-ttu-id="531dc-113">Описание</span><span class="sxs-lookup"><span data-stu-id="531dc-113">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="531dc-114">Устанавливает конфигурацию для интерфейса COM+ для интеграции Service Model.</span><span class="sxs-lookup"><span data-stu-id="531dc-114">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="531dc-115">Краткая форма: `/i`.</span><span class="sxs-lookup"><span data-stu-id="531dc-115">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="531dc-116">Удаляет конфигурацию для интерфейса COM+ из интеграции Service Model.</span><span class="sxs-lookup"><span data-stu-id="531dc-116">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="531dc-117">Краткая форма: `/u`.</span><span class="sxs-lookup"><span data-stu-id="531dc-117">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="531dc-118">Отображает сведения о приложениях и компонентах COM+, которые имеют интерфейсы, настроенные для интеграции Service Model.</span><span class="sxs-lookup"><span data-stu-id="531dc-118">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="531dc-119">Краткая форма: `/l`.</span><span class="sxs-lookup"><span data-stu-id="531dc-119">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="531dc-120">В следующей таблице представлены флаги, которые могут использоваться с ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="531dc-120">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="531dc-121">Параметр</span><span class="sxs-lookup"><span data-stu-id="531dc-121">Option</span></span>|<span data-ttu-id="531dc-122">Описание</span><span class="sxs-lookup"><span data-stu-id="531dc-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="531dc-123">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="531dc-123">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="531dc-124">Позволяет указать приложение COM+ для настройки.</span><span class="sxs-lookup"><span data-stu-id="531dc-124">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="531dc-125">Краткая форма: `/a`.</span><span class="sxs-lookup"><span data-stu-id="531dc-125">Short form `/a`.</span></span>|  
|<span data-ttu-id="531dc-126">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="531dc-126">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="531dc-127">Позволяет указать компонент и интерфейс COM+, которые будут настроены в качестве контракта для службы.</span><span class="sxs-lookup"><span data-stu-id="531dc-127">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="531dc-128">Краткая форма: `/c`.</span><span class="sxs-lookup"><span data-stu-id="531dc-128">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="531dc-129">Хотя подстановочный знак ( \* ) можно использовать при указании имен компонентов и интерфейсов, рекомендуется не использовать его, поскольку вы можете предоставлять интерфейсы, которые не планировались.</span><span class="sxs-lookup"><span data-stu-id="531dc-129">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="531dc-130">`/hosting:` \<*complus*  &#124; *was*\></span><span class="sxs-lookup"><span data-stu-id="531dc-130">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="531dc-131">Позволяет указать необходимость использования режима размещения COM+ или режима размещения на веб-сервере.</span><span class="sxs-lookup"><span data-stu-id="531dc-131">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="531dc-132">Краткая форма: `/h`.</span><span class="sxs-lookup"><span data-stu-id="531dc-132">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="531dc-133">Для использования режима размещения COM+ требуется явная активация приложения COM+.</span><span class="sxs-lookup"><span data-stu-id="531dc-133">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="531dc-134">Использование режима размещения на веб-сервере позволяет автоматически активировать приложение COM+ при необходимости.</span><span class="sxs-lookup"><span data-stu-id="531dc-134">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="531dc-135">Если приложение COM+ является библиотечным приложением, оно выполняется в процессе IIS.</span><span class="sxs-lookup"><span data-stu-id="531dc-135">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="531dc-136">Если приложение COM+ является серверным приложением, оно выполняется в процессе Dllhost.exe.</span><span class="sxs-lookup"><span data-stu-id="531dc-136">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="531dc-137">`/webSite:` \<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="531dc-137">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="531dc-138">Позволяет указать веб-сайт для размещения при использовании режима размещения на веб-сервере (см. флаг `/hosting`).</span><span class="sxs-lookup"><span data-stu-id="531dc-138">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="531dc-139">Краткая форма: `/w`.</span><span class="sxs-lookup"><span data-stu-id="531dc-139">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="531dc-140">Если веб-сайт не указан, используется веб-сайт по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="531dc-140">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="531dc-141">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="531dc-141">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="531dc-142">Позволяет указать виртуальный каталог для размещения при использовании режима размещения на веб-сервере (см. флаг `/hosting`).</span><span class="sxs-lookup"><span data-stu-id="531dc-142">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="531dc-143">Краткая форма: `/d`.</span><span class="sxs-lookup"><span data-stu-id="531dc-143">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="531dc-144">Добавляет конечную точку службы обмена метаданными в конфигурацию службы по умолчанию для поддержки клиентов, которым требуется извлечь определение контракта из службы.</span><span class="sxs-lookup"><span data-stu-id="531dc-144">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="531dc-145">Краткая форма: `/x`.</span><span class="sxs-lookup"><span data-stu-id="531dc-145">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="531dc-146">Отображает информацию о приложении, компоненте и интерфейсе в виде идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="531dc-146">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="531dc-147">Краткая форма: `/k`.</span><span class="sxs-lookup"><span data-stu-id="531dc-147">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="531dc-148">Подавляет отображение логотипа ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="531dc-148">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="531dc-149">Краткая форма: `/n`.</span><span class="sxs-lookup"><span data-stu-id="531dc-149">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="531dc-150">Выводит все предупреждения или информационный текст в дополнение к любым обнаруженным ошибкам.</span><span class="sxs-lookup"><span data-stu-id="531dc-150">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="531dc-151">Краткая форма: `/v`.</span><span class="sxs-lookup"><span data-stu-id="531dc-151">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="531dc-152">Отображает сообщение об использовании.</span><span class="sxs-lookup"><span data-stu-id="531dc-152">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="531dc-153">Краткая форма: `/?`.</span><span class="sxs-lookup"><span data-stu-id="531dc-153">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="531dc-154">Создает конфигурацию службы, если указанный интерфейс включает одну или несколько сигнатур метода, которые могут быть предоставлены для использования.</span><span class="sxs-lookup"><span data-stu-id="531dc-154">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="531dc-155">Во время инициализации службы совместимые методы отображаются как операции над контрактом службы, а несовместимые методы игнорируются и исключаются из контракта службы.</span><span class="sxs-lookup"><span data-stu-id="531dc-155">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="531dc-156">Если данный флаг отсутствует, средство не создает конфигурацию службы, когда указанный интерфейс включает один или несколько несовместимых методов.</span><span class="sxs-lookup"><span data-stu-id="531dc-156">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="531dc-157">Примеры</span><span class="sxs-lookup"><span data-stu-id="531dc-157">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="531dc-158">Описание</span><span class="sxs-lookup"><span data-stu-id="531dc-158">Description</span></span>  

 <span data-ttu-id="531dc-159">В следующем примере с помощью режима размещения COM+ выполняется добавление интерфейса `IFinances` компонента `ItemOrders.IFinancial` (из приложения COM+ OnlineStore) в набор интерфейсов, предоставляемых как веб-службы.</span><span class="sxs-lookup"><span data-stu-id="531dc-159">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="531dc-160">В дополнение к любым обнаруженным ошибкам выводятся все предупреждения.</span><span class="sxs-lookup"><span data-stu-id="531dc-160">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="531dc-161">Код</span><span class="sxs-lookup"><span data-stu-id="531dc-161">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="531dc-162">Описание</span><span class="sxs-lookup"><span data-stu-id="531dc-162">Description</span></span>  

 <span data-ttu-id="531dc-163">В следующем примере с помощью режима размещения на веб-сервере выполняется добавление интерфейса `IStockLevels` компонента `ItemInventory.Warehouse` (из приложения COM+ OnlineWarehouse) в набор интерфейсов, предоставляемых как веб-службы.</span><span class="sxs-lookup"><span data-stu-id="531dc-163">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="531dc-164">Веб-служба размещается в виртуальном каталоге OnlineWarehouse в IIS.</span><span class="sxs-lookup"><span data-stu-id="531dc-164">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="531dc-165">Код</span><span class="sxs-lookup"><span data-stu-id="531dc-165">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="531dc-166">Описание</span><span class="sxs-lookup"><span data-stu-id="531dc-166">Description</span></span>  

 <span data-ttu-id="531dc-167">В следующем примере выполняется удаление интерфейса `IFinances` компонента `ItemOrders.Financial` (из приложения COM+ OnlineStore) из набора интерфейсов, предоставляемых как веб-службы.</span><span class="sxs-lookup"><span data-stu-id="531dc-167">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="531dc-168">Код</span><span class="sxs-lookup"><span data-stu-id="531dc-168">Code</span></span>  
  
```console  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="531dc-169">Описание</span><span class="sxs-lookup"><span data-stu-id="531dc-169">Description</span></span>  

 <span data-ttu-id="531dc-170">В следующем примере выводится список предоставляемых в данный момент интерфейсов, размещенных в COM+, а также соответствующий адрес и сведения о привязке для приложения COM+ OnlineStore на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="531dc-170">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="531dc-171">Код</span><span class="sxs-lookup"><span data-stu-id="531dc-171">Code</span></span>  
  
```console  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="531dc-172">См. также</span><span class="sxs-lookup"><span data-stu-id="531dc-172">See also</span></span>

- [<span data-ttu-id="531dc-173">Практическое руководство. Использование программы командной строки настройки модели служб COM+</span><span class="sxs-lookup"><span data-stu-id="531dc-173">How to: Use the COM+ Service Model Configuration Tool</span></span>](./feature-details/how-to-use-the-com-service-model-configuration-tool.md)
