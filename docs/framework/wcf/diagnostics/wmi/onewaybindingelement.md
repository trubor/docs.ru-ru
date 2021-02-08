---
description: 'Дополнительные сведения о: Оневайбиндинжелемент'
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 9c2ccc301bd854c7b85fcc53551ed6def329a8fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803091"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="86844-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="86844-103">OneWayBindingElement</span></span>

<span data-ttu-id="86844-104">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="86844-104">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86844-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="86844-105">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="86844-106">Методы</span><span class="sxs-lookup"><span data-stu-id="86844-106">Methods</span></span>  

 <span data-ttu-id="86844-107">Класс OneWayBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="86844-107">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="86844-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="86844-108">Properties</span></span>  

 <span data-ttu-id="86844-109">Класс OneWayBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="86844-109">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="86844-110">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="86844-110">ChannelPoolSettings</span></span>  

 <span data-ttu-id="86844-111">Тип данных: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="86844-111">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="86844-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="86844-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="86844-113">Параметры пула каналов.</span><span class="sxs-lookup"><span data-stu-id="86844-113">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="86844-114">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="86844-114">MaxAcceptedChannels</span></span>  

 <span data-ttu-id="86844-115">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="86844-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="86844-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="86844-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="86844-117">Максимальное число принимаемых каналов.</span><span class="sxs-lookup"><span data-stu-id="86844-117">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="86844-118">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="86844-118">PacketRoutable</span></span>  

 <span data-ttu-id="86844-119">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="86844-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="86844-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="86844-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="86844-121">Значение, указывающее, возможна ли маршрутизация пакета.</span><span class="sxs-lookup"><span data-stu-id="86844-121">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86844-122">Требования</span><span class="sxs-lookup"><span data-stu-id="86844-122">Requirements</span></span>  
  
|<span data-ttu-id="86844-123">MOF</span><span class="sxs-lookup"><span data-stu-id="86844-123">MOF</span></span>|<span data-ttu-id="86844-124">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="86844-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="86844-125">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="86844-125">Namespace</span></span>|<span data-ttu-id="86844-126">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="86844-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86844-127">См. также</span><span class="sxs-lookup"><span data-stu-id="86844-127">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
