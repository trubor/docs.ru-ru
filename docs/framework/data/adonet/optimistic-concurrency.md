---
description: Дополнительные сведения о оптимистичном параллелизме
title: Оптимистическая блокировка
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: 1034720b2c57b863b87eef440424a7e2f4c2c6c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739148"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="152e6-103">Оптимистическая блокировка</span><span class="sxs-lookup"><span data-stu-id="152e6-103">Optimistic Concurrency</span></span>

<span data-ttu-id="152e6-104">В многопользовательской среде предусмотрены две модели обновления данных в базе данных: оптимистичный параллелизм и пессимистичный параллелизм.</span><span class="sxs-lookup"><span data-stu-id="152e6-104">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="152e6-105">Объект <xref:System.Data.DataSet> предназначен для стимулирования использования оптимистичного параллелизма для длительный действий, таких как удаленный доступ к данным и взаимодействие с данными.</span><span class="sxs-lookup"><span data-stu-id="152e6-105">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="152e6-106">Пессимистичный параллелизм предусматривает блокировку строк в источнике данных, что позволяет запретить другим пользователям модификацию данных, которая может отрицательно повлиять на работу текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="152e6-106">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="152e6-107">В пессимистической модели, когда пользователь выполняет действие, вызывающее применение блокировки, другие пользователи не могут выполнять действия, которые могли бы конфликтовать с этой блокировкой, до тех пор как владелец блокировки ее не снимет.</span><span class="sxs-lookup"><span data-stu-id="152e6-107">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="152e6-108">Эта модель в основном используется в таких средах, где наблюдается интенсивная конкуренция по доступу к данным, поэтому расходы на защиту данных с помощью блокировок оказываются меньше по сравнению с расходами на откаты транзакций, обусловленные возникновением конфликтов параллельного доступа.</span><span class="sxs-lookup"><span data-stu-id="152e6-108">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="152e6-109">Поэтому в модели с пессимистичным параллелизмом пользователь, обновляющий строку, устанавливает блокировку.</span><span class="sxs-lookup"><span data-stu-id="152e6-109">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="152e6-110">До тех пор пока пользователь не закончит обновление и не снимет блокировку, больше никто другой не сможет вносить изменения в эту строку.</span><span class="sxs-lookup"><span data-stu-id="152e6-110">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="152e6-111">Это означает, что пессимистичный параллелизм является наиболее подходящим в тех ситуациях, когда блокировки устанавливаются на короткое время, например как при программной обработке записей.</span><span class="sxs-lookup"><span data-stu-id="152e6-111">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="152e6-112">Применение пессимистичного параллелизма становится препятствием для масштабирования приложения, когда пользователи взаимодействуют с данными и вызывают блокировку записей на относительно большие промежутки времени.</span><span class="sxs-lookup"><span data-stu-id="152e6-112">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="152e6-113">Если в приложении требуется обновлять несколько строк в одной операции, то создание транзакций обеспечивает лучшее масштабирование по сравнению с использованием пессимистичных блокировок.</span><span class="sxs-lookup"><span data-stu-id="152e6-113">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="152e6-114">В отличие от этого, пользователи, применяющие оптимистичный параллелизм, не блокируют строку при ее чтении.</span><span class="sxs-lookup"><span data-stu-id="152e6-114">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="152e6-115">Когда пользователю требуется обновить строку, приложение должно определить, не изменялась ли эта строка другим пользователем после того, как она была открыта для чтения.</span><span class="sxs-lookup"><span data-stu-id="152e6-115">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="152e6-116">Оптимистичный параллелизм обычно используется в средах, характеризующихся низкой конкуренцией за данные.</span><span class="sxs-lookup"><span data-stu-id="152e6-116">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="152e6-117">Применение оптимистичного параллелизма способствует повышению производительности благодаря тому, что не требуется блокировка записей, которая требует дополнительных ресурсов сервера.</span><span class="sxs-lookup"><span data-stu-id="152e6-117">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="152e6-118">Кроме того, для блокировки записей требуется постоянное соединение с сервером базы данных.</span><span class="sxs-lookup"><span data-stu-id="152e6-118">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="152e6-119">При использовании модели оптимистичного параллелизма такая необходимость отсутствует, поэтому соединения с сервером можно применять для обслуживания большего количества клиентов за меньшее время.</span><span class="sxs-lookup"><span data-stu-id="152e6-119">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="152e6-120">В модели оптимистичного параллелизма конфликтом параллельного доступа считается ситуация, когда вслед за получением пользователем значения из базы данных другой пользователь изменяет это значение до того, как первый пользователь попытается его изменить.</span><span class="sxs-lookup"><span data-stu-id="152e6-120">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="152e6-121">Разрешение конфликта параллельного доступа лучше всего показать, рассмотрев следующий пример.</span><span class="sxs-lookup"><span data-stu-id="152e6-121">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="152e6-122">В следующих таблицах рассматривается пример оптимистичного параллелизма.</span><span class="sxs-lookup"><span data-stu-id="152e6-122">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="152e6-123">В 13:00 Пользователь1 считывает из базы данных строку со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="152e6-123">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="152e6-124">**CustID     LastName     FirstName**</span><span class="sxs-lookup"><span data-stu-id="152e6-124">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="152e6-125">101          Smith             Bob</span><span class="sxs-lookup"><span data-stu-id="152e6-125">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="152e6-126">Имя столбца</span><span class="sxs-lookup"><span data-stu-id="152e6-126">Column name</span></span>|<span data-ttu-id="152e6-127">Исходное значение</span><span class="sxs-lookup"><span data-stu-id="152e6-127">Original value</span></span>|<span data-ttu-id="152e6-128">Текущее значение</span><span class="sxs-lookup"><span data-stu-id="152e6-128">Current value</span></span>|<span data-ttu-id="152e6-129">Значение в базе данных</span><span class="sxs-lookup"><span data-stu-id="152e6-129">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="152e6-130">CustID</span><span class="sxs-lookup"><span data-stu-id="152e6-130">CustID</span></span>|<span data-ttu-id="152e6-131">101</span><span class="sxs-lookup"><span data-stu-id="152e6-131">101</span></span>|<span data-ttu-id="152e6-132">101</span><span class="sxs-lookup"><span data-stu-id="152e6-132">101</span></span>|<span data-ttu-id="152e6-133">101</span><span class="sxs-lookup"><span data-stu-id="152e6-133">101</span></span>|  
|<span data-ttu-id="152e6-134">LastName</span><span class="sxs-lookup"><span data-stu-id="152e6-134">LastName</span></span>|<span data-ttu-id="152e6-135">Смит</span><span class="sxs-lookup"><span data-stu-id="152e6-135">Smith</span></span>|<span data-ttu-id="152e6-136">Смит</span><span class="sxs-lookup"><span data-stu-id="152e6-136">Smith</span></span>|<span data-ttu-id="152e6-137">Смит</span><span class="sxs-lookup"><span data-stu-id="152e6-137">Smith</span></span>|  
|<span data-ttu-id="152e6-138">FirstName</span><span class="sxs-lookup"><span data-stu-id="152e6-138">FirstName</span></span>|<span data-ttu-id="152e6-139">Владимир</span><span class="sxs-lookup"><span data-stu-id="152e6-139">Bob</span></span>|<span data-ttu-id="152e6-140">Владимир</span><span class="sxs-lookup"><span data-stu-id="152e6-140">Bob</span></span>|<span data-ttu-id="152e6-141">Владимир</span><span class="sxs-lookup"><span data-stu-id="152e6-141">Bob</span></span>|  
  
 <span data-ttu-id="152e6-142">В 13:01 Пользователь2 считывает ту же строку.</span><span class="sxs-lookup"><span data-stu-id="152e6-142">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="152e6-143">В 13:03 Пользователь2 изменяет значение **FirstName** с "Bob" на "Robert" и обновляет базу данных.</span><span class="sxs-lookup"><span data-stu-id="152e6-143">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="152e6-144">Имя столбца</span><span class="sxs-lookup"><span data-stu-id="152e6-144">Column name</span></span>|<span data-ttu-id="152e6-145">Исходное значение</span><span class="sxs-lookup"><span data-stu-id="152e6-145">Original value</span></span>|<span data-ttu-id="152e6-146">Текущее значение</span><span class="sxs-lookup"><span data-stu-id="152e6-146">Current value</span></span>|<span data-ttu-id="152e6-147">Значение в базе данных</span><span class="sxs-lookup"><span data-stu-id="152e6-147">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="152e6-148">CustID</span><span class="sxs-lookup"><span data-stu-id="152e6-148">CustID</span></span>|<span data-ttu-id="152e6-149">101</span><span class="sxs-lookup"><span data-stu-id="152e6-149">101</span></span>|<span data-ttu-id="152e6-150">101</span><span class="sxs-lookup"><span data-stu-id="152e6-150">101</span></span>|<span data-ttu-id="152e6-151">101</span><span class="sxs-lookup"><span data-stu-id="152e6-151">101</span></span>|  
