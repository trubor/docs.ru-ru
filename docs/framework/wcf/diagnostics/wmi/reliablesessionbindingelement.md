---
description: 'Дополнительные сведения о: элемент ReliableSessionBindingElement'
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 582fd62a8751a31c2834b7d81219a237c9887236
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743867"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="f9fde-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="f9fde-103">ReliableSessionBindingElement</span></span>

<span data-ttu-id="f9fde-104">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="f9fde-104">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9fde-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f9fde-105">Syntax</span></span>  
  
```csharp
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f9fde-106">Методы</span><span class="sxs-lookup"><span data-stu-id="f9fde-106">Methods</span></span>  

 <span data-ttu-id="f9fde-107">Класс ReliableSessionBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="f9fde-107">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f9fde-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="f9fde-108">Properties</span></span>  

 <span data-ttu-id="f9fde-109">Класс ReliableSessionBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="f9fde-109">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="f9fde-110">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="f9fde-110">AcknowledgementInterval</span></span>  

 <span data-ttu-id="f9fde-111">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="f9fde-111">Data type: datetime</span></span>  
  
 <span data-ttu-id="f9fde-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f9fde-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f9fde-113">Промежуток времени, в течение которого пункт назначения ожидает перед отправкой подтверждения источнику сообщения по надежным каналам, созданным фабрикой.</span><span class="sxs-lookup"><span data-stu-id="f9fde-113">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="f9fde-114">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="f9fde-114">FlowControlEnabled</span></span>  

 <span data-ttu-id="f9fde-115">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="f9fde-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="f9fde-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f9fde-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f9fde-117">Логическое значение, указывающее, включено ли управление потоком.</span><span class="sxs-lookup"><span data-stu-id="f9fde-117">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="f9fde-118">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="f9fde-118">InactivityTimeout</span></span>  

 <span data-ttu-id="f9fde-119">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="f9fde-119">Data type: datetime</span></span>  
  
 <span data-ttu-id="f9fde-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f9fde-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f9fde-121">Максимальное время, в течение которого канал позволяет другому участнику соединения не отправлять никаких сообщений, прежде чем канал будет закрыт с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="f9fde-121">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="f9fde-122">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="f9fde-122">MaxPendingChannels</span></span>  

 <span data-ttu-id="f9fde-123">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="f9fde-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="f9fde-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f9fde-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f9fde-125">Максимальное число каналов, ожидающих принятия на прослушивателе.</span><span class="sxs-lookup"><span data-stu-id="f9fde-125">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="f9fde-126">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="f9fde-126">MaxRetryCount</span></span>  

 <span data-ttu-id="f9fde-127">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="f9fde-127">Data type: sint32</span></span>  
  
 <span data-ttu-id="f9fde-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f9fde-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f9fde-129">Максимальное количество попыток повторной передачи надежным каналом сообщения, для которого не было получено подтверждение приема. Повторная передача осуществляется посредством вызова метода `Send` в базовом канале.</span><span class="sxs-lookup"><span data-stu-id="f9fde-129">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="f9fde-130">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="f9fde-130">MaxTransferWindowSize</span></span>  

 <span data-ttu-id="f9fde-131">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="f9fde-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="f9fde-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f9fde-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f9fde-133">Максимальный размер окна передачи для надежного сеанса.</span><span class="sxs-lookup"><span data-stu-id="f9fde-133">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="f9fde-134">Заказано</span><span class="sxs-lookup"><span data-stu-id="f9fde-134">Ordered</span></span>  

 <span data-ttu-id="f9fde-135">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="f9fde-135">Data type: boolean</span></span>  
  
 <span data-ttu-id="f9fde-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f9fde-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f9fde-137">Логическое значение, определяющее, прибывают ли сообщения точно в том порядке, в котором они были отправлены.</span><span class="sxs-lookup"><span data-stu-id="f9fde-137">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="f9fde-138">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="f9fde-138">ReliableMessagingVersion</span></span>  

 <span data-ttu-id="f9fde-139">Тип данных: integer</span><span class="sxs-lookup"><span data-stu-id="f9fde-139">Data type: integer</span></span>  
  
 <span data-ttu-id="f9fde-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="f9fde-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f9fde-141">Целочисленное значение, задающее версию используемого в надежном канале протокола WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="f9fde-141">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9fde-142">Требования</span><span class="sxs-lookup"><span data-stu-id="f9fde-142">Requirements</span></span>  
  
|<span data-ttu-id="f9fde-143">MOF</span><span class="sxs-lookup"><span data-stu-id="f9fde-143">MOF</span></span>|<span data-ttu-id="f9fde-144">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f9fde-144">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f9fde-145">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="f9fde-145">Namespace</span></span>|<span data-ttu-id="f9fde-146">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="f9fde-146">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9fde-147">См. также</span><span class="sxs-lookup"><span data-stu-id="f9fde-147">See also</span></span>

- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
