---
description: 'Дополнительные сведения о: AsymmetricSecurityBindingElement'
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 25d0ac205491e9ce27c59d3a0670d1e4a3150e21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757947"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="3c9bb-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3c9bb-103">AsymmetricSecurityBindingElement</span></span>

<span data-ttu-id="3c9bb-104">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3c9bb-104">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c9bb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3c9bb-105">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3c9bb-106">Методы</span><span class="sxs-lookup"><span data-stu-id="3c9bb-106">Methods</span></span>  

 <span data-ttu-id="3c9bb-107">Класс AsymmetricSecurityBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-107">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3c9bb-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="3c9bb-108">Properties</span></span>  

 <span data-ttu-id="3c9bb-109">Класс AsymmetricSecurityBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-109">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="3c9bb-110">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="3c9bb-110">MessageProtectionOrder</span></span>  

 <span data-ttu-id="3c9bb-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="3c9bb-111">Data type: string</span></span>  
  
 <span data-ttu-id="3c9bb-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="3c9bb-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3c9bb-113">Порядок шифрования и подписывания сообщений для данной привязки.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-113">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="3c9bb-114">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="3c9bb-114">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="3c9bb-115">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="3c9bb-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="3c9bb-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="3c9bb-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3c9bb-117">Указывает, требует ли привязка подтверждения подписи.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-117">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c9bb-118">Требования</span><span class="sxs-lookup"><span data-stu-id="3c9bb-118">Requirements</span></span>  
  
|<span data-ttu-id="3c9bb-119">MOF</span><span class="sxs-lookup"><span data-stu-id="3c9bb-119">MOF</span></span>|<span data-ttu-id="3c9bb-120">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-120">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3c9bb-121">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="3c9bb-121">Namespace</span></span>|<span data-ttu-id="3c9bb-122">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-122">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c9bb-123">См. также</span><span class="sxs-lookup"><span data-stu-id="3c9bb-123">See also</span></span>

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