|<span data-ttu-id="152e6-152">LastName</span><span class="sxs-lookup"><span data-stu-id="152e6-152">LastName</span></span>|<span data-ttu-id="152e6-153">Смит</span><span class="sxs-lookup"><span data-stu-id="152e6-153">Smith</span></span>|<span data-ttu-id="152e6-154">Смит</span><span class="sxs-lookup"><span data-stu-id="152e6-154">Smith</span></span>|<span data-ttu-id="152e6-155">Смит</span><span class="sxs-lookup"><span data-stu-id="152e6-155">Smith</span></span>|  
|<span data-ttu-id="152e6-156">FirstName</span><span class="sxs-lookup"><span data-stu-id="152e6-156">FirstName</span></span>|<span data-ttu-id="152e6-157">Владимир</span><span class="sxs-lookup"><span data-stu-id="152e6-157">Bob</span></span>|<span data-ttu-id="152e6-158">Robert</span><span class="sxs-lookup"><span data-stu-id="152e6-158">Robert</span></span>|<span data-ttu-id="152e6-159">Владимир</span><span class="sxs-lookup"><span data-stu-id="152e6-159">Bob</span></span>|  
  
 <span data-ttu-id="152e6-160">Эта операция обновления завершается успешно, поскольку значения в базе данных ко времени обновления соответствуют первоначальным значениям, которые имеются в распоряжении Пользователя2.</span><span class="sxs-lookup"><span data-stu-id="152e6-160">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="152e6-161">В 13:05 Пользователь1 изменяет значение FirstName с «Bob» на «James» и пытается обновить строку.</span><span class="sxs-lookup"><span data-stu-id="152e6-161">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="152e6-162">Имя столбца</span><span class="sxs-lookup"><span data-stu-id="152e6-162">Column name</span></span>|<span data-ttu-id="152e6-163">Исходное значение</span><span class="sxs-lookup"><span data-stu-id="152e6-163">Original value</span></span>|<span data-ttu-id="152e6-164">Текущее значение</span><span class="sxs-lookup"><span data-stu-id="152e6-164">Current value</span></span>|<span data-ttu-id="152e6-165">Значение в базе данных</span><span class="sxs-lookup"><span data-stu-id="152e6-165">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="152e6-166">CustID</span><span class="sxs-lookup"><span data-stu-id="152e6-166">CustID</span></span>|<span data-ttu-id="152e6-167">101</span><span class="sxs-lookup"><span data-stu-id="152e6-167">101</span></span>|<span data-ttu-id="152e6-168">101</span><span class="sxs-lookup"><span data-stu-id="152e6-168">101</span></span>|<span data-ttu-id="152e6-169">101</span><span class="sxs-lookup"><span data-stu-id="152e6-169">101</span></span>|  
