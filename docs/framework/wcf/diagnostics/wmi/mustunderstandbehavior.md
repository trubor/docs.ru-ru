---
description: 'Дополнительные сведения о: Мустундерстандбехавиор'
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 173548f2f3346a79bf7f53c90384db94a638a366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803130"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="8e1b7-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="8e1b7-103">MustUnderstandBehavior</span></span>

<span data-ttu-id="8e1b7-104">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="8e1b7-104">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e1b7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8e1b7-105">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8e1b7-106">Методы</span><span class="sxs-lookup"><span data-stu-id="8e1b7-106">Methods</span></span>  

 <span data-ttu-id="8e1b7-107">Класс MustUnderstandBehavior не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="8e1b7-107">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8e1b7-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="8e1b7-108">Properties</span></span>  

 <span data-ttu-id="8e1b7-109">Класс MustUnderstandBehavior содержит следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="8e1b7-109">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="8e1b7-110">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="8e1b7-110">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="8e1b7-111">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="8e1b7-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="8e1b7-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="8e1b7-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e1b7-113">Если логическое значение равно `true`, все заголовки SOAP с атрибутом `MustUnderstand` не обрабатываются, потому что поведение создало исключение.</span><span class="sxs-lookup"><span data-stu-id="8e1b7-113">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e1b7-114">Требования</span><span class="sxs-lookup"><span data-stu-id="8e1b7-114">Requirements</span></span>  
  
|<span data-ttu-id="8e1b7-115">MOF</span><span class="sxs-lookup"><span data-stu-id="8e1b7-115">MOF</span></span>|<span data-ttu-id="8e1b7-116">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8e1b7-116">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8e1b7-117">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="8e1b7-117">Namespace</span></span>|<span data-ttu-id="8e1b7-118">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="8e1b7-118">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e1b7-119">См. также</span><span class="sxs-lookup"><span data-stu-id="8e1b7-119">See also</span></span>

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
