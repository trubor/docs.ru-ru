---
description: Дополнительные сведения см. в статье как разрешать конфликты путем удержания значений базы данных.
title: Практическое руководство. Как разрешать конфликты параллелизма путем сохранения значений базы данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: ef47370768ce474ccb6d941bcec0e66807290599
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723495"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="2f61d-103">Практическое руководство. Как разрешать конфликты параллелизма путем сохранения значений базы данных</span><span class="sxs-lookup"><span data-stu-id="2f61d-103">How to: Resolve Conflicts by Retaining Database Values</span></span>

<span data-ttu-id="2f61d-104">Чтобы согласовать различия между ожидаемыми и фактическими значениями базы данных до повторной отправки изменений, можно воспользоваться <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> для сохранения значений, найденных в базе данных.</span><span class="sxs-lookup"><span data-stu-id="2f61d-104">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="2f61d-105">Текущие значения в объектной модели при этом перезаписываются.</span><span class="sxs-lookup"><span data-stu-id="2f61d-105">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="2f61d-106">Дополнительные сведения см. в разделе [Оптимистическая блокировка: обзор](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2f61d-106">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f61d-107">Во всех случаях запись на клиенте сначала обновляется путем извлечения обновленных данных из базы данных.</span><span class="sxs-lookup"><span data-stu-id="2f61d-107">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="2f61d-108">Это действие гарантирует успешное выполнение следующей попытки обновления при тех же проверках параллелизма.</span><span class="sxs-lookup"><span data-stu-id="2f61d-108">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f61d-109">Пример</span><span class="sxs-lookup"><span data-stu-id="2f61d-109">Example</span></span>  

 <span data-ttu-id="2f61d-110">В данном сценарии, когда Пользователь1 пытается отправить изменения, возникает исключение <xref:System.Data.Linq.ChangeConflictException>, поскольку Пользователь2 в это время изменил столбцы "Помощник" и "Отдел".</span><span class="sxs-lookup"><span data-stu-id="2f61d-110">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="2f61d-111">Эта ситуация представлена в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="2f61d-111">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="2f61d-112">Manager</span><span class="sxs-lookup"><span data-stu-id="2f61d-112">Manager</span></span>|<span data-ttu-id="2f61d-113">Помощник</span><span class="sxs-lookup"><span data-stu-id="2f61d-113">Assistant</span></span>|<span data-ttu-id="2f61d-114">отдел;</span><span class="sxs-lookup"><span data-stu-id="2f61d-114">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="2f61d-115">Исходное состояние базы данных при отправке запросов Пользователем1 и Пользователем2.</span><span class="sxs-lookup"><span data-stu-id="2f61d-115">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="2f61d-116">Алексеи</span><span class="sxs-lookup"><span data-stu-id="2f61d-116">Alfreds</span></span>|<span data-ttu-id="2f61d-117">Мария</span><span class="sxs-lookup"><span data-stu-id="2f61d-117">Maria</span></span>|<span data-ttu-id="2f61d-118">Sales</span><span class="sxs-lookup"><span data-stu-id="2f61d-118">Sales</span></span>|  
|<span data-ttu-id="2f61d-119">Пользователь1 готовится отправить изменения.</span><span class="sxs-lookup"><span data-stu-id="2f61d-119">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="2f61d-120">Алексей</span><span class="sxs-lookup"><span data-stu-id="2f61d-120">Alfred</span></span>||<span data-ttu-id="2f61d-121">Marketing</span><span class="sxs-lookup"><span data-stu-id="2f61d-121">Marketing</span></span>|  
|<span data-ttu-id="2f61d-122">Пользователь2 уже отправил изменения.</span><span class="sxs-lookup"><span data-stu-id="2f61d-122">User2 has already submitted these changes.</span></span>||<span data-ttu-id="2f61d-123">Инна</span><span class="sxs-lookup"><span data-stu-id="2f61d-123">Mary</span></span>|<span data-ttu-id="2f61d-124">Служба</span><span class="sxs-lookup"><span data-stu-id="2f61d-124">Service</span></span>|  
  
 <span data-ttu-id="2f61d-125">Пользователь1 решает устранить этот конфликт путем перезаписи текущих значений из объектной модели более новыми значениями базы данных.</span><span class="sxs-lookup"><span data-stu-id="2f61d-125">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="2f61d-126">При устранении Пользователем1 конфликта с помощью <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> результат в базе данных будет соответствовать данным в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="2f61d-126">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="2f61d-127">Manager</span><span class="sxs-lookup"><span data-stu-id="2f61d-127">Manager</span></span>|<span data-ttu-id="2f61d-128">Помощник</span><span class="sxs-lookup"><span data-stu-id="2f61d-128">Assistant</span></span>|<span data-ttu-id="2f61d-129">отдел;</span><span class="sxs-lookup"><span data-stu-id="2f61d-129">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="2f61d-130">Новое состояние после устранения конфликта.</span><span class="sxs-lookup"><span data-stu-id="2f61d-130">New state after conflict resolution.</span></span>|<span data-ttu-id="2f61d-131">Алексеи</span><span class="sxs-lookup"><span data-stu-id="2f61d-131">Alfreds</span></span><br /><br /> <span data-ttu-id="2f61d-132">(исходное значение)</span><span class="sxs-lookup"><span data-stu-id="2f61d-132">(original)</span></span>|<span data-ttu-id="2f61d-133">Инна</span><span class="sxs-lookup"><span data-stu-id="2f61d-133">Mary</span></span><br /><br /> <span data-ttu-id="2f61d-134">(от Пользователя2)</span><span class="sxs-lookup"><span data-stu-id="2f61d-134">(from User2)</span></span>|<span data-ttu-id="2f61d-135">Служба</span><span class="sxs-lookup"><span data-stu-id="2f61d-135">Service</span></span><br /><br /> <span data-ttu-id="2f61d-136">(от Пользователя2)</span><span class="sxs-lookup"><span data-stu-id="2f61d-136">(from User2)</span></span>|  
  
 <span data-ttu-id="2f61d-137">В следующем примере кода показано, как перезаписать текущие значения из объектной модели значениями базы данных</span><span class="sxs-lookup"><span data-stu-id="2f61d-137">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="2f61d-138">(проверка или пользовательская обработка конфликтов отдельных членов не выполняется).</span><span class="sxs-lookup"><span data-stu-id="2f61d-138">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2f61d-139">См. также</span><span class="sxs-lookup"><span data-stu-id="2f61d-139">See also</span></span>

- [<span data-ttu-id="2f61d-140">Практическое руководство. Как управлять конфликтами изменений</span><span class="sxs-lookup"><span data-stu-id="2f61d-140">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