|<span data-ttu-id="152e6-170">LastName</span><span class="sxs-lookup"><span data-stu-id="152e6-170">LastName</span></span>|<span data-ttu-id="152e6-171">Смит</span><span class="sxs-lookup"><span data-stu-id="152e6-171">Smith</span></span>|<span data-ttu-id="152e6-172">Смит</span><span class="sxs-lookup"><span data-stu-id="152e6-172">Smith</span></span>|<span data-ttu-id="152e6-173">Смит</span><span class="sxs-lookup"><span data-stu-id="152e6-173">Smith</span></span>|  
|<span data-ttu-id="152e6-174">FirstName</span><span class="sxs-lookup"><span data-stu-id="152e6-174">FirstName</span></span>|<span data-ttu-id="152e6-175">Владимир</span><span class="sxs-lookup"><span data-stu-id="152e6-175">Bob</span></span>|<span data-ttu-id="152e6-176">James</span><span class="sxs-lookup"><span data-stu-id="152e6-176">James</span></span>|<span data-ttu-id="152e6-177">Robert</span><span class="sxs-lookup"><span data-stu-id="152e6-177">Robert</span></span>|  
  
 <span data-ttu-id="152e6-178">В этот момент Пользователь1 обнаруживает нарушение оптимистичного параллелизма, поскольку значение в базе данных («Robert») больше не соответствует первоначальному значению, которое ожидал найти Пользователь1 («Bob»).</span><span class="sxs-lookup"><span data-stu-id="152e6-178">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="152e6-179">Это нарушение параллелизма просто позволяет узнать о том, что обновление окончилось неудачей.</span><span class="sxs-lookup"><span data-stu-id="152e6-179">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="152e6-180">После этого нужно принять решение, следует ли перезаписать изменения, внесенные Пользователем2, изменениями, которые внес Пользователь1, или отменить изменения Пользователя1.</span><span class="sxs-lookup"><span data-stu-id="152e6-180">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="152e6-181">Проверка на наличие нарушений оптимистичного параллелизма</span><span class="sxs-lookup"><span data-stu-id="152e6-181">Testing for Optimistic Concurrency Violations</span></span>  

 <span data-ttu-id="152e6-182">Существует несколько методов проверки на наличие нарушений оптимистичного параллелизма.</span><span class="sxs-lookup"><span data-stu-id="152e6-182">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="152e6-183">Один из этих методов предусматривает включение столбца метки времени в таблицу.</span><span class="sxs-lookup"><span data-stu-id="152e6-183">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="152e6-184">Базы данных обычно предоставляют возможность использования отметок времени, которые могут служить для определения даты и времени последнего обновления записи.</span><span class="sxs-lookup"><span data-stu-id="152e6-184">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="152e6-185">При использовании этого метода в определение таблицы включается столбец метки времени.</span><span class="sxs-lookup"><span data-stu-id="152e6-185">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="152e6-186">После каждого обновления записи обновляется также метка времени, отражая текущую дату и время.</span><span class="sxs-lookup"><span data-stu-id="152e6-186">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="152e6-187">При проверке на наличие нарушений оптимистичного параллелизма при любом запросе к содержимому таблицы происходит возврат значений столбца метки времени.</span><span class="sxs-lookup"><span data-stu-id="152e6-187">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="152e6-188">При попытке обновления это значение метки времени из базы данных сравнивается с первоначальным значением метки времени, содержащимся в измененной строке.</span><span class="sxs-lookup"><span data-stu-id="152e6-188">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="152e6-189">Если эти значения совпадают, операция обновления выполняется и столбец метки времени обновляется с указанием текущего времени, чтобы отразить факт обновления.</span><span class="sxs-lookup"><span data-stu-id="152e6-189">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="152e6-190">Если эти значения не совпадают, то возникает конфликт оптимистичного параллелизма.</span><span class="sxs-lookup"><span data-stu-id="152e6-190">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="152e6-191">Еще один метод проверки на наличие нарушения оптимистичного параллелизма состоит в проверке того, что все первоначальные значения полей в строке все еще соответствуют находящимся в базе данных.</span><span class="sxs-lookup"><span data-stu-id="152e6-191">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="152e6-192">Например, рассмотрим следующий запрос:</span><span class="sxs-lookup"><span data-stu-id="152e6-192">For example, consider the following query:</span></span>  
  
