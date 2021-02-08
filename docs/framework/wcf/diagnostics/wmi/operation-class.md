---
description: 'Дополнительные сведения: Класс Operation'
title: Класс операции
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 035c02bc05b7a64c5d15538001dbdcf2ec0b135b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803078"
---
# <a name="operation-class"></a><span data-ttu-id="daba5-103">Класс операции</span><span class="sxs-lookup"><span data-stu-id="daba5-103">Operation class</span></span>

<span data-ttu-id="daba5-104">Операция</span><span class="sxs-lookup"><span data-stu-id="daba5-104">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daba5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="daba5-105">Syntax</span></span>  
  
```csharp
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="daba5-106">Методы</span><span class="sxs-lookup"><span data-stu-id="daba5-106">Methods</span></span>  

 <span data-ttu-id="daba5-107">Класс Operation не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="daba5-107">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="daba5-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="daba5-108">Properties</span></span>  

 <span data-ttu-id="daba5-109">Класс Operation имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="daba5-109">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="daba5-110">Действие</span><span class="sxs-lookup"><span data-stu-id="daba5-110">Action</span></span>  

 <span data-ttu-id="daba5-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="daba5-111">Data type: string</span></span>  
  
 <span data-ttu-id="daba5-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="daba5-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daba5-113">Действие WS-Addressing сообщения запроса.</span><span class="sxs-lookup"><span data-stu-id="daba5-113">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="daba5-114">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="daba5-114">AsyncPattern</span></span>  

 <span data-ttu-id="daba5-115">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="daba5-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="daba5-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="daba5-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daba5-117">Указывает, что операция реализуется асинхронно с помощью `Begin` пары методов [открывающий/закрывающий угловые скобки] и `End` [открывающих и закрывающих угловых скобок] в контракте службы.</span><span class="sxs-lookup"><span data-stu-id="daba5-117">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="daba5-118">Расширения функциональности</span><span class="sxs-lookup"><span data-stu-id="daba5-118">Behaviors</span></span>  

 <span data-ttu-id="daba5-119">Тип данных: массив Behavior</span><span class="sxs-lookup"><span data-stu-id="daba5-119">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="daba5-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="daba5-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daba5-121">Поведения, связанные с этой операцией.</span><span class="sxs-lookup"><span data-stu-id="daba5-121">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="daba5-122">IsCallback</span><span class="sxs-lookup"><span data-stu-id="daba5-122">IsCallback</span></span>  

 <span data-ttu-id="daba5-123">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="daba5-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="daba5-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="daba5-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daba5-125">Истинно, если операция является операцией обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="daba5-125">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="daba5-126">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="daba5-126">IsInitiating</span></span>  

 <span data-ttu-id="daba5-127">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="daba5-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="daba5-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="daba5-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daba5-129">Показывает, реализует ли метод операцию, которая может инициировать сеанс на сервере.</span><span class="sxs-lookup"><span data-stu-id="daba5-129">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="daba5-130">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="daba5-130">IsOneWay</span></span>  

 <span data-ttu-id="daba5-131">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="daba5-131">Data type: boolean</span></span>  
  
 <span data-ttu-id="daba5-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="daba5-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daba5-133">Показывает, возвращает ли операция ответное сообщение.</span><span class="sxs-lookup"><span data-stu-id="daba5-133">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="daba5-134">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="daba5-134">IsTerminating</span></span>  

 <span data-ttu-id="daba5-135">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="daba5-135">Data type: boolean</span></span>  
  
 <span data-ttu-id="daba5-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="daba5-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daba5-137">Показывает, возвращает ли операция ответное сообщение.</span><span class="sxs-lookup"><span data-stu-id="daba5-137">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="daba5-138">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="daba5-138">MethodSignature</span></span>  

 <span data-ttu-id="daba5-139">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="daba5-139">Data type: string</span></span>  
  
 <span data-ttu-id="daba5-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="daba5-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daba5-141">Подпись метода операции.</span><span class="sxs-lookup"><span data-stu-id="daba5-141">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="daba5-142">Имя</span><span class="sxs-lookup"><span data-stu-id="daba5-142">Name</span></span>  

 <span data-ttu-id="daba5-143">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="daba5-143">Data type: string</span></span>  
  
 <span data-ttu-id="daba5-144">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="daba5-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daba5-145">Имя операции.</span><span class="sxs-lookup"><span data-stu-id="daba5-145">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="daba5-146">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="daba5-146">ParameterTypes</span></span>  

 <span data-ttu-id="daba5-147">Тип данных: массив строк</span><span class="sxs-lookup"><span data-stu-id="daba5-147">Data type: string array</span></span>  
  
 <span data-ttu-id="daba5-148">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="daba5-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daba5-149">Типы параметров операции.</span><span class="sxs-lookup"><span data-stu-id="daba5-149">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="daba5-150">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="daba5-150">ReplyAction</span></span>  

 <span data-ttu-id="daba5-151">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="daba5-151">Data type: string</span></span>  
  
 <span data-ttu-id="daba5-152">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="daba5-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daba5-153">Значение действия SOAP для ответного сообщения операции.</span><span class="sxs-lookup"><span data-stu-id="daba5-153">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="daba5-154">ReturnType</span><span class="sxs-lookup"><span data-stu-id="daba5-154">ReturnType</span></span>  

 <span data-ttu-id="daba5-155">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="daba5-155">Data type: string</span></span>  
  
 <span data-ttu-id="daba5-156">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="daba5-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daba5-157">Тип возвращаемого значения операции.</span><span class="sxs-lookup"><span data-stu-id="daba5-157">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daba5-158">Требования</span><span class="sxs-lookup"><span data-stu-id="daba5-158">Requirements</span></span>  
  
|<span data-ttu-id="daba5-159">MOF</span><span class="sxs-lookup"><span data-stu-id="daba5-159">MOF</span></span>|<span data-ttu-id="daba5-160">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="daba5-160">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="daba5-161">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="daba5-161">Namespace</span></span>|<span data-ttu-id="daba5-162">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="daba5-162">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="daba5-163">См. также</span><span class="sxs-lookup"><span data-stu-id="daba5-163">See also</span></span>

- <xref:System.ServiceModel.Description.OperationDescription>
