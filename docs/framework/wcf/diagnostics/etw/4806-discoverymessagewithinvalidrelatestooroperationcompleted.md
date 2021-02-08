---
description: 'Дополнительные сведения: 4806-Дисковеримессажевисинвалидрелатестуроператионкомплетед'
title: 4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted
ms.date: 03/30/2017
ms.assetid: 19e9a660-25f3-4332-b716-a12a59f2cbbb
ms.openlocfilehash: 51c1dd9e4478f53098a8087cb4c2e2efdceeaa2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788388"
---
# <a name="4806---discoverymessagewithinvalidrelatestooroperationcompleted"></a><span data-ttu-id="0c39c-103">4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="0c39c-103">4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="0c39c-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="0c39c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c39c-105">ID</span><span class="sxs-lookup"><span data-stu-id="0c39c-105">ID</span></span>|<span data-ttu-id="0c39c-106">4806</span><span class="sxs-lookup"><span data-stu-id="0c39c-106">4806</span></span>|  
|<span data-ttu-id="0c39c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="0c39c-107">Keywords</span></span>|<span data-ttu-id="0c39c-108">Обнаружение</span><span class="sxs-lookup"><span data-stu-id="0c39c-108">Discovery</span></span>|  
|<span data-ttu-id="0c39c-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="0c39c-109">Level</span></span>|<span data-ttu-id="0c39c-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="0c39c-110">Warning</span></span>|  
|<span data-ttu-id="0c39c-111">Канал</span><span class="sxs-lookup"><span data-stu-id="0c39c-111">Channel</span></span>|<span data-ttu-id="0c39c-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0c39c-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0c39c-113">Описание</span><span class="sxs-lookup"><span data-stu-id="0c39c-113">Description</span></span>  

 <span data-ttu-id="0c39c-114">Это сообщение создается, если сообщение обнаружения было отброшено клиентом DiscoveryClient, поскольку выполнена соответствующая операция, либо значение relatesTo является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="0c39c-114">This event is emitted when the discovery message was dropped by the DiscoveryClient because either the corresponding operation was completed or the relatesTo value is invalid.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0c39c-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="0c39c-115">Message</span></span>  

 <span data-ttu-id="0c39c-116">Сообщение %1 с messageId="%2" и relatesTo="%3" удалено клиентом DiscoveryClient, поскольку выполнена соответствующая операция %4 или значение relatesTo является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="0c39c-116">A %1 message with messageId='%2' and relatesTo='%3' was dropped by the DiscoveryClient because either the corresponding %4 operation was completed or the relatesTo value is invalid.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0c39c-117">Подробнее</span><span class="sxs-lookup"><span data-stu-id="0c39c-117">Details</span></span>
