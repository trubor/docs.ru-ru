---
description: 'Дополнительные сведения: SQL Server двоичные данные и Large-Value данных'
title: Двоичные данные и данные большого объема SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 8c7da5d504af0bc1beeea7e210a6fff4157fb090
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767444"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="4d856-103">Двоичные данные и данные большого объема SQL Server</span><span class="sxs-lookup"><span data-stu-id="4d856-103">SQL Server Binary and Large-Value Data</span></span>

<span data-ttu-id="4d856-104">SQL Server предоставляет описатель `max`, который расширяет возможности хранения для типов данных `varchar`, `nvarchar` и `varbinary`.</span><span class="sxs-lookup"><span data-stu-id="4d856-104">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="4d856-105">Типы данных `varchar(max)`, `nvarchar(max)` и `varbinary(max)` называются *типами данных большого размера*.</span><span class="sxs-lookup"><span data-stu-id="4d856-105">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="4d856-106">Можно использовать типы данных больших значений для хранения 2^31–1 байт данных.</span><span class="sxs-lookup"><span data-stu-id="4d856-106">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="4d856-107">В SQL Server 2008 добавлен элемент FILESTREAM. Это не тип данных, а определяемый на уровне столбца атрибут, позволяющий хранить данные большого размера в файловой системе, а не в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4d856-107">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4d856-108">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="4d856-108">In This Section</span></span>  

 [<span data-ttu-id="4d856-109">Изменение данных Large-Value (max) в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4d856-109">Modifying Large-Value (max) Data in ADO.NET</span></span>](modifying-large-value-max-data.md)  
 <span data-ttu-id="4d856-110">Описание работы с типами данных больших значений.</span><span class="sxs-lookup"><span data-stu-id="4d856-110">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="4d856-111">Данные FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="4d856-111">FILESTREAM Data</span></span>](filestream-data.md)  
 <span data-ttu-id="4d856-112">Описывает, как работать в SQL Server 2008 с данными большого объема, для которых указан атрибут FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="4d856-112">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d856-113">См. также</span><span class="sxs-lookup"><span data-stu-id="4d856-113">See also</span></span>

- [<span data-ttu-id="4d856-114">Типы данных SQL Server и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4d856-114">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="4d856-115">SQL Serverные операции с данными в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4d856-115">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="4d856-116">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4d856-116">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="4d856-117">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4d856-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
