---
description: Дополнительные сведения см. в статье как разрешить конфликты путем слияния со значениями базы данных.
title: Практическое руководство. Как разрешать конфликты путем слияния значений базы данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: 83cae4c98fdd2e51065c66d36ef04202bdc86c9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767769"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a><span data-ttu-id="91d16-103">Практическое руководство. Как разрешать конфликты путем слияния значений базы данных</span><span class="sxs-lookup"><span data-stu-id="91d16-103">How to: Resolve Conflicts by Merging with Database Values</span></span>

<span data-ttu-id="91d16-104">Чтобы согласовать различия между ожидаемыми и фактическими значениями базы данных до повторной отправки изменений, можно воспользоваться <xref:System.Data.Linq.RefreshMode.KeepChanges> для слияния значений базы данных с текущими значениями члена клиента.</span><span class="sxs-lookup"><span data-stu-id="91d16-104">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepChanges> to merge database values with the current client member values.</span></span> <span data-ttu-id="91d16-105">Дополнительные сведения см. в разделе [Оптимистическая блокировка: обзор](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="91d16-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91d16-106">Во всех случаях запись на клиенте сначала обновляется путем извлечения обновленных данных из базы данных.</span><span class="sxs-lookup"><span data-stu-id="91d16-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="91d16-107">Это действие гарантирует успешное выполнение следующей попытки обновления при тех же проверках параллелизма.</span><span class="sxs-lookup"><span data-stu-id="91d16-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91d16-108">Пример</span><span class="sxs-lookup"><span data-stu-id="91d16-108">Example</span></span>  

 <span data-ttu-id="91d16-109">В данном сценарии, когда Пользователь1 пытается отправить изменения, возникает исключение <xref:System.Data.Linq.ChangeConflictException>, поскольку Пользователь2 в это время изменил столбцы "Помощник" и "Отдел".</span><span class="sxs-lookup"><span data-stu-id="91d16-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="91d16-110">Эта ситуация представлена в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="91d16-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="91d16-111">Manager</span><span class="sxs-lookup"><span data-stu-id="91d16-111">Manager</span></span>|<span data-ttu-id="91d16-112">Помощник</span><span class="sxs-lookup"><span data-stu-id="91d16-112">Assistant</span></span>|<span data-ttu-id="91d16-113">отдел;</span><span class="sxs-lookup"><span data-stu-id="91d16-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="91d16-114">Исходное состояние базы данных при отправке запросов Пользователем1 и Пользователем2.</span><span class="sxs-lookup"><span data-stu-id="91d16-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="91d16-115">Алексеи</span><span class="sxs-lookup"><span data-stu-id="91d16-115">Alfreds</span></span>|<span data-ttu-id="91d16-116">Мария</span><span class="sxs-lookup"><span data-stu-id="91d16-116">Maria</span></span>|<span data-ttu-id="91d16-117">Sales</span><span class="sxs-lookup"><span data-stu-id="91d16-117">Sales</span></span>|  
|<span data-ttu-id="91d16-118">Пользователь1 готовится отправить изменения.</span><span class="sxs-lookup"><span data-stu-id="91d16-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="91d16-119">Алексей</span><span class="sxs-lookup"><span data-stu-id="91d16-119">Alfred</span></span>||<span data-ttu-id="91d16-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="91d16-120">Marketing</span></span>|  
|<span data-ttu-id="91d16-121">Пользователь2 уже отправил изменения.</span><span class="sxs-lookup"><span data-stu-id="91d16-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="91d16-122">Инна</span><span class="sxs-lookup"><span data-stu-id="91d16-122">Mary</span></span>|<span data-ttu-id="91d16-123">Служба</span><span class="sxs-lookup"><span data-stu-id="91d16-123">Service</span></span>|  
  
 <span data-ttu-id="91d16-124">Пользователь1 решает устранить этот конфликт путем объединения значений базы данных с текущими значениями члена клиента.</span><span class="sxs-lookup"><span data-stu-id="91d16-124">User1 decides to resolve this conflict by merging database values with the current client member values.</span></span> <span data-ttu-id="91d16-125">Ожидаемый результат: значения базы данных будут переопределены только при изменении значения текущим набором изменений.</span><span class="sxs-lookup"><span data-stu-id="91d16-125">The result will be that database values are overwritten only when the current changeset has also modified that value.</span></span>  
  
 <span data-ttu-id="91d16-126">При устранении Пользователем1 конфликта с помощью <xref:System.Data.Linq.RefreshMode.KeepChanges> результат в базе данных будет соответствовать данным в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="91d16-126">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepChanges>, the result in the database is as in the following table:</span></span>  
  
||<span data-ttu-id="91d16-127">Manager</span><span class="sxs-lookup"><span data-stu-id="91d16-127">Manager</span></span>|<span data-ttu-id="91d16-128">Помощник</span><span class="sxs-lookup"><span data-stu-id="91d16-128">Assistant</span></span>|<span data-ttu-id="91d16-129">отдел;</span><span class="sxs-lookup"><span data-stu-id="91d16-129">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="91d16-130">Новое состояние после устранения конфликта.</span><span class="sxs-lookup"><span data-stu-id="91d16-130">New state after conflict resolution.</span></span>|<span data-ttu-id="91d16-131">Алексей</span><span class="sxs-lookup"><span data-stu-id="91d16-131">Alfred</span></span><br /><br /> <span data-ttu-id="91d16-132">(от Пользователя1)</span><span class="sxs-lookup"><span data-stu-id="91d16-132">(from User1)</span></span>|<span data-ttu-id="91d16-133">Инна</span><span class="sxs-lookup"><span data-stu-id="91d16-133">Mary</span></span><br /><br /> <span data-ttu-id="91d16-134">(от Пользователя2)</span><span class="sxs-lookup"><span data-stu-id="91d16-134">(from User2)</span></span>|<span data-ttu-id="91d16-135">Marketing</span><span class="sxs-lookup"><span data-stu-id="91d16-135">Marketing</span></span><br /><br /> <span data-ttu-id="91d16-136">(от Пользователя1)</span><span class="sxs-lookup"><span data-stu-id="91d16-136">(from User1)</span></span>|  
  
 <span data-ttu-id="91d16-137">В следующем примере показано объединение значений базы данных с текущими значениями члена клиента (если клиент также не изменил это значение).</span><span class="sxs-lookup"><span data-stu-id="91d16-137">The following example shows how to merge database values with the current client member values (unless the client has also changed that value).</span></span> <span data-ttu-id="91d16-138">Конфликты проверки или пользовательской обработки отдельных членов не возникают.</span><span class="sxs-lookup"><span data-stu-id="91d16-138">No inspection or custom handling of individual member conflicts occurs.</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="91d16-139">См. также</span><span class="sxs-lookup"><span data-stu-id="91d16-139">See also</span></span>

- [<span data-ttu-id="91d16-140">Практическое руководство. Как разрешать конфликты путем переписывания значений базы данных</span><span class="sxs-lookup"><span data-stu-id="91d16-140">How to: Resolve Conflicts by Overwriting Database Values</span></span>](how-to-resolve-conflicts-by-overwriting-database-values.md)
- [<span data-ttu-id="91d16-141">Практическое руководство. Как разрешать конфликты параллелизма путем сохранения значений базы данных</span><span class="sxs-lookup"><span data-stu-id="91d16-141">How to: Resolve Conflicts by Retaining Database Values</span></span>](how-to-resolve-conflicts-by-retaining-database-values.md)
- [<span data-ttu-id="91d16-142">Практическое руководство. Как управлять конфликтами изменений</span><span class="sxs-lookup"><span data-stu-id="91d16-142">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
