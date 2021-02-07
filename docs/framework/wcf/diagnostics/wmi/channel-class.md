---
description: Дополнительные сведения о классе Channel
title: Класс Channel
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: dcc92f78f09e9a73a24134c6c0685949f46f38dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757726"
---
# <a name="channel-class"></a><span data-ttu-id="9b578-103">Класс Channel</span><span class="sxs-lookup"><span data-stu-id="9b578-103">Channel class</span></span>

<span data-ttu-id="9b578-104">Канал</span><span class="sxs-lookup"><span data-stu-id="9b578-104">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b578-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9b578-105">Syntax</span></span>  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9b578-106">Методы</span><span class="sxs-lookup"><span data-stu-id="9b578-106">Methods</span></span>  

 <span data-ttu-id="9b578-107">Класс Channel не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="9b578-107">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9b578-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="9b578-108">Properties</span></span>  

 <span data-ttu-id="9b578-109">Класс Channel имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="9b578-109">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="9b578-110">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="9b578-110">LocalAddress</span></span>  

 <span data-ttu-id="9b578-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="9b578-111">Data type: string</span></span>  
  
 <span data-ttu-id="9b578-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9b578-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b578-113">Локальная конечная точка канала.</span><span class="sxs-lookup"><span data-stu-id="9b578-113">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="9b578-114">ref</span><span class="sxs-lookup"><span data-stu-id="9b578-114">ref</span></span>  

 <span data-ttu-id="9b578-115">Тип данных: Endpoint</span><span class="sxs-lookup"><span data-stu-id="9b578-115">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="9b578-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9b578-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b578-117">Ссылка на конечную точку, к которой подключается канал.</span><span class="sxs-lookup"><span data-stu-id="9b578-117">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="9b578-118">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="9b578-118">RemoteAddress</span></span>  

 <span data-ttu-id="9b578-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="9b578-119">Data type: string</span></span>  
  
 <span data-ttu-id="9b578-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9b578-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b578-121">Удаленный адрес, связанный с каналом.</span><span class="sxs-lookup"><span data-stu-id="9b578-121">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="9b578-122">SessionId</span><span class="sxs-lookup"><span data-stu-id="9b578-122">SessionId</span></span>  

 <span data-ttu-id="9b578-123">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="9b578-123">Data type: string</span></span>  
  
 <span data-ttu-id="9b578-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9b578-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b578-125">Идентификатор текущего сеанса, если он существует.</span><span class="sxs-lookup"><span data-stu-id="9b578-125">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="9b578-126">Тип</span><span class="sxs-lookup"><span data-stu-id="9b578-126">Type</span></span>  

 <span data-ttu-id="9b578-127">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="9b578-127">Data type: string</span></span>  
  
 <span data-ttu-id="9b578-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9b578-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b578-129">Тип канала.</span><span class="sxs-lookup"><span data-stu-id="9b578-129">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b578-130">Требования</span><span class="sxs-lookup"><span data-stu-id="9b578-130">Requirements</span></span>  
  
|<span data-ttu-id="9b578-131">MOF</span><span class="sxs-lookup"><span data-stu-id="9b578-131">MOF</span></span>|<span data-ttu-id="9b578-132">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9b578-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9b578-133">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="9b578-133">Namespace</span></span>|<span data-ttu-id="9b578-134">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="9b578-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b578-135">См. также</span><span class="sxs-lookup"><span data-stu-id="9b578-135">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelBase>
