---
description: 'Дополнительные сведения о: Ткптранспортбиндинжелемент'
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: b52bb2eb4b40648808459f76e068a6f72f9476a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715149"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="8dd9c-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="8dd9c-103">TcpTransportBindingElement</span></span>

<span data-ttu-id="8dd9c-104">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="8dd9c-104">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dd9c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8dd9c-105">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8dd9c-106">Методы</span><span class="sxs-lookup"><span data-stu-id="8dd9c-106">Methods</span></span>  

 <span data-ttu-id="8dd9c-107">Класс TcpTransportBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="8dd9c-107">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8dd9c-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="8dd9c-108">Properties</span></span>  

 <span data-ttu-id="8dd9c-109">Класс TcpTransportBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="8dd9c-109">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="8dd9c-110">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="8dd9c-110">ConnectionPoolSettings</span></span>  

 <span data-ttu-id="8dd9c-111">Тип данных: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="8dd9c-111">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="8dd9c-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="8dd9c-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8dd9c-113">Настройки пула подключений.</span><span class="sxs-lookup"><span data-stu-id="8dd9c-113">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="8dd9c-114">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="8dd9c-114">ListenBacklog</span></span>  

 <span data-ttu-id="8dd9c-115">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="8dd9c-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="8dd9c-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="8dd9c-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8dd9c-117">Максимально допустимое количество ожидающих запросов на подключение в очереди.</span><span class="sxs-lookup"><span data-stu-id="8dd9c-117">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="8dd9c-118">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="8dd9c-118">PortSharingEnabled</span></span>  

 <span data-ttu-id="8dd9c-119">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="8dd9c-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="8dd9c-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="8dd9c-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8dd9c-121">Логическое значение, определяющее, включено ли совместное использование порта TCP для этого подключения.</span><span class="sxs-lookup"><span data-stu-id="8dd9c-121">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="8dd9c-122">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="8dd9c-122">TeredoEnabled</span></span>  

 <span data-ttu-id="8dd9c-123">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="8dd9c-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="8dd9c-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="8dd9c-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8dd9c-125">Логическое значение, указывающее, используется ли Teredo (технология адресации клиентов, защищенных брандмауэром).</span><span class="sxs-lookup"><span data-stu-id="8dd9c-125">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dd9c-126">Требования</span><span class="sxs-lookup"><span data-stu-id="8dd9c-126">Requirements</span></span>  
  
|<span data-ttu-id="8dd9c-127">MOF</span><span class="sxs-lookup"><span data-stu-id="8dd9c-127">MOF</span></span>|<span data-ttu-id="8dd9c-128">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8dd9c-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8dd9c-129">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="8dd9c-129">Namespace</span></span>|<span data-ttu-id="8dd9c-130">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="8dd9c-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8dd9c-131">См. также</span><span class="sxs-lookup"><span data-stu-id="8dd9c-131">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
