---
description: 'Дополнительные сведения: внесение и отправка изменений данных'
title: Внесение и отправка изменений данных
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 260dab911057b45250d44ded7c254dd903e2aed7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695578"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="b91bd-103">Внесение и отправка изменений данных</span><span class="sxs-lookup"><span data-stu-id="b91bd-103">Making and Submitting Data Changes</span></span>

<span data-ttu-id="b91bd-104">В подразделах данного раздела описывается, как выполнять изменения и передавать их в базу данных, а также обрабатывать конфликты оптимистического параллелизма.</span><span class="sxs-lookup"><span data-stu-id="b91bd-104">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>

> [!NOTE]
> <span data-ttu-id="b91bd-105">Можно переопределить методы [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], используемые по умолчанию для операций `Insert`, `Update` и `Delete` базы данных.</span><span class="sxs-lookup"><span data-stu-id="b91bd-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="b91bd-106">Дополнительные сведения см. в разделе [Настройка операций вставки, обновления и удаления](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b91bd-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="b91bd-107">Разработчики, использующие Visual Studio, могут использовать реляционный конструктор объектов для разработки хранимых процедур для той же цели.</span><span class="sxs-lookup"><span data-stu-id="b91bd-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b91bd-108">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="b91bd-108">In This Section</span></span>

<span data-ttu-id="b91bd-109">[Инструкции. Вставка строк в базу данных](how-to-insert-rows-into-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="b91bd-109">[How to: Insert Rows Into the Database](how-to-insert-rows-into-the-database.md) </span></span>\
<span data-ttu-id="b91bd-110">Описывает, как вставлять строки в базу данных путем добавления объектов в модель объектов.</span><span class="sxs-lookup"><span data-stu-id="b91bd-110">Describes how to insert rows in the database by adding objects to the object model.</span></span>

<span data-ttu-id="b91bd-111">[Как обновлять строки в базе данных](how-to-update-rows-in-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="b91bd-111">[How to: Update Rows in the Database](how-to-update-rows-in-the-database.md) </span></span>\
<span data-ttu-id="b91bd-112">Описывается, как обновлять строки в базе данных путем обновления объектов в объектной модели.</span><span class="sxs-lookup"><span data-stu-id="b91bd-112">Describes how to update rows in the database by updating objects in the object model.</span></span>

<span data-ttu-id="b91bd-113">[Как удалить строки из базы данных](how-to-delete-rows-from-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="b91bd-113">[How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md) </span></span>\
<span data-ttu-id="b91bd-114">Описывается, как удалять строки из базы данных путем удаления объектов из объектной модели.</span><span class="sxs-lookup"><span data-stu-id="b91bd-114">Describes how to delete rows in the database by deleting objects in the object model.</span></span>

<span data-ttu-id="b91bd-115">[Как отправлять изменения в базу данных](how-to-submit-changes-to-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="b91bd-115">[How to: Submit Changes to the Database](how-to-submit-changes-to-the-database.md) </span></span>\
<span data-ttu-id="b91bd-116">Описывается, как отправлять изменения объектной модели в базу данных.</span><span class="sxs-lookup"><span data-stu-id="b91bd-116">Describes how to send object-model changes to the database.</span></span>

<span data-ttu-id="b91bd-117">[Как использовать скобки для отправки данных с помощью транзакций](how-to-bracket-data-submissions-by-using-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="b91bd-117">[How to: Bracket Data Submissions by Using Transactions](how-to-bracket-data-submissions-by-using-transactions.md) </span></span>\
<span data-ttu-id="b91bd-118">Описывается, как включать операции в транзакцию.</span><span class="sxs-lookup"><span data-stu-id="b91bd-118">Describes how to include operations in a transaction.</span></span>

<span data-ttu-id="b91bd-119">[Руководство. динамическое создание базы данных](how-to-dynamically-create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="b91bd-119">[How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md) </span></span>\
<span data-ttu-id="b91bd-120">Описывается динамическое создание баз данных и типичные сценарии использования этого метода.</span><span class="sxs-lookup"><span data-stu-id="b91bd-120">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>

<span data-ttu-id="b91bd-121">[Руководство. Управление конфликтами изменений](how-to-manage-change-conflicts.md) </span><span class="sxs-lookup"><span data-stu-id="b91bd-121">[How to: Manage Change Conflicts](how-to-manage-change-conflicts.md) </span></span>\
<span data-ttu-id="b91bd-122">Описываются методы устранения проблем оптимистического параллелизма.</span><span class="sxs-lookup"><span data-stu-id="b91bd-122">Describes techniques for addressing optimistic concurrency issues.</span></span>
