---
description: Дополнительные сведения о том, как разрешать конфликты путем перезаписи значений базы данных.
title: Практическое руководство. Как разрешать конфликты путем переписывания значений базы данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 4eaa66b4bb49706bb1ca6449d24c688a89f2750b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723508"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="e7f5e-103">Практическое руководство. Как разрешать конфликты путем переписывания значений базы данных</span><span class="sxs-lookup"><span data-stu-id="e7f5e-103">How to: Resolve Conflicts by Overwriting Database Values</span></span>

<span data-ttu-id="e7f5e-104">Чтобы выверить различия между ожидаемыми и фактическими значениями базы данных до повторной отправки изменений, можно воспользоваться <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> для перезаписи значений базы данных.</span><span class="sxs-lookup"><span data-stu-id="e7f5e-104">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="e7f5e-105">Дополнительные сведения см. в разделе [Оптимистическая блокировка: обзор](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e7f5e-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7f5e-106">Во всех случаях запись на клиенте сначала обновляется путем извлечения обновленных данных из базы данных.</span><span class="sxs-lookup"><span data-stu-id="e7f5e-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="e7f5e-107">Это действие гарантирует успешное выполнение следующей попытки обновления при тех же проверках параллелизма.</span><span class="sxs-lookup"><span data-stu-id="e7f5e-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7f5e-108">Пример</span><span class="sxs-lookup"><span data-stu-id="e7f5e-108">Example</span></span>  

 <span data-ttu-id="e7f5e-109">В данном сценарии, когда Пользователь1 пытается отправить изменения, возникает исключение <xref:System.Data.Linq.ChangeConflictException>, поскольку Пользователь2 в это время изменил столбцы "Помощник" и "Отдел".</span><span class="sxs-lookup"><span data-stu-id="e7f5e-109">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="e7f5e-110">Эта ситуация представлена в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="e7f5e-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="e7f5e-111">Manager</span><span class="sxs-lookup"><span data-stu-id="e7f5e-111">Manager</span></span>|<span data-ttu-id="e7f5e-112">Помощник</span><span class="sxs-lookup"><span data-stu-id="e7f5e-112">Assistant</span></span>|<span data-ttu-id="e7f5e-113">отдел;</span><span class="sxs-lookup"><span data-stu-id="e7f5e-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="e7f5e-114">Исходное состояние базы данных при отправке запросов Пользователем1 и Пользователем2.</span><span class="sxs-lookup"><span data-stu-id="e7f5e-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="e7f5e-115">Алексеи</span><span class="sxs-lookup"><span data-stu-id="e7f5e-115">Alfreds</span></span>|<span data-ttu-id="e7f5e-116">Мария</span><span class="sxs-lookup"><span data-stu-id="e7f5e-116">Maria</span></span>|<span data-ttu-id="e7f5e-117">Sales</span><span class="sxs-lookup"><span data-stu-id="e7f5e-117">Sales</span></span>|  
|<span data-ttu-id="e7f5e-118">Пользователь1 готовится отправить изменения.</span><span class="sxs-lookup"><span data-stu-id="e7f5e-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="e7f5e-119">Алексей</span><span class="sxs-lookup"><span data-stu-id="e7f5e-119">Alfred</span></span>||<span data-ttu-id="e7f5e-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="e7f5e-120">Marketing</span></span>|  
|<span data-ttu-id="e7f5e-121">Пользователь2 уже отправил изменения.</span><span class="sxs-lookup"><span data-stu-id="e7f5e-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="e7f5e-122">Инна</span><span class="sxs-lookup"><span data-stu-id="e7f5e-122">Mary</span></span>|<span data-ttu-id="e7f5e-123">Служба</span><span class="sxs-lookup"><span data-stu-id="e7f5e-123">Service</span></span>|  
  
 <span data-ttu-id="e7f5e-124">Пользователь1 решает устранить этот конфликт путем перезаписи значений базы данных текущими значениями членов клиента.</span><span class="sxs-lookup"><span data-stu-id="e7f5e-124">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="e7f5e-125">При устранении Пользователем1 конфликта с помощью <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> результат в базе данных будет соответствовать данным в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="e7f5e-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="e7f5e-126">Manager</span><span class="sxs-lookup"><span data-stu-id="e7f5e-126">Manager</span></span>|<span data-ttu-id="e7f5e-127">Помощник</span><span class="sxs-lookup"><span data-stu-id="e7f5e-127">Assistant</span></span>|<span data-ttu-id="e7f5e-128">отдел;</span><span class="sxs-lookup"><span data-stu-id="e7f5e-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="e7f5e-129">Новое состояние после устранения конфликта.</span><span class="sxs-lookup"><span data-stu-id="e7f5e-129">New state after conflict resolution.</span></span>|<span data-ttu-id="e7f5e-130">Алексей</span><span class="sxs-lookup"><span data-stu-id="e7f5e-130">Alfred</span></span><br /><br /> <span data-ttu-id="e7f5e-131">(от Пользователя1)</span><span class="sxs-lookup"><span data-stu-id="e7f5e-131">(from User1)</span></span>|<span data-ttu-id="e7f5e-132">Мария</span><span class="sxs-lookup"><span data-stu-id="e7f5e-132">Maria</span></span><br /><br /> <span data-ttu-id="e7f5e-133">(исходное значение)</span><span class="sxs-lookup"><span data-stu-id="e7f5e-133">(original)</span></span>|<span data-ttu-id="e7f5e-134">Marketing</span><span class="sxs-lookup"><span data-stu-id="e7f5e-134">Marketing</span></span><br /><br /> <span data-ttu-id="e7f5e-135">(от Пользователя1)</span><span class="sxs-lookup"><span data-stu-id="e7f5e-135">(from User1)</span></span>|  
  
 <span data-ttu-id="e7f5e-136">В следующем примере кода показано, как перезаписать значения базы данных текущими значениями членов клиента</span><span class="sxs-lookup"><span data-stu-id="e7f5e-136">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="e7f5e-137">(проверка или пользовательская обработка конфликтов отдельных членов не выполняется).</span><span class="sxs-lookup"><span data-stu-id="e7f5e-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e7f5e-138">См. также</span><span class="sxs-lookup"><span data-stu-id="e7f5e-138">See also</span></span>

- [<span data-ttu-id="e7f5e-139">Практическое руководство. Как управлять конфликтами изменений</span><span class="sxs-lookup"><span data-stu-id="e7f5e-139">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
