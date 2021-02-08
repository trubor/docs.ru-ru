---
description: 'Дополнительные сведения: строка подключения и имя строки подключения'
title: Строка соединения и имя строки соединения
ms.date: 03/30/2017
ms.assetid: 473e7a3c-c88a-4a01-914a-bea82ba42866
ms.openlocfilehash: 5de81228434d3099df6e60664db0fea22f63c6ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792743"
---
# <a name="connection-string-and-connection-string-name"></a><span data-ttu-id="ed2aa-103">Строка соединения и имя строки соединения</span><span class="sxs-lookup"><span data-stu-id="ed2aa-103">Connection String and Connection String Name</span></span>

<span data-ttu-id="ed2aa-104">Свойство **строки подключения** указывает строку подключения, которую хранилище экземпляров рабочих процессов SQL должно использовать для подключения к базе данных сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="ed2aa-104">**Connection String** property specifies the connection string that the SQL Workflow Instance Store should use to connect to a persistence database.</span></span> <span data-ttu-id="ed2aa-105">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="ed2aa-105">This parameter is an optional parameter.</span></span> <span data-ttu-id="ed2aa-106">Свойство " **имя строки подключения** " указывает имя именованной строки подключения, которое должно использоваться хранилищем экземпляров рабочих процессов SQL для подключения к базе данных сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="ed2aa-106">**Connection String Name** property specifies the name of the named connection string that the SQL Workflow Instance Store should use to connect to the persistence database.</span></span> <span data-ttu-id="ed2aa-107">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="ed2aa-107">This parameter is an optional parameter.</span></span> <span data-ttu-id="ed2aa-108">Если не нужно, чтобы хранилище экземпляров рабочих процессов SQL использовало именованную строку подключения **дефаултсклворкфловинстанцестореконнектионстринг**, необходимо указать значение для свойства имя строки подключения или для свойства строки соединения.</span><span class="sxs-lookup"><span data-stu-id="ed2aa-108">You should specify a value for the Connection String Name property or the Connection String property if you do not want the SQL Workflow Instance Store to use the default named connection string **DefaultSqlWorkflowInstanceStoreConnectionString**.</span></span>
