---
description: 'Дополнительные сведения о: Ткпконнектионпулсеттингс'
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 927fcba7f94bcbfa80e06479e79bf20986a661e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715201"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="284a2-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="284a2-103">TcpConnectionPoolSettings</span></span>

<span data-ttu-id="284a2-104">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="284a2-104">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="284a2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="284a2-105">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="284a2-106">Методы</span><span class="sxs-lookup"><span data-stu-id="284a2-106">Methods</span></span>  

 <span data-ttu-id="284a2-107">Класс TcpConnectionPoolSettings не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="284a2-107">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="284a2-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="284a2-108">Properties</span></span>  

 <span data-ttu-id="284a2-109">Класс TcpConnectionPoolSettings имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="284a2-109">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="284a2-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="284a2-110">GroupName</span></span>  

 <span data-ttu-id="284a2-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="284a2-111">Data type: string</span></span>  
  
 <span data-ttu-id="284a2-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="284a2-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="284a2-113">Имя группы пула подключений, используемого элементом привязки.</span><span class="sxs-lookup"><span data-stu-id="284a2-113">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="284a2-114">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="284a2-114">IdleTimeout</span></span>  

 <span data-ttu-id="284a2-115">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="284a2-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="284a2-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="284a2-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="284a2-117">Максимальное время, в течение которого подключение может простаивать перед отключением.</span><span class="sxs-lookup"><span data-stu-id="284a2-117">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="284a2-118">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="284a2-118">LeaseTimeout</span></span>  

 <span data-ttu-id="284a2-119">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="284a2-119">Data type: datetime</span></span>  
  
 <span data-ttu-id="284a2-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="284a2-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="284a2-121">Максимальное время ожидания завершения выполнения операции аренды.</span><span class="sxs-lookup"><span data-stu-id="284a2-121">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="284a2-122">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="284a2-122">MaxOutboundConnectionsPerEndpoint</span></span>  

 <span data-ttu-id="284a2-123">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="284a2-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="284a2-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="284a2-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="284a2-125">Максимальное число исходящих подключений для каждой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="284a2-125">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="284a2-126">Требования</span><span class="sxs-lookup"><span data-stu-id="284a2-126">Requirements</span></span>  
  
|<span data-ttu-id="284a2-127">MOF</span><span class="sxs-lookup"><span data-stu-id="284a2-127">MOF</span></span>|<span data-ttu-id="284a2-128">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="284a2-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="284a2-129">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="284a2-129">Namespace</span></span>|<span data-ttu-id="284a2-130">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="284a2-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="284a2-131">См. также</span><span class="sxs-lookup"><span data-stu-id="284a2-131">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