```sql
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="152e6-193">Чтобы выполнить проверку на наличие нарушения оптимистического параллелизма при обновлении строки в таблице **Table1**, можно выполнить следующую инструкцию UPDATE:</span><span class="sxs-lookup"><span data-stu-id="152e6-193">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="152e6-194">При условии, что первоначальные значения равны значениям в базе данных, обновление выполняется.</span><span class="sxs-lookup"><span data-stu-id="152e6-194">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="152e6-195">Если же какое-то значение было изменено, то при обновлении изменение строки не происходит, поскольку в предложении WHERE не обнаруживается совпадение.</span><span class="sxs-lookup"><span data-stu-id="152e6-195">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="152e6-196">Обратите внимание, что всегда рекомендуется возвращать уникальное значение первичного ключа в каждом конкретном запросе.</span><span class="sxs-lookup"><span data-stu-id="152e6-196">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="152e6-197">В противном случае в предыдущей инструкции UPDATE может произойти обновление нескольких строк, что может не соответствовать намерениям.</span><span class="sxs-lookup"><span data-stu-id="152e6-197">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="152e6-198">Если столбец в источнике данных допускает значения NULL, то может потребоваться дополнить предложение WHERE для проверки на наличие согласующихся ссылок NULL в локальной таблице и в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="152e6-198">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="152e6-199">Например, в следующей инструкции UPDATE проверяется, что ссылка NULL в локальной строке все еще соответствует ссылке NULL в источнике данных или что значение в локальной строке все еще соответствует значению в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="152e6-199">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="152e6-200">При использовании модели оптимистичного параллелизма можно также выбрать менее строгие критерии.</span><span class="sxs-lookup"><span data-stu-id="152e6-200">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="152e6-201">Например, если в предложении WHERE используются только столбцы первичного ключа, то перезапись данных происходит независимо от того, произошло ли обновление других столбцов со времени выполнения последнего запроса.</span><span class="sxs-lookup"><span data-stu-id="152e6-201">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="152e6-202">Предложение WHERE также можно применять только к конкретным столбцам, в результате чего перезапись данных будет выполняться, только если со времени последнего запроса к определенным полям они не обновлялись.</span><span class="sxs-lookup"><span data-stu-id="152e6-202">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="152e6-203">Событие DataAdapter.RowUpdated</span><span class="sxs-lookup"><span data-stu-id="152e6-203">The DataAdapter.RowUpdated Event</span></span>  

 <span data-ttu-id="152e6-204">Событие **RowUpdated** объекта <xref:System.Data.Common.DataAdapter> может использоваться в сочетании с методами, описанными выше, для передачи приложению уведомлений о конфликтах оптимистического параллелизма.</span><span class="sxs-lookup"><span data-stu-id="152e6-204">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="152e6-205">Событие **RowUpdated** возникает после каждой попытки обновить строку с меткой **Modified** из объекта **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="152e6-205">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="152e6-206">Это позволяет включать в приложение специальный код обработки, в том числе обеспечивающий обработку при возникновении исключений, добавление пользовательских сведений об ошибке, введение программных средств повторного выполнения и т. д.</span><span class="sxs-lookup"><span data-stu-id="152e6-206">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="152e6-207">Объект <xref:System.Data.Common.RowUpdatedEventArgs> возвращает свойство **RecordsAffected**, содержащее количество строк, затронутых конкретной командой обновления для измененной строки в таблице.</span><span class="sxs-lookup"><span data-stu-id="152e6-207">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="152e6-208">Таким образом, если для проверки на наличие конфликтов оптимистического параллелизма применяется команда обновления, свойство **RecordsAffected** возвращает значение 0, если возник конфликт оптимистического параллелизма, поскольку не были обновлены какие-либо записи.</span><span class="sxs-lookup"><span data-stu-id="152e6-208">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="152e6-209">В таком случае вызывается исключение.</span><span class="sxs-lookup"><span data-stu-id="152e6-209">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="152e6-210">Событие **RowUpdated** позволяет обрабатывать такую ситуацию и предотвращать возникновение исключения путем задания соответствующего значения **RowUpdatedEventArgs.Status**, такого как **UpdateStatus.SkipCurrentRow**.</span><span class="sxs-lookup"><span data-stu-id="152e6-210">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="152e6-211">Дополнительные сведения о событии **RowUpdated** см. в разделе [Обработка событий DataAdapter](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="152e6-211">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="152e6-212">При желании можно задать значение **DataAdapter.ContinueUpdateOnError** равным **true** перед вызовом метода **Update** и действовать с учетом данных об ошибке, хранящихся в свойстве **RowError** конкретной строки, после завершения выполнения метода **Update**.</span><span class="sxs-lookup"><span data-stu-id="152e6-212">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="152e6-213">Дополнительные сведения см. в разделе [Сведения об ошибках строк](./dataset-datatable-dataview/row-error-information.md).</span><span class="sxs-lookup"><span data-stu-id="152e6-213">For more information, see [Row Error Information](./dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="152e6-214">Пример оптимистического управления параллелизмом</span><span class="sxs-lookup"><span data-stu-id="152e6-214">Optimistic Concurrency Example</span></span>  

 <span data-ttu-id="152e6-215">Ниже приведен простой пример, в котором для проверки оптимистического параллелизма задается свойство **UpdateCommand** объекта **DataAdapter**, после чего используется событие **RowUpdated** для проверки конфликтов оптимистического параллелизма.</span><span class="sxs-lookup"><span data-stu-id="152e6-215">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="152e6-216">Если обнаруживается конфликт оптимистического параллелизма, то приложение задает значение **RowError** для строки, для которой проводилось обновление, чтобы отразить наличие конфликта оптимистического параллелизма.</span><span class="sxs-lookup"><span data-stu-id="152e6-216">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="152e6-217">Обратите внимание, что значения параметров, передаваемые в предложение WHERE команды UPDATE, соответствуют значениям **Original** в соответствующих столбцах.</span><span class="sxs-lookup"><span data-stu-id="152e6-217">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="152e6-218">См. также</span><span class="sxs-lookup"><span data-stu-id="152e6-218">See also</span></span>

- [<span data-ttu-id="152e6-219">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="152e6-219">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="152e6-220">Обновление источников данных с объектами DataAdapter</span><span class="sxs-lookup"><span data-stu-id="152e6-220">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="152e6-221">Сведения об ошибках строк</span><span class="sxs-lookup"><span data-stu-id="152e6-221">Row Error Information</span></span>](./dataset-datatable-dataview/row-error-information.md)
- [<span data-ttu-id="152e6-222">Транзакции и параллелизм</span><span class="sxs-lookup"><span data-stu-id="152e6-222">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="152e6-223">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="152e6-223">ADO.NET Overview</span></span>](ado-net-overview.md)
