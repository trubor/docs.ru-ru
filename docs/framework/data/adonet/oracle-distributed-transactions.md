---
description: 'Подробнее: распределенные транзакции Oracle'
title: Распределенные транзакции Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: d0c41920f18e0f56ebdf57e3cb82cf829a59c450
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786177"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="d19b6-103">Распределенные транзакции Oracle</span><span class="sxs-lookup"><span data-stu-id="d19b6-103">Oracle Distributed Transactions</span></span>

<span data-ttu-id="d19b6-104">Объект <xref:System.Data.OracleClient.OracleConnection> автоматически прикрепляется к существующей распределенной транзакции, если он определяет, что транзакция активна.</span><span class="sxs-lookup"><span data-stu-id="d19b6-104">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="d19b6-105">Автоматическое прикрепление к транзакции происходит при открытии соединения или его получении из пула соединений.</span><span class="sxs-lookup"><span data-stu-id="d19b6-105">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="d19b6-106">Автоматическое прикрепление к существующим транзакциям можно отменить, задав</span><span class="sxs-lookup"><span data-stu-id="d19b6-106">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```csharp  
Enlist=false  
```  
  
 <span data-ttu-id="d19b6-107">в качестве параметра строки соединения для <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="d19b6-107">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d19b6-108">См. также</span><span class="sxs-lookup"><span data-stu-id="d19b6-108">See also</span></span>

- [<span data-ttu-id="d19b6-109">Oracle и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d19b6-109">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="d19b6-110">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d19b6-110">ADO.NET Overview</span></span>](ado-net-overview.md)
