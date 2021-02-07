---
description: 'Дополнительные сведения о: Чаннелпулсеттингс'
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: b08c5483e7a0c918393795b4608b9eef16b18341
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757687"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="3f499-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3f499-103">ChannelPoolSettings</span></span>

<span data-ttu-id="3f499-104">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3f499-104">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f499-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3f499-105">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3f499-106">Методы</span><span class="sxs-lookup"><span data-stu-id="3f499-106">Methods</span></span>  

 <span data-ttu-id="3f499-107">Класс ChannelPoolSettings не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="3f499-107">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3f499-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="3f499-108">Properties</span></span>  

 <span data-ttu-id="3f499-109">Класс ChannelPoolSettings имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="3f499-109">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="3f499-110">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="3f499-110">IdleTimeout</span></span>  

 <span data-ttu-id="3f499-111">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="3f499-111">Data type: datetime</span></span>  
  
 <span data-ttu-id="3f499-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="3f499-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3f499-113">Максимальное время, в течение которого подключение может простаивать перед отключением.</span><span class="sxs-lookup"><span data-stu-id="3f499-113">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="3f499-114">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="3f499-114">LeaseTimeout</span></span>  

 <span data-ttu-id="3f499-115">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="3f499-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="3f499-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="3f499-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3f499-117">Максимальное время ожидания завершения операции аренды.</span><span class="sxs-lookup"><span data-stu-id="3f499-117">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="3f499-118">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="3f499-118">MaxOutboundChannelsPerEndpoint</span></span>  

 <span data-ttu-id="3f499-119">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="3f499-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="3f499-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="3f499-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3f499-121">Максимальное число исходящих каналов для каждой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="3f499-121">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f499-122">Требования</span><span class="sxs-lookup"><span data-stu-id="3f499-122">Requirements</span></span>  
  
|<span data-ttu-id="3f499-123">MOF</span><span class="sxs-lookup"><span data-stu-id="3f499-123">MOF</span></span>|<span data-ttu-id="3f499-124">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3f499-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3f499-125">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="3f499-125">Namespace</span></span>|<span data-ttu-id="3f499-126">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="3f499-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f499-127">См. также</span><span class="sxs-lookup"><span data-stu-id="3f499-127">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
