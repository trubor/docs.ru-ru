---
description: 'Дополнительные сведения о: SymmetricSecurityBindingElement'
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: c158f0bedec91a74b305f359889dd307cff48079
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715305"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="55a38-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="55a38-103">SymmetricSecurityBindingElement</span></span>

<span data-ttu-id="55a38-104">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="55a38-104">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55a38-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="55a38-105">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="55a38-106">Методы</span><span class="sxs-lookup"><span data-stu-id="55a38-106">Methods</span></span>  

 <span data-ttu-id="55a38-107">Класс SymmetricSecurityBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="55a38-107">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="55a38-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="55a38-108">Properties</span></span>  

 <span data-ttu-id="55a38-109">Класс SymmetricSecurityBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="55a38-109">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="55a38-110">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="55a38-110">MessageProtectionOrder</span></span>  

 <span data-ttu-id="55a38-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="55a38-111">Data type: string</span></span>  
  
 <span data-ttu-id="55a38-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="55a38-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55a38-113">Порядок шифрования и подписывания сообщений для данной привязки.</span><span class="sxs-lookup"><span data-stu-id="55a38-113">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="55a38-114">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="55a38-114">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="55a38-115">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="55a38-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="55a38-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="55a38-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55a38-117">Указывает, требует ли привязка подтверждения подписи.</span><span class="sxs-lookup"><span data-stu-id="55a38-117">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55a38-118">Требования</span><span class="sxs-lookup"><span data-stu-id="55a38-118">Requirements</span></span>  
  
|<span data-ttu-id="55a38-119">MOF</span><span class="sxs-lookup"><span data-stu-id="55a38-119">MOF</span></span>|<span data-ttu-id="55a38-120">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="55a38-120">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="55a38-121">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="55a38-121">Namespace</span></span>|<span data-ttu-id="55a38-122">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="55a38-122">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55a38-123">См. также</span><span class="sxs-lookup"><span data-stu-id="55a38-123">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
