---
description: 'Дополнительные сведения о: Мсмкбиндинжелементбасе'
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 3aa5ec2343d73798f1cf5e3c7d4b5a8282f97ac9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803182"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="f451b-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="f451b-103">MsmqBindingElementBase</span></span>

<span data-ttu-id="f451b-104">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="f451b-104">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f451b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f451b-105">Syntax</span></span>  
  
```csharp  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f451b-106">Методы</span><span class="sxs-lookup"><span data-stu-id="f451b-106">Methods</span></span>  

 <span data-ttu-id="f451b-107">Класс MsmqBindingElementBase не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="f451b-107">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f451b-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="f451b-108">Properties</span></span>  

 <span data-ttu-id="f451b-109">Класс MsmqBindingElementBase имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="f451b-109">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="f451b-110">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="f451b-110">CustomDeadLetterQueue</span></span>  

 <span data-ttu-id="f451b-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="f451b-111">Data type: string</span></span>  
  
 <span data-ttu-id="f451b-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f451b-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f451b-113">Универсальный код ресурса (URI), содержащий местоположение очереди недоставленных сообщений для каждого приложения; в эту очередь помещаются просроченные сообщения или сообщения, которые не удалось передать или доставить.</span><span class="sxs-lookup"><span data-stu-id="f451b-113">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="f451b-114">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="f451b-114">DeadLetterQueue</span></span>  

 <span data-ttu-id="f451b-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="f451b-115">Data type: string</span></span>  
  
 <span data-ttu-id="f451b-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f451b-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f451b-117">Значение перечисления, указывающее тип используемой очереди недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="f451b-117">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="f451b-118">durable</span><span class="sxs-lookup"><span data-stu-id="f451b-118">Durable</span></span>  

 <span data-ttu-id="f451b-119">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="f451b-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="f451b-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f451b-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f451b-121">Значение, указывающее, являются ли сообщения, обрабатываемые этой привязкой, устойчивыми или неустойчивыми.</span><span class="sxs-lookup"><span data-stu-id="f451b-121">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="f451b-122">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="f451b-122">ExactlyOnce</span></span>  

 <span data-ttu-id="f451b-123">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="f451b-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="f451b-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f451b-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f451b-125">Логическое значение, указывающее, доставляются ли сообщения, обрабатываемые этой привязкой, только один раз.</span><span class="sxs-lookup"><span data-stu-id="f451b-125">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="f451b-126">MaxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="f451b-126">MaxRetryCycles</span></span>  

 <span data-ttu-id="f451b-127">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="f451b-127">Data type: sint32</span></span>  
  
 <span data-ttu-id="f451b-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f451b-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f451b-129">Максимальное количество циклов повторных попыток доставить сообщение принимающему приложению.</span><span class="sxs-lookup"><span data-stu-id="f451b-129">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="f451b-130">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="f451b-130">ReceiveErrorHandling</span></span>  

 <span data-ttu-id="f451b-131">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="f451b-131">Data type: string</span></span>  
  
 <span data-ttu-id="f451b-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f451b-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f451b-133">Параметры обработки подозрительных сообщений.</span><span class="sxs-lookup"><span data-stu-id="f451b-133">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="f451b-134">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="f451b-134">ReceiveRetryCount</span></span>  

 <span data-ttu-id="f451b-135">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="f451b-135">Data type: sint32</span></span>  
  
 <span data-ttu-id="f451b-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f451b-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f451b-137">Максимальное количество немедленных повторных попыток считывания сообщения из очереди приложения.</span><span class="sxs-lookup"><span data-stu-id="f451b-137">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="f451b-138">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="f451b-138">RetryCycleDelay</span></span>  

 <span data-ttu-id="f451b-139">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="f451b-139">Data type: datetime</span></span>  
  
 <span data-ttu-id="f451b-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f451b-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f451b-141">Значение, указывающее временную задержку между циклами повторных попыток доставить сообщение, которое не удалось доставить немедленно.</span><span class="sxs-lookup"><span data-stu-id="f451b-141">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="f451b-142">timeToLive</span><span class="sxs-lookup"><span data-stu-id="f451b-142">TimeToLive</span></span>  

 <span data-ttu-id="f451b-143">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="f451b-143">Data type: datetime</span></span>  
  
 <span data-ttu-id="f451b-144">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f451b-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f451b-145">Промежуток времени, соответствующий максимальному сроку нахождения в очереди сообщений, обрабатываемых этой привязкой.</span><span class="sxs-lookup"><span data-stu-id="f451b-145">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="f451b-146">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="f451b-146">UseMsmqTracing</span></span>  

 <span data-ttu-id="f451b-147">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="f451b-147">Data type: boolean</span></span>  
  
 <span data-ttu-id="f451b-148">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f451b-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f451b-149">Логическое значение, указывающее, следует ли трассировать сообщения, обрабатываемые этой привязкой.</span><span class="sxs-lookup"><span data-stu-id="f451b-149">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="f451b-150">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="f451b-150">UseSourceJournal</span></span>  

 <span data-ttu-id="f451b-151">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="f451b-151">Data type: boolean</span></span>  
  
 <span data-ttu-id="f451b-152">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f451b-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f451b-153">Логическое значение, указывающее, должны ли сохраняться в очереди журнала источника копии сообщений, обрабатываемых этой привязкой.</span><span class="sxs-lookup"><span data-stu-id="f451b-153">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f451b-154">Требования</span><span class="sxs-lookup"><span data-stu-id="f451b-154">Requirements</span></span>  
  
|<span data-ttu-id="f451b-155">MOF</span><span class="sxs-lookup"><span data-stu-id="f451b-155">MOF</span></span>|<span data-ttu-id="f451b-156">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f451b-156">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f451b-157">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="f451b-157">Namespace</span></span>|<span data-ttu-id="f451b-158">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="f451b-158">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f451b-159">См. также</span><span class="sxs-lookup"><span data-stu-id="f451b-159">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
