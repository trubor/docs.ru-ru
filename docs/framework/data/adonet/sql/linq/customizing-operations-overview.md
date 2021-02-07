---
description: 'Дополнительные сведения: Настройка операций: обзор'
title: 'Настройка операций: Обзор'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: bdcaf482f49b9c55fb7a1834b19b683ac2fa16bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729605"
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="ce58c-103">Настройка операций: Обзор</span><span class="sxs-lookup"><span data-stu-id="ce58c-103">Customizing Operations: Overview</span></span>

<span data-ttu-id="ce58c-104">По умолчанию [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] создает динамический код SQL для операций вставки, обновления и удаления на основе сопоставления.</span><span class="sxs-lookup"><span data-stu-id="ce58c-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="ce58c-105">Однако на практике часто приходится добавлять собственную бизнес-логику для обеспечения безопасности, выполнения проверок и т. д.</span><span class="sxs-lookup"><span data-stu-id="ce58c-105">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ce58c-106">Ниже приведены методы настройки этих операций.</span><span class="sxs-lookup"><span data-stu-id="ce58c-106">techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="ce58c-107">Возможности загрузки</span><span class="sxs-lookup"><span data-stu-id="ce58c-107">Loading Options</span></span>  

 <span data-ttu-id="ce58c-108">В запросах можно определять, какой объем данных, связанных с основными целевыми объектами, должен извлекаться при подключении к базе данных.</span><span class="sxs-lookup"><span data-stu-id="ce58c-108">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="ce58c-109">Эта функциональная возможность реализуется, в первую очередь, посредством использования параметров <xref:System.Data.Linq.DataLoadOptions>.</span><span class="sxs-lookup"><span data-stu-id="ce58c-109">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="ce58c-110">Дополнительные сведения см. в разделе [Отложенная и немедленная загрузка](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="ce58c-110">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="ce58c-111">Разделяемые методы</span><span class="sxs-lookup"><span data-stu-id="ce58c-111">Partial Methods</span></span>  

 <span data-ttu-id="ce58c-112">При использовании сопоставления по умолчанию технология [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] предоставляет разделяемые методы, которые можно использовать для реализации пользовательской бизнес-логики.</span><span class="sxs-lookup"><span data-stu-id="ce58c-112">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="ce58c-113">Дополнительные сведения см. в разделе [Добавление бизнес-логики с помощью разделяемых методов](adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ce58c-113">For more information, see [Adding Business Logic By Using Partial Methods](adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="ce58c-114">Хранимые процедуры и пользовательские функции</span><span class="sxs-lookup"><span data-stu-id="ce58c-114">Stored Procedures and User-Defined Functions</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ce58c-115">поддерживает использование хранимых процедур и определяемых пользователем функций.</span><span class="sxs-lookup"><span data-stu-id="ce58c-115">supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="ce58c-116">Хранимые процедуры часто используются для настройки операций.</span><span class="sxs-lookup"><span data-stu-id="ce58c-116">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="ce58c-117">Дополнительные сведения см. в разделе [Хранимые процедуры](stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ce58c-117">For more information, see [Stored Procedures](stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce58c-118">См. также</span><span class="sxs-lookup"><span data-stu-id="ce58c-118">See also</span></span>

- [<span data-ttu-id="ce58c-119">Настройка операций вставки, обновления и удаления</span><span class="sxs-lookup"><span data-stu-id="ce58c-119">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
