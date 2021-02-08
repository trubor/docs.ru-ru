---
description: 'Дополнительные сведения о: Мсмктранспортбиндинжелемент'
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 4b6f363d979972c6ff0a2a378906feeece2ff6b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803156"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="bd91d-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="bd91d-103">MsmqTransportBindingElement</span></span>

<span data-ttu-id="bd91d-104">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="bd91d-104">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd91d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bd91d-105">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bd91d-106">Методы</span><span class="sxs-lookup"><span data-stu-id="bd91d-106">Methods</span></span>  

 <span data-ttu-id="bd91d-107">Класс MsmqTransportBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="bd91d-107">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bd91d-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="bd91d-108">Properties</span></span>  

 <span data-ttu-id="bd91d-109">Класс MsmqTransportBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="bd91d-109">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="bd91d-110">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="bd91d-110">MaxPoolSize</span></span>  

 <span data-ttu-id="bd91d-111">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="bd91d-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="bd91d-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="bd91d-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd91d-113">Максимальный размер пула, содержащего внутренние объекты сообщений MSMQ.</span><span class="sxs-lookup"><span data-stu-id="bd91d-113">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="bd91d-114">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="bd91d-114">QueueTransferProtocol</span></span>  

 <span data-ttu-id="bd91d-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="bd91d-115">Data type: string</span></span>  
  
 <span data-ttu-id="bd91d-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="bd91d-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd91d-117">Значение перечисления, в котором указывается поставленный в очередь транспорт канала связи, используемый данной привязкой.</span><span class="sxs-lookup"><span data-stu-id="bd91d-117">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="bd91d-118">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="bd91d-118">UseActiveDirectory</span></span>  

 <span data-ttu-id="bd91d-119">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="bd91d-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="bd91d-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="bd91d-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd91d-121">Возвращает логическое значение, указывающее, следует ли преобразовывать адреса очередей с помощью Active Directory.</span><span class="sxs-lookup"><span data-stu-id="bd91d-121">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd91d-122">Требования</span><span class="sxs-lookup"><span data-stu-id="bd91d-122">Requirements</span></span>  
  
|<span data-ttu-id="bd91d-123">MOF</span><span class="sxs-lookup"><span data-stu-id="bd91d-123">MOF</span></span>|<span data-ttu-id="bd91d-124">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="bd91d-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bd91d-125">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="bd91d-125">Namespace</span></span>|<span data-ttu-id="bd91d-126">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="bd91d-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd91d-127">См. также</span><span class="sxs-lookup"><span data-stu-id="bd91d-127">See also</span></span>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
