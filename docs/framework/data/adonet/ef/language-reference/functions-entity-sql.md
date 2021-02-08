---
description: 'Дополнительные сведения: функции (Entity SQL)'
title: Функции (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: c557d264587a1d40194971d756e6b5c75a3856aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786307"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="68609-103">Функции (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="68609-103">Functions (Entity SQL)</span></span>

<span data-ttu-id="68609-104">Язык Entity SQL поддерживает определяемые пользователем функции и функции поставщиков.</span><span class="sxs-lookup"><span data-stu-id="68609-104">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="68609-105">Определяемые пользователем функции определяются в концептуальной модели либо внутри запроса.</span><span class="sxs-lookup"><span data-stu-id="68609-105">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="68609-106">Дополнительные сведения см. в разделе [определяемые пользователем функции](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="68609-106">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="68609-107">Канонические функции встроены в платформу Entity Framework и должны поддерживаться поставщиками данных.</span><span class="sxs-lookup"><span data-stu-id="68609-107">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="68609-108">Команды Entity SQL завершатся ошибкой, если пользователь вызывает функции, которые не поддерживаются поставщиком данных.</span><span class="sxs-lookup"><span data-stu-id="68609-108">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="68609-109">Поэтому, как правило, рекомендуется использовать канонические функции, а не функции, зависящие от хранилища и находящиеся в пространстве имен поставщика данных.</span><span class="sxs-lookup"><span data-stu-id="68609-109">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="68609-110">Дополнительные сведения см. в разделе [канонические функции](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="68609-110">For more information, see [Canonical Functions](canonical-functions.md).</span></span>  
  
 <span data-ttu-id="68609-111">Управляемый поставщик клиента Microsoft SQL предоставляет набор функций для поставщика.</span><span class="sxs-lookup"><span data-stu-id="68609-111">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="68609-112">Дополнительные сведения см. в разделе [SqlClient для функций Entity Framework](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="68609-112">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="68609-113">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="68609-113">In This Section</span></span>  

 [<span data-ttu-id="68609-114">Определяемые пользователем функции</span><span class="sxs-lookup"><span data-stu-id="68609-114">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="68609-115">Разрешение перегрузки функций</span><span class="sxs-lookup"><span data-stu-id="68609-115">Function Overload Resolution</span></span>](function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="68609-116">Агрегатные функции</span><span class="sxs-lookup"><span data-stu-id="68609-116">Aggregate Functions</span></span>](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="68609-117">См. также</span><span class="sxs-lookup"><span data-stu-id="68609-117">See also</span></span>

- [<span data-ttu-id="68609-118">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="68609-118">Entity SQL Overview</span></span>](entity-sql-overview.md)
