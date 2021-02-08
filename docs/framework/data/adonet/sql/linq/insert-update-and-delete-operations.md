---
description: 'Дополнительные сведения: операции вставки, обновления и удаления'
title: Операции вставки, обновления и удаления
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 2d0470ed6abe654ca08f954c3de97de207adb75d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803822"
---
# <a name="insert-update-and-delete-operations"></a><span data-ttu-id="7e7a2-103">Операции вставки, обновления и удаления</span><span class="sxs-lookup"><span data-stu-id="7e7a2-103">Insert, Update, and Delete Operations</span></span>

<span data-ttu-id="7e7a2-104">В `Insert` операции `Update`, `Delete` и [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] выполняются путем добавления, изменения и удаления объектов в объектной модели.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-104">You perform `Insert`, `Update`, and `Delete` operations in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] by adding, changing, and removing objects in your object model.</span></span> <span data-ttu-id="7e7a2-105">По умолчанию [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] преобразует действия в язык SQL и отправляет изменения в базу данных.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-105">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your actions to SQL and submits the changes to the database.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7e7a2-106">обеспечивает максимальную гибкость при манипуляции и сохранении изменений, внесенных в объекты.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-106">offers maximum flexibility in manipulating and persisting changes that you made to your objects.</span></span> <span data-ttu-id="7e7a2-107">Как только будут доступны объекты сущности (либо при извлечении их с помощью запроса, либо при создании заново), их можно изменить как обычные объекты в приложении.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-107">As soon as entity objects are available (either by retrieving them through a query or by constructing them anew), you can change them as typical objects in your application.</span></span> <span data-ttu-id="7e7a2-108">Это означает, что можно изменить их значения, добавить в коллекцию или удалить из нее.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-108">That is, you can change their values, you can add them to your collections, and you can remove them from your collections.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7e7a2-109">отслеживает изменения и готов отправить их обратно в базу данных, когда будет вызван метод <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-109">tracks your changes and is ready to transmit them back to the database when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span>

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7e7a2-110">не поддерживает или не распознает операции каскадного удаления.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-110">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="7e7a2-111">Если необходимо удалить строку в таблице с ограничениями, необходимо либо задать `ON DELETE CASCADE` правило в ограничении внешнего ключа в базе данных, либо использовать собственный код, чтобы сначала удалить дочерние объекты, препятствующие удалению родительского объекта.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-111">If you want to delete a row in a table that has constraints against it, you must either set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database, or use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span> <span data-ttu-id="7e7a2-112">В противном случае создается исключение.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-112">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="7e7a2-113">Дополнительные сведения см. в разделе [инструкции. Удаление строк из базы данных](how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="7e7a2-113">For more information, see [How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md).</span></span>

<span data-ttu-id="7e7a2-114">В следующих фрагментах используются классы `Customer` и `Order` из образца базы данных "Борей".</span><span class="sxs-lookup"><span data-stu-id="7e7a2-114">The following excerpts use the `Customer` and `Order` classes from the Northwind sample database.</span></span> <span data-ttu-id="7e7a2-115">Для краткости определения классов не показаны.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-115">Class definitions are not shown for brevity.</span></span>

[!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
[!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]

<span data-ttu-id="7e7a2-116">При вызове метода <xref:System.Data.Linq.DataContext.SubmitChanges%2A>[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] автоматически создает и выполняет команды SQL, необходимые для передачи изменений обратно в базу данных.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-116">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatically generates and executes the SQL commands that it must have to transmit your changes back to the database.</span></span>

> [!NOTE]
> <span data-ttu-id="7e7a2-117">Это поведение можно переопределить использованием собственной настраиваемой логики, обычно за счет хранимой процедуры.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-117">You can override this behavior by using your own custom logic, typically by way of a stored procedure.</span></span> <span data-ttu-id="7e7a2-118">Дополнительные сведения см. [в разделе обязанности разработчика при переопределении поведения по умолчанию](responsibilities-of-the-developer-in-overriding-default-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="7e7a2-118">For more information, see [Responsibilities of the Developer In Overriding Default Behavior](responsibilities-of-the-developer-in-overriding-default-behavior.md).</span></span>
>
> <span data-ttu-id="7e7a2-119">Разработчики, использующие Visual Studio, могут использовать реляционный конструктор объектов для разработки хранимых процедур для этой цели.</span><span class="sxs-lookup"><span data-stu-id="7e7a2-119">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for this purpose.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e7a2-120">См. также</span><span class="sxs-lookup"><span data-stu-id="7e7a2-120">See also</span></span>

- [<span data-ttu-id="7e7a2-121">Загрузка примеров баз данных</span><span class="sxs-lookup"><span data-stu-id="7e7a2-121">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="7e7a2-122">Настройка операций вставки, обновления и удаления</span><span class="sxs-lookup"><span data-stu-id="7e7a2-122">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
