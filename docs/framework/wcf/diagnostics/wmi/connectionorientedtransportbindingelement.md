---
description: 'Дополнительные сведения о: Коннектионориентедтранспортбиндинжелемент'
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: bd0c05fc86ad7bc95837cee7e22ea83975369b62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757583"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="fb363-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="fb363-103">ConnectionOrientedTransportBindingElement</span></span>

<span data-ttu-id="fb363-104">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="fb363-104">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb363-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fb363-105">Syntax</span></span>  
  
```csharp
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fb363-106">Методы</span><span class="sxs-lookup"><span data-stu-id="fb363-106">Methods</span></span>  

 <span data-ttu-id="fb363-107">Класс ConnectionOrientedTransportBindingElement не определяет никакие методы.</span><span class="sxs-lookup"><span data-stu-id="fb363-107">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fb363-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="fb363-108">Properties</span></span>  

 <span data-ttu-id="fb363-109">Класс ConnectionOrientedTransportBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="fb363-109">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="fb363-110">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="fb363-110">ChannelInitializationTimeout</span></span>  

 <span data-ttu-id="fb363-111">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="fb363-111">Data type: datetime</span></span>  
  
 <span data-ttu-id="fb363-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb363-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb363-113">Задает интервал времени, который выделяется для инициализации канала до возникновения тайм-аута.</span><span class="sxs-lookup"><span data-stu-id="fb363-113">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="fb363-114">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="fb363-114">ConnectionBufferSize</span></span>  

 <span data-ttu-id="fb363-115">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="fb363-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="fb363-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb363-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb363-117">Размер буфера, используемого для передачи по сети фрагмента сериализованного сообщения от клиента серверу.</span><span class="sxs-lookup"><span data-stu-id="fb363-117">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="fb363-118">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="fb363-118">HostNameComparisonMode</span></span>  

 <span data-ttu-id="fb363-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="fb363-119">Data type: string</span></span>  
  
 <span data-ttu-id="fb363-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb363-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb363-121">Значение, указывающее, используется ли имя узла для доступа к службе при сопоставлении по универсальному коду ресурса (URI).</span><span class="sxs-lookup"><span data-stu-id="fb363-121">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="fb363-122">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="fb363-122">MaxBufferSize</span></span>  

 <span data-ttu-id="fb363-123">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="fb363-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="fb363-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb363-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb363-125">Максимально используемый размер буфера.</span><span class="sxs-lookup"><span data-stu-id="fb363-125">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="fb363-126">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="fb363-126">MaxOutputDelay</span></span>  

 <span data-ttu-id="fb363-127">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="fb363-127">Data type: datetime</span></span>  
  
 <span data-ttu-id="fb363-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb363-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb363-129">Максимальный промежуток времени, в течение которого фрагмент сообщения или все сообщение может оставаться в буфере перед отправкой.</span><span class="sxs-lookup"><span data-stu-id="fb363-129">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="fb363-130">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="fb363-130">MaxPendingAccepts</span></span>  

 <span data-ttu-id="fb363-131">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="fb363-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="fb363-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb363-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb363-133">Максимальное число ожидающих асинхронных потоков приема, доступных для обработки входящих подключений к службе.</span><span class="sxs-lookup"><span data-stu-id="fb363-133">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="fb363-134">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="fb363-134">MaxPendingConnections</span></span>  

 <span data-ttu-id="fb363-135">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="fb363-135">Data type: sint32</span></span>  
  
 <span data-ttu-id="fb363-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb363-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb363-137">Максимальное количество ожидающих подключений.</span><span class="sxs-lookup"><span data-stu-id="fb363-137">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="fb363-138">TransferMode</span><span class="sxs-lookup"><span data-stu-id="fb363-138">TransferMode</span></span>  

 <span data-ttu-id="fb363-139">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="fb363-139">Data type: string</span></span>  
  
 <span data-ttu-id="fb363-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb363-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb363-141">Значение, указывающее, следует ли буферизировать сообщения, или передавать их потоком с использованием транспорта, ориентированного на подключения.</span><span class="sxs-lookup"><span data-stu-id="fb363-141">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb363-142">Требования</span><span class="sxs-lookup"><span data-stu-id="fb363-142">Requirements</span></span>  
  
|<span data-ttu-id="fb363-143">MOF</span><span class="sxs-lookup"><span data-stu-id="fb363-143">MOF</span></span>|<span data-ttu-id="fb363-144">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fb363-144">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fb363-145">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="fb363-145">Namespace</span></span>|<span data-ttu-id="fb363-146">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="fb363-146">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb363-147">См. также</span><span class="sxs-lookup"><span data-stu-id="fb363-147">See also</span></span>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
