---
description: 'Дополнительные сведения: Навигация по таблицам DataTable'
title: Навигация по таблицам данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 0564af241adc082ef1b736f2e4a561328fbcc976
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651786"
---
# <a name="navigating-datatables"></a><span data-ttu-id="3d1bd-103">Навигация по таблицам данных</span><span class="sxs-lookup"><span data-stu-id="3d1bd-103">Navigating DataTables</span></span>

<span data-ttu-id="3d1bd-104">Объект <xref:System.Data.DataTableReader> получает содержимое одного или нескольких объектов <xref:System.Data.DataTable> в виде одного или нескольких однопроходных результирующих наборов, доступных только для чтения.</span><span class="sxs-lookup"><span data-stu-id="3d1bd-104">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="3d1bd-105">Объект <xref:System.Data.DataTableReader> может содержать несколько результирующих наборов, если он создан методом <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d1bd-105">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="3d1bd-106">Если имеется несколько результирующих наборов, метод <xref:System.Data.DataTableReader.NextResult%2A> продвигает курсор к следующему результирующему набору.</span><span class="sxs-lookup"><span data-stu-id="3d1bd-106">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="3d1bd-107">Это однопроходной процесс.</span><span class="sxs-lookup"><span data-stu-id="3d1bd-107">This is a forward-only process.</span></span> <span data-ttu-id="3d1bd-108">Вернуться к предыдущему результирующему набору невозможно.</span><span class="sxs-lookup"><span data-stu-id="3d1bd-108">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d1bd-109">Пример</span><span class="sxs-lookup"><span data-stu-id="3d1bd-109">Example</span></span>  

 <span data-ttu-id="3d1bd-110">В следующем примере `TestConstructor` метод создает два <xref:System.Data.DataTable> экземпляра.</span><span class="sxs-lookup"><span data-stu-id="3d1bd-110">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="3d1bd-111">Чтобы продемонстрировать этот конструктор для <xref:System.Data.DataTableReader> класса, в примере создается новый **DataTableReader** на основе массива, содержащего два **объекта DataTables**, и выполняется простая операция печати содержимого из первых нескольких столбцов в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="3d1bd-111">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3d1bd-112">См. также</span><span class="sxs-lookup"><span data-stu-id="3d1bd-112">See also</span></span>

- [<span data-ttu-id="3d1bd-113">Объекты DataTableReader</span><span class="sxs-lookup"><span data-stu-id="3d1bd-113">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="3d1bd-114">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3d1bd-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
