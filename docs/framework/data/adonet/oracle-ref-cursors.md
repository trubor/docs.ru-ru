---
description: Дополнительные сведения о КУРСОРах Oracle REF
title: REF CURSOR в Oracle
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 0a9c5e95a9f0d2da74fd6a3db19f15699a3e2787
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672456"
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="7b5a0-103">REF CURSOR в Oracle</span><span class="sxs-lookup"><span data-stu-id="7b5a0-103">Oracle REF CURSORs</span></span>

<span data-ttu-id="7b5a0-104">Поставщик данных платформа .NET Framework для Oracle поддерживает тип данных Oracle **ref Cursor** .</span><span class="sxs-lookup"><span data-stu-id="7b5a0-104">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="7b5a0-105">При использовании поставщика данных для работы с данными типа REF CURSOR Oracle необходимо учитывать следующие особенности его функционирования.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-105">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b5a0-106">По некоторым особенностям функционирования он отличается от поставщика Microsoft OLE DB для Oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="7b5a0-106">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
- <span data-ttu-id="7b5a0-107">По соображениям производительности поставщик данных для Oracle не привязывает типы данных **ссылочных курсоров** автоматически, как если бы они явно не заданы.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-107">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
- <span data-ttu-id="7b5a0-108">Указанный поставщик данных не поддерживает никаких escape-последовательностей ODBC, включая escape-последовательность {resultset}, используемую для задания параметров REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-108">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
- <span data-ttu-id="7b5a0-109">Для выполнения хранимой процедуры, возвращающей ссылки REF CURSOR, необходимо определить параметры в <xref:System.Data.OracleClient.OracleParameterCollection> с помощью <xref:System.Data.OracleClient.OracleType> **курсора** и <xref:System.Data.OracleClient.OracleParameter.Direction%2A> **выходных данных**.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-109">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="7b5a0-110">Этот поставщик данных поддерживает привязку данных типа REF CURSOR только в качестве выходных параметров.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-110">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="7b5a0-111">Этот поставщик не поддерживает данные типа REF CURSOR как входные параметры.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-111">The provider does not support REF CURSORs as input parameters.</span></span>  
  
- <span data-ttu-id="7b5a0-112">Получение модуля <xref:System.Data.OracleClient.OracleDataReader> из значения параметра не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-112">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="7b5a0-113">Значения имеют тип <xref:System.DBNull> после выполнения команды.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-113">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
- <span data-ttu-id="7b5a0-114">Единственным значением перечисления **CommandBehavior** , которое работает с КЛЮЧЕВЫМи курсорами (например, при вызове <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> ), является **клосеконнектион**; все остальные игнорируются.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-114">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
- <span data-ttu-id="7b5a0-115">Порядок ССЫЛОЧных КУРСОРов в **OracleDataReader** зависит от порядка параметров в **OracleParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-115">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="7b5a0-116">Свойство <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> не учитывается.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-116">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
- <span data-ttu-id="7b5a0-117">**Табличный** тип данных PL/SQL не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-117">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="7b5a0-118">Но данные типа REF CURSOR являются более эффективными.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-118">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="7b5a0-119">Если необходимо использовать **табличный** тип данных, используйте поставщик данных OLE DB .NET с MSDAORA.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-119">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b5a0-120">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="7b5a0-120">In This Section</span></span>  

 [<span data-ttu-id="7b5a0-121">Примеры REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="7b5a0-121">REF CURSOR Examples</span></span>](ref-cursor-examples.md)  
 <span data-ttu-id="7b5a0-122">Содержит три примера, которые демонстрируют использование данных типа REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-122">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="7b5a0-123">Параметры REF CURSOR в объекте OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="7b5a0-123">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="7b5a0-124">Демонстрирует выполнение хранимой процедуры PL/SQL, возвращающей параметр REF CURSOR, и считывание значения в виде **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-124">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="7b5a0-125">Извлечение данных нескольких REF CURSOR с использованием OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="7b5a0-125">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="7b5a0-126">Демонстрирует выполнение хранимой процедуры PL/SQL, возвращающей два параметра REF CURSOR, и считывание значений с помощью **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-126">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="7b5a0-127">Заполнение набора данных с помощью одного или нескольких параметров REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="7b5a0-127">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="7b5a0-128">Показывает, как выполнить хранимую процедуру PL/SQL, которая возвращает два параметра REF CURSOR и заполняет <xref:System.Data.DataSet> возвращаемыми строками.</span><span class="sxs-lookup"><span data-stu-id="7b5a0-128">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b5a0-129">См. также</span><span class="sxs-lookup"><span data-stu-id="7b5a0-129">See also</span></span>

- [<span data-ttu-id="7b5a0-130">Oracle и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7b5a0-130">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="7b5a0-131">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7b5a0-131">ADO.NET Overview</span></span>](ado-net-overview.md)
