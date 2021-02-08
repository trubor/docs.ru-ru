---
description: 'Дополнительные сведения о: Намедпипеконнектионпулсеттингс'
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8d724c7a24f62a8d48797125528eb8a194ece660
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803117"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="eef44-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="eef44-103">NamedPipeConnectionPoolSettings</span></span>

<span data-ttu-id="eef44-104">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="eef44-104">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eef44-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eef44-105">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="eef44-106">Методы</span><span class="sxs-lookup"><span data-stu-id="eef44-106">Methods</span></span>  

 <span data-ttu-id="eef44-107">Класс NamedPipeConnectionPoolSettings не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="eef44-107">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="eef44-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="eef44-108">Properties</span></span>  

 <span data-ttu-id="eef44-109">Класс NamedPipeConnectionPoolSettings имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="eef44-109">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="eef44-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="eef44-110">GroupName</span></span>  

 <span data-ttu-id="eef44-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="eef44-111">Data type: string</span></span>  
  
 <span data-ttu-id="eef44-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="eef44-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eef44-113">Имя группы пула подключений, используемого элементом привязки.</span><span class="sxs-lookup"><span data-stu-id="eef44-113">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="eef44-114">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="eef44-114">IdleTimeout</span></span>  

 <span data-ttu-id="eef44-115">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="eef44-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="eef44-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="eef44-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eef44-117">Максимальное время, в течение которого подключение может простаивать перед отключением.</span><span class="sxs-lookup"><span data-stu-id="eef44-117">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="eef44-118">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="eef44-118">MaxOutboundConnectionsPerEndpoint</span></span>  

 <span data-ttu-id="eef44-119">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="eef44-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="eef44-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="eef44-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eef44-121">Максимальное число исходящих соединений для каждой конечной точки на клиенте.</span><span class="sxs-lookup"><span data-stu-id="eef44-121">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eef44-122">Требования</span><span class="sxs-lookup"><span data-stu-id="eef44-122">Requirements</span></span>  
  
|<span data-ttu-id="eef44-123">MOF</span><span class="sxs-lookup"><span data-stu-id="eef44-123">MOF</span></span>|<span data-ttu-id="eef44-124">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="eef44-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="eef44-125">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="eef44-125">Namespace</span></span>|<span data-ttu-id="eef44-126">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="eef44-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eef44-127">См. также</span><span class="sxs-lookup"><span data-stu-id="eef44-127">See also</span></span>

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
