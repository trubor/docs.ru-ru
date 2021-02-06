---
description: 'Дополнительные сведения о: Дататаблереадерс'
title: Объекты DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: b3e85ae05c07af18fe6219602b5b40f50a9fbc8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652605"
---
# <a name="datatablereaders"></a><span data-ttu-id="c82db-103">Объекты DataTableReader</span><span class="sxs-lookup"><span data-stu-id="c82db-103">DataTableReaders</span></span>

<span data-ttu-id="c82db-104"><xref:System.Data.DataTableReader> представляет содержимое объекта <xref:System.Data.DataTable> или <xref:System.Data.DataSet> в виде одного или нескольких результирующих наборов, предназначенных только для чтения и только для перенаправления.</span><span class="sxs-lookup"><span data-stu-id="c82db-104">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="c82db-105">При создании объекта **DataTableReader** из **таблицы** данных результирующий объект **DataTableReader** содержит один результирующий набор с теми же данными, что и **таблица DataTable** , из которой он был создан, за исключением строк, которые были помечены как удаленные.</span><span class="sxs-lookup"><span data-stu-id="c82db-105">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="c82db-106">Столбцы отображаются в том же порядке, что и в исходной **таблице** данных.</span><span class="sxs-lookup"><span data-stu-id="c82db-106">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="c82db-107">Объект **DataTableReader** может содержать несколько результирующих наборов, если он был создан путем вызова метода <xref:System.Data.DataSet.CreateDataReader%2A> .</span><span class="sxs-lookup"><span data-stu-id="c82db-107">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="c82db-108">Результаты находятся в том же порядке, что и **DataTables** в коллекции объекта **DataSet** <xref:System.Data.DataSet.Tables%2A> .</span><span class="sxs-lookup"><span data-stu-id="c82db-108">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c82db-109">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="c82db-109">In This Section</span></span>  

 [<span data-ttu-id="c82db-110">Создание объекта DataReader</span><span class="sxs-lookup"><span data-stu-id="c82db-110">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="c82db-111">Описывает, как создать объект **DataTableReader** .</span><span class="sxs-lookup"><span data-stu-id="c82db-111">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="c82db-112">Навигация по таблицам данных</span><span class="sxs-lookup"><span data-stu-id="c82db-112">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="c82db-113">Описывает использование метода **Read** для перемещения по содержимому объекта **DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="c82db-113">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c82db-114">См. также</span><span class="sxs-lookup"><span data-stu-id="c82db-114">See also</span></span>

- [<span data-ttu-id="c82db-115">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c82db-115">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="c82db-116">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c82db-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
