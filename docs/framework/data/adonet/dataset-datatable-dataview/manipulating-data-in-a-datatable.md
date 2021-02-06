---
description: 'Дополнительные сведения: Управление данными в DataTable'
title: Управление данными в таблице данных
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: 41f70bd15a023f8d92733bdce142666a08245d9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652072"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="7999c-103">Управление данными в таблице данных</span><span class="sxs-lookup"><span data-stu-id="7999c-103">Manipulating Data in a DataTable</span></span>

<span data-ttu-id="7999c-104">После создания объекта <xref:System.Data.DataTable> в объекте <xref:System.Data.DataSet> можно выполнять такие же действия, как и при использовании таблицы в базе данных.</span><span class="sxs-lookup"><span data-stu-id="7999c-104">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="7999c-105">Можно добавлять, просматривать, изменять и удалять данные в таблице. Можно отслеживать ошибки и события; кроме того, можно запрашивать находящиеся в таблице данные.</span><span class="sxs-lookup"><span data-stu-id="7999c-105">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="7999c-106">При изменении данных в **DataTable** можно также проверить, являются ли изменения точными, и определить, следует ли программно принимать или отклонять эти изменения.</span><span class="sxs-lookup"><span data-stu-id="7999c-106">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7999c-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="7999c-107">In This Section</span></span>  

 [<span data-ttu-id="7999c-108">Добавление данных в таблицу данных</span><span class="sxs-lookup"><span data-stu-id="7999c-108">Adding Data to a DataTable</span></span>](adding-data-to-a-datatable.md)  
 <span data-ttu-id="7999c-109">Рассказывает, как создавать новые строки и добавлять их в таблицу.</span><span class="sxs-lookup"><span data-stu-id="7999c-109">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="7999c-110">Просмотр данных в таблице данных</span><span class="sxs-lookup"><span data-stu-id="7999c-110">Viewing Data in a DataTable</span></span>](viewing-data-in-a-datatable.md)  
 <span data-ttu-id="7999c-111">Описывает, как получать доступ к данным в строке, включая исходную и текущую версии данных.</span><span class="sxs-lookup"><span data-stu-id="7999c-111">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="7999c-112">Метод Load</span><span class="sxs-lookup"><span data-stu-id="7999c-112">The Load Method</span></span>](the-load-method.md)  
 <span data-ttu-id="7999c-113">Описывает использование метода **Load** для заполнения **таблицы DataTable** строками.</span><span class="sxs-lookup"><span data-stu-id="7999c-113">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="7999c-114">Редактирование таблиц данных</span><span class="sxs-lookup"><span data-stu-id="7999c-114">DataTable Edits</span></span>](datatable-edits.md)  
 <span data-ttu-id="7999c-115">Рассказывает, как изменять данные в строке, в том числе приостанавливать внесение изменений в строку, пока предложенные изменения не будут проверены и приняты.</span><span class="sxs-lookup"><span data-stu-id="7999c-115">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="7999c-116">Состояния и версии строк</span><span class="sxs-lookup"><span data-stu-id="7999c-116">Row States and Row Versions</span></span>](row-states-and-row-versions.md)  
 <span data-ttu-id="7999c-117">Приводит сведения о разных состояниях строки.</span><span class="sxs-lookup"><span data-stu-id="7999c-117">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="7999c-118">Удаление DataRow</span><span class="sxs-lookup"><span data-stu-id="7999c-118">DataRow Deletion</span></span>](datarow-deletion.md)  
 <span data-ttu-id="7999c-119">Описывает, как удалять строку из таблицы.</span><span class="sxs-lookup"><span data-stu-id="7999c-119">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="7999c-120">Сведения об ошибках строк</span><span class="sxs-lookup"><span data-stu-id="7999c-120">Row Error Information</span></span>](row-error-information.md)  
 <span data-ttu-id="7999c-121">Объясняет, как вставлять сведения об ошибках по одной строке, чтобы способствовать разрешению проблем с данными в приложении.</span><span class="sxs-lookup"><span data-stu-id="7999c-121">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="7999c-122">AcceptChanges и RejectChanges</span><span class="sxs-lookup"><span data-stu-id="7999c-122">AcceptChanges and RejectChanges</span></span>](acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="7999c-123">Объясняет, как принимать или отклонять внесенные в строку изменения.</span><span class="sxs-lookup"><span data-stu-id="7999c-123">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7999c-124">См. также</span><span class="sxs-lookup"><span data-stu-id="7999c-124">See also</span></span>

- [<span data-ttu-id="7999c-125">DataTables</span><span class="sxs-lookup"><span data-stu-id="7999c-125">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="7999c-126">Обработка событий таблиц данных</span><span class="sxs-lookup"><span data-stu-id="7999c-126">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="7999c-127">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7999c-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
