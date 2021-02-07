---
description: 'Дополнительные сведения о: Аппдомаининфо'
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 1e527f2a25c48a3bf35d974e3ac192d937a8a86e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757973"
---
# <a name="appdomaininfo"></a><span data-ttu-id="0e94c-103">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="0e94c-103">AppDomainInfo</span></span>

<span data-ttu-id="0e94c-104">Сведения о домене приложения</span><span class="sxs-lookup"><span data-stu-id="0e94c-104">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e94c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0e94c-105">Syntax</span></span>  
  
```csharp
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0e94c-106">Методы</span><span class="sxs-lookup"><span data-stu-id="0e94c-106">Methods</span></span>  

 <span data-ttu-id="0e94c-107">Класс AppDomainInfo не определяет никакие методы.</span><span class="sxs-lookup"><span data-stu-id="0e94c-107">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0e94c-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="0e94c-108">Properties</span></span>  

 <span data-ttu-id="0e94c-109">Класс AppDomainInfo имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="0e94c-109">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="0e94c-110">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="0e94c-110">AppDomainId</span></span>  

 <span data-ttu-id="0e94c-111">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="0e94c-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="0e94c-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="0e94c-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0e94c-113">Идентификатор домена приложения.</span><span class="sxs-lookup"><span data-stu-id="0e94c-113">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="0e94c-114">IsDefault</span><span class="sxs-lookup"><span data-stu-id="0e94c-114">IsDefault</span></span>  

 <span data-ttu-id="0e94c-115">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="0e94c-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="0e94c-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="0e94c-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0e94c-117">Указывает, является ли домен приложения доменом приложения, используемым по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0e94c-117">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="0e94c-118">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="0e94c-118">LogMalformedMessages</span></span>  

 <span data-ttu-id="0e94c-119">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="0e94c-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="0e94c-120">Тип доступа: чтение/запись</span><span class="sxs-lookup"><span data-stu-id="0e94c-120">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="0e94c-121">Значение, указывающее, заносятся ли в журнал неправильные сообщения.</span><span class="sxs-lookup"><span data-stu-id="0e94c-121">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="0e94c-122">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="0e94c-122">LogMessagesAtServiceLevel</span></span>  

 <span data-ttu-id="0e94c-123">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="0e94c-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="0e94c-124">Тип доступа: чтение/запись</span><span class="sxs-lookup"><span data-stu-id="0e94c-124">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="0e94c-125">Значение, указывающее, трассируются ли сообщения на уровне службы (перед шифрованием и преобразованиями, связанными с транспортом).</span><span class="sxs-lookup"><span data-stu-id="0e94c-125">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="0e94c-126">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="0e94c-126">LogMessagesAtTransportLevel</span></span>  

 <span data-ttu-id="0e94c-127">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="0e94c-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="0e94c-128">Тип доступа: чтение/запись</span><span class="sxs-lookup"><span data-stu-id="0e94c-128">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="0e94c-129">Значение, указывающее, трассируются ли сообщения на уровне транспорта.</span><span class="sxs-lookup"><span data-stu-id="0e94c-129">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="0e94c-130">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="0e94c-130">MessageLoggingTraceListeners</span></span>  

 <span data-ttu-id="0e94c-131">Тип данных: массив TraceListener</span><span class="sxs-lookup"><span data-stu-id="0e94c-131">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="0e94c-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="0e94c-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0e94c-133">Коллекция прослушивателей трассировки, которые ожидают передачи данных источнику трассировки System.Wmi.MessageLogging.</span><span class="sxs-lookup"><span data-stu-id="0e94c-133">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="0e94c-134">Имя</span><span class="sxs-lookup"><span data-stu-id="0e94c-134">Name</span></span>  

 <span data-ttu-id="0e94c-135">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="0e94c-135">Data type: string</span></span>  
  
 <span data-ttu-id="0e94c-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="0e94c-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0e94c-137">Имя домена приложения.</span><span class="sxs-lookup"><span data-stu-id="0e94c-137">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="0e94c-138">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="0e94c-138">PerformanceCounters</span></span>  

 <span data-ttu-id="0e94c-139">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="0e94c-139">Data type: string</span></span>  
  
 <span data-ttu-id="0e94c-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="0e94c-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0e94c-141">Область активных счетчиков производительности в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="0e94c-141">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="0e94c-142">ProcessId</span><span class="sxs-lookup"><span data-stu-id="0e94c-142">ProcessId</span></span>  

 <span data-ttu-id="0e94c-143">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="0e94c-143">Data type: sint32</span></span>  
  
 <span data-ttu-id="0e94c-144">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="0e94c-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0e94c-145">Идентификатор процесса.</span><span class="sxs-lookup"><span data-stu-id="0e94c-145">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="0e94c-146">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="0e94c-146">ServiceConfigPath</span></span>  

 <span data-ttu-id="0e94c-147">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="0e94c-147">Data type: string</span></span>  
  
 <span data-ttu-id="0e94c-148">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="0e94c-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0e94c-149">Путь к конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="0e94c-149">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="0e94c-150">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="0e94c-150">TraceLevel</span></span>  

 <span data-ttu-id="0e94c-151">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="0e94c-151">Data type: string</span></span>  
  
 <span data-ttu-id="0e94c-152">Тип доступа: чтение/запись</span><span class="sxs-lookup"><span data-stu-id="0e94c-152">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="0e94c-153">Уровень трассировки источника трассировки System.Wmi.</span><span class="sxs-lookup"><span data-stu-id="0e94c-153">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="0e94c-154">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="0e94c-154">ServiceModelTraceListeners</span></span>  

 <span data-ttu-id="0e94c-155">Тип данных: массив TraceListener</span><span class="sxs-lookup"><span data-stu-id="0e94c-155">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="0e94c-156">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="0e94c-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0e94c-157">Коллекция прослушивателей, ожидающих передачи данных от источника трассировки System.ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="0e94c-157">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e94c-158">Требования</span><span class="sxs-lookup"><span data-stu-id="0e94c-158">Requirements</span></span>  
  
|<span data-ttu-id="0e94c-159">MOF</span><span class="sxs-lookup"><span data-stu-id="0e94c-159">MOF</span></span>|<span data-ttu-id="0e94c-160">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0e94c-160">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0e94c-161">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="0e94c-161">Namespace</span></span>|<span data-ttu-id="0e94c-162">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="0e94c-162">Defined in root\ServiceModel</span></span>|
