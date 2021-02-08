---
description: 'Дополнительные сведения о: OperationBehaviorAttribute'
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: c1f1b80134163ee65d5015e52017f5bb455aeac7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803065"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="b74b7-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="b74b7-103">OperationBehaviorAttribute</span></span>

<span data-ttu-id="b74b7-104">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="b74b7-104">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b74b7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b74b7-105">Syntax</span></span>  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b74b7-106">Методы</span><span class="sxs-lookup"><span data-stu-id="b74b7-106">Methods</span></span>  

 <span data-ttu-id="b74b7-107">Класс OperationBehaviorAttribute не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="b74b7-107">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b74b7-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="b74b7-108">Properties</span></span>  

 <span data-ttu-id="b74b7-109">Класс OperationBehaviorAttribute имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="b74b7-109">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="b74b7-110">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="b74b7-110">AutoDisposeParameters</span></span>  

 <span data-ttu-id="b74b7-111">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="b74b7-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="b74b7-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="b74b7-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b74b7-113">Состояние возможности автоматического удаления для параметров.</span><span class="sxs-lookup"><span data-stu-id="b74b7-113">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="b74b7-114">Олицетворение</span><span class="sxs-lookup"><span data-stu-id="b74b7-114">Impersonation</span></span>  

 <span data-ttu-id="b74b7-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="b74b7-115">Data type: string</span></span>  
  
 <span data-ttu-id="b74b7-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="b74b7-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b74b7-117">Указывает уровень олицетворения вызывающей стороны, который поддерживает операция.</span><span class="sxs-lookup"><span data-stu-id="b74b7-117">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="b74b7-118">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="b74b7-118">ReleaseInstanceMode</span></span>  

 <span data-ttu-id="b74b7-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="b74b7-119">Data type: string</span></span>  
  
 <span data-ttu-id="b74b7-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="b74b7-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b74b7-121">Указывает, когда удалять объект в процессе вызова операции.</span><span class="sxs-lookup"><span data-stu-id="b74b7-121">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="b74b7-122">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="b74b7-122">TransactionAutoComplete</span></span>  

 <span data-ttu-id="b74b7-123">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="b74b7-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="b74b7-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="b74b7-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b74b7-125">Указывает, следует ли автоматически фиксировать текущую транзакцию при отсутствии необработанных исключений.</span><span class="sxs-lookup"><span data-stu-id="b74b7-125">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="b74b7-126">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="b74b7-126">TransactionScopeRequired</span></span>  

 <span data-ttu-id="b74b7-127">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="b74b7-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="b74b7-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="b74b7-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b74b7-129">Указывает, требует ли операция транзакции.</span><span class="sxs-lookup"><span data-stu-id="b74b7-129">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b74b7-130">Требования</span><span class="sxs-lookup"><span data-stu-id="b74b7-130">Requirements</span></span>  
  
|<span data-ttu-id="b74b7-131">MOF</span><span class="sxs-lookup"><span data-stu-id="b74b7-131">MOF</span></span>|<span data-ttu-id="b74b7-132">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b74b7-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b74b7-133">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="b74b7-133">Namespace</span></span>|<span data-ttu-id="b74b7-134">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="b74b7-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b74b7-135">См. также</span><span class="sxs-lookup"><span data-stu-id="b74b7-135">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
