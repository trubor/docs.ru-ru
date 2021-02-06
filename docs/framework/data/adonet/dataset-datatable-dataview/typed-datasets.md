---
description: 'Дополнительные сведения: типизированные наборы данных'
title: Типизированные наборы данных
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 698efbe52e960afe00ca337445df919545d8437e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651500"
---
# <a name="typed-datasets"></a><span data-ttu-id="d7c70-103">Типизированные наборы данных</span><span class="sxs-lookup"><span data-stu-id="d7c70-103">Typed DataSets</span></span>

<span data-ttu-id="d7c70-104">Наряду с доступом к значениям с поздним связыванием через слабо типизированные переменные, в объекте <xref:System.Data.DataSet> предоставляется доступ к данным на основе принципа строгой типизации.</span><span class="sxs-lookup"><span data-stu-id="d7c70-104">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="d7c70-105">Доступ к таблицам и столбцам, которые являются частью **набора данных** , можно получить с помощью понятных имен и строго типизированных переменных.</span><span class="sxs-lookup"><span data-stu-id="d7c70-105">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="d7c70-106">Типизированный **набор данных** — это класс, производный от **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="d7c70-106">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="d7c70-107">Таким образом, он наследует все методы, события и свойства **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="d7c70-107">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="d7c70-108">Кроме того, типизированный **набор данных** предоставляет строго типизированные методы, события и свойства.</span><span class="sxs-lookup"><span data-stu-id="d7c70-108">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="d7c70-109">Это означает, что к таблицам и столбцам можно обращаться путем указания имен вместо использования методов на основе коллекций.</span><span class="sxs-lookup"><span data-stu-id="d7c70-109">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="d7c70-110">Помимо улучшенной удобочитаемости кода, типизированный **набор данных** также позволяет редактору кода Visual Studio .NET автоматически завершать строки по мере ввода.</span><span class="sxs-lookup"><span data-stu-id="d7c70-110">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="d7c70-111">Кроме того, строго типизированный **набор данных** предоставляет доступ к значениям в качестве правильного типа во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="d7c70-111">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="d7c70-112">При использовании строго типизированного **набора данных** ошибки несоответствия типов перехватываются при компиляции кода, а не во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d7c70-112">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7c70-113">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="d7c70-113">In This Section</span></span>  

 [<span data-ttu-id="d7c70-114">Создание строго типизированных наборов данных</span><span class="sxs-lookup"><span data-stu-id="d7c70-114">Generating Strongly Typed DataSets</span></span>](generating-strongly-typed-datasets.md)  
 <span data-ttu-id="d7c70-115">Описывает создание и использование строго типизированного **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="d7c70-115">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="d7c70-116">Создание примечаний к типизированным наборам данных</span><span class="sxs-lookup"><span data-stu-id="d7c70-116">Annotating Typed DataSets</span></span>](annotating-typed-datasets.md)  
 <span data-ttu-id="d7c70-117">Описывает, как закомментировать схему XSD, используемую для создания строго типизированного **набора данных**, чтобы предоставить понятные имена элементам **набора данных** без изменения базовой схемы.</span><span class="sxs-lookup"><span data-stu-id="d7c70-117">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c70-118">См. также</span><span class="sxs-lookup"><span data-stu-id="d7c70-118">See also</span></span>

- [<span data-ttu-id="d7c70-119">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="d7c70-119">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="d7c70-120">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d7c70-120">ADO.NET Overview</span></span>](../ado-net-overview.md)
