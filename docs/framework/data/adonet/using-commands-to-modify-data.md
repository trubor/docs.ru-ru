---
description: 'Дополнительные сведения: использование команд для изменения данных'
title: Использование команд для изменения данных
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 3addcb93850aa8e26fe441b5c859502779433bfb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766560"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="7c716-103">Использование команд для изменения данных</span><span class="sxs-lookup"><span data-stu-id="7c716-103">Using Commands to Modify Data</span></span>

<span data-ttu-id="7c716-104">Используя поставщик данных .NET Framework, можно выполнять хранимые процедуры или инструкции языка описания данных DDL (например, CREATE TABLE и ALTER COLUMN) для выполнения операций со схемой в базе данных или в каталоге.</span><span class="sxs-lookup"><span data-stu-id="7c716-104">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="7c716-105">Эти команды не возвращают строки в виде запроса, поэтому объект **Command** предоставляет **ExecuteNonQuery** для их обработки.</span><span class="sxs-lookup"><span data-stu-id="7c716-105">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="7c716-106">Помимо использования **ExecuteNonQuery** для изменения схемы, этот метод можно также использовать для обработки инструкций SQL (например, INSERT, UPDATE и DELETE), которые изменяют данные, но не возвращают строки.</span><span class="sxs-lookup"><span data-stu-id="7c716-106">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="7c716-107">Хотя метод **ExecuteNonQuery** не возвращает строки, входные и выходные параметры, а также возвращаемые значения могут передаваться и возвращаться через коллекцию **Parameters** объекта **Command**.</span><span class="sxs-lookup"><span data-stu-id="7c716-107">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c716-108">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="7c716-108">In This Section</span></span>  

 [<span data-ttu-id="7c716-109">Обновление данных в источнике данных</span><span class="sxs-lookup"><span data-stu-id="7c716-109">Updating Data in a Data Source</span></span>](updating-data-in-a-data-source.md)  
 <span data-ttu-id="7c716-110">Описывает выполнение команд или хранимых процедур, которые изменяют данные в базе данных.</span><span class="sxs-lookup"><span data-stu-id="7c716-110">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="7c716-111">Выполнение операций с каталогами</span><span class="sxs-lookup"><span data-stu-id="7c716-111">Performing Catalog Operations</span></span>](performing-catalog-operations.md)  
 <span data-ttu-id="7c716-112">Описывает выполнение команд, которые изменяют схему базы данных.</span><span class="sxs-lookup"><span data-stu-id="7c716-112">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c716-113">См. также</span><span class="sxs-lookup"><span data-stu-id="7c716-113">See also</span></span>

- [<span data-ttu-id="7c716-114">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7c716-114">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="7c716-115">Команды и параметры</span><span class="sxs-lookup"><span data-stu-id="7c716-115">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="7c716-116">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7c716-116">ADO.NET Overview</span></span>](ado-net-overview.md)
