---
description: 'Дополнительные сведения о: Пирсекуритисеттингс'
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: a8b5b8c88e71cb46110fa35186599c0f9c366d17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803013"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="028f1-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="028f1-103">PeerSecuritySettings</span></span>

<span data-ttu-id="028f1-104">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="028f1-104">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="028f1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="028f1-105">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="028f1-106">Методы</span><span class="sxs-lookup"><span data-stu-id="028f1-106">Methods</span></span>  

 <span data-ttu-id="028f1-107">Класс PeerSecuritySettings не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="028f1-107">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="028f1-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="028f1-108">Properties</span></span>  

 <span data-ttu-id="028f1-109">Класс PeerSecuritySettings имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="028f1-109">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="028f1-110">Режим</span><span class="sxs-lookup"><span data-stu-id="028f1-110">Mode</span></span>  

 <span data-ttu-id="028f1-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="028f1-111">Data type: string</span></span>  
  
 <span data-ttu-id="028f1-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="028f1-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="028f1-113">Определяет, использует ли настроенная с помощью привязки конечная точка безопасность на уровне сообщений и на транспортном уровне.</span><span class="sxs-lookup"><span data-stu-id="028f1-113">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="028f1-114">Транспорт</span><span class="sxs-lookup"><span data-stu-id="028f1-114">Transport</span></span>  

 <span data-ttu-id="028f1-115">Тип данных: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="028f1-115">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="028f1-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="028f1-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="028f1-117">Параметры безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="028f1-117">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="028f1-118">Требования</span><span class="sxs-lookup"><span data-stu-id="028f1-118">Requirements</span></span>  
  
|<span data-ttu-id="028f1-119">MOF</span><span class="sxs-lookup"><span data-stu-id="028f1-119">MOF</span></span>|<span data-ttu-id="028f1-120">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="028f1-120">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="028f1-121">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="028f1-121">Namespace</span></span>|<span data-ttu-id="028f1-122">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="028f1-122">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="028f1-123">См. также</span><span class="sxs-lookup"><span data-stu-id="028f1-123">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
