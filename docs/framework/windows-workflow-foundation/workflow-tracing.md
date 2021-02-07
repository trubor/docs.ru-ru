---
description: 'Дополнительные сведения: трассировка рабочего процесса'
title: Отслеживание рабочих процессов
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 6d976cce1310a072f8d1c98db138696921b382c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754853"
---
# <a name="workflow-tracing"></a><span data-ttu-id="d38c2-103">Отслеживание рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="d38c2-103">Workflow Tracing</span></span>

<span data-ttu-id="d38c2-104">Трассировка рабочего процесса позволяет получать сведения диагностики при помощи прослушивателей трассировки .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d38c2-104">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="d38c2-105">Трассировку можно включить при обнаружении проблемы в работе приложения, а затем снова отключить после разрешения проблемы.</span><span class="sxs-lookup"><span data-stu-id="d38c2-105">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="d38c2-106">Существует два способа включения трассировки отладки для рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="d38c2-106">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="d38c2-107">Можно настроить отслеживание в средстве просмотра трассировки событий либо использовать <xref:System.Diagnostics> для отправки событий трассировки в файл.</span><span class="sxs-lookup"><span data-stu-id="d38c2-107">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="d38c2-108">Включение трассировки отладки в ETW</span><span class="sxs-lookup"><span data-stu-id="d38c2-108">Enabling Debug Tracing in ETW</span></span>  

 <span data-ttu-id="d38c2-109">Для включения трассировки при помощи ETW включите канал отладки в средстве просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="d38c2-109">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1. <span data-ttu-id="d38c2-110">Перейдите в узел аналитики и журналов отладки в средстве просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="d38c2-110">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2. <span data-ttu-id="d38c2-111">В представлении в виде дерева в Просмотр событий перейдите к **Просмотр событий->журналы приложений и служб — >Microsoft->Windows->сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="d38c2-111">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="d38c2-112">Щелкните правой кнопкой мыши **сервер приложений — приложения** и выберите **вид->Показать журналы аналитики и отладки**.</span><span class="sxs-lookup"><span data-stu-id="d38c2-112">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="d38c2-113">Щелкните правой кнопкой мыши **Отладка** и выберите **Включить журнал**.</span><span class="sxs-lookup"><span data-stu-id="d38c2-113">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3. <span data-ttu-id="d38c2-114">Когда рабочий процесс запускает отладку и трассы событий выдаются в канал отладки ETW, их можно просмотреть в средстве просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="d38c2-114">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="d38c2-115">Перейдите к разделу **Просмотр событий->журналы приложений и служб->Microsoft->Windows->сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="d38c2-115">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="d38c2-116">Щелкните правой кнопкой мыши элемент **Отладка** и выберите команду **Обновить**.</span><span class="sxs-lookup"><span data-stu-id="d38c2-116">Right-click **Debug** and select **Refresh**.</span></span>  
  
4. <span data-ttu-id="d38c2-117">Размер буфера аналитической трассировки по умолчанию составляет всего 4 килобайта (КБ). Рекомендуется увеличить этот размер до 32 КБ.</span><span class="sxs-lookup"><span data-stu-id="d38c2-117">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="d38c2-118">Для этого сделайте следующее.</span><span class="sxs-lookup"><span data-stu-id="d38c2-118">To do this, perform the following steps.</span></span>  
  
    1. <span data-ttu-id="d38c2-119">Выполните следующую команду в текущем каталоге платформы (например, C:\Windows\Microsoft.NET\Framework\v4.0.21203):`wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="d38c2-119">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2. <span data-ttu-id="d38c2-120">Измените \<bufferSize> значение в файле Windows. ApplicationServer. Applications. Man на 32.</span><span class="sxs-lookup"><span data-stu-id="d38c2-120">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. <span data-ttu-id="d38c2-121">Выполните следующую команду в текущем каталоге платформы (например, C:\Windows\Microsoft.NET\Framework\v4.0.21203):`wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="d38c2-121">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d38c2-122">Если вы используете клиентский профиль платформа .NET Framework 4, сначала необходимо зарегистрировать манифест ETW, выполнив следующую команду из каталога платформа .NET Framework 4: `ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="d38c2-122">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="d38c2-123">Включение трассировки отладки при помощи System.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="d38c2-123">Enabling Debug Tracing using System.Diagnostics</span></span>  

 <span data-ttu-id="d38c2-124">Эти прослушиватели можно настроить в файле App.config приложения рабочего процесса либо в файле Web.config для службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d38c2-124">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="d38c2-125">В этом примере a <xref:System.Diagnostics.TextWriterTraceListener> настроен для сохранения данных трассировки в файл MyTraceLog.txt в текущем каталоге.</span><span class="sxs-lookup"><span data-stu-id="d38c2-125">In this example, a <xref:System.Diagnostics.TextWriterTraceListener> is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d38c2-126">См. также</span><span class="sxs-lookup"><span data-stu-id="d38c2-126">See also</span></span>

- <span data-ttu-id="d38c2-127">[Мониторинг Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d38c2-127">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="d38c2-128">[Мониторинг приложений с помощью App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d38c2-128">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
