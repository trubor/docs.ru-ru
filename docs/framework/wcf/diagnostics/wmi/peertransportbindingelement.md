---
description: 'Дополнительные сведения о: Пиртранспортбиндинжелемент'
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: b1ca8020f51a5f9b121f7d238d82b9971d13cdd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757336"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="ceb22-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="ceb22-103">PeerTransportBindingElement</span></span>

<span data-ttu-id="ceb22-104">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="ceb22-104">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb22-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ceb22-105">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ceb22-106">Методы</span><span class="sxs-lookup"><span data-stu-id="ceb22-106">Methods</span></span>  

 <span data-ttu-id="ceb22-107">Класс PeerTransportBindingElement не определяет никакие методы.</span><span class="sxs-lookup"><span data-stu-id="ceb22-107">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ceb22-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="ceb22-108">Properties</span></span>  

 <span data-ttu-id="ceb22-109">Класс PeerTransportBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="ceb22-109">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="ceb22-110">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="ceb22-110">ListenIPAddress</span></span>  

 <span data-ttu-id="ceb22-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="ceb22-111">Data type: string</span></span>  
  
 <span data-ttu-id="ceb22-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="ceb22-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ceb22-113">IP-адрес, на котором одноранговый узел будет ожидать сообщения.</span><span class="sxs-lookup"><span data-stu-id="ceb22-113">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="ceb22-114">Port</span><span class="sxs-lookup"><span data-stu-id="ceb22-114">Port</span></span>  

 <span data-ttu-id="ceb22-115">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="ceb22-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="ceb22-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="ceb22-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ceb22-117">Порт сетевого интерфейса, на котором эта привязка будет обрабатывать сообщения однорангового канала.</span><span class="sxs-lookup"><span data-stu-id="ceb22-117">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="ceb22-118">Безопасность</span><span class="sxs-lookup"><span data-stu-id="ceb22-118">Security</span></span>  

 <span data-ttu-id="ceb22-119">Тип данных: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ceb22-119">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="ceb22-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="ceb22-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ceb22-121">Параметры безопасности однорангового транспорта.</span><span class="sxs-lookup"><span data-stu-id="ceb22-121">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceb22-122">Требования</span><span class="sxs-lookup"><span data-stu-id="ceb22-122">Requirements</span></span>  
  
|<span data-ttu-id="ceb22-123">MOF</span><span class="sxs-lookup"><span data-stu-id="ceb22-123">MOF</span></span>|<span data-ttu-id="ceb22-124">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ceb22-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ceb22-125">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="ceb22-125">Namespace</span></span>|<span data-ttu-id="ceb22-126">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="ceb22-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ceb22-127">См. также</span><span class="sxs-lookup"><span data-stu-id="ceb22-127">See also</span></span>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
