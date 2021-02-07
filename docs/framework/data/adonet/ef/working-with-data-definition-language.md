---
description: 'Дополнительные сведения: работа с языком описания данных'
title: Работа с языком описания данных DDL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 2f924087d12b519e6086289a91dedce3a88199f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673028"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="4a8a3-103">Работа с языком описания данных DDL</span><span class="sxs-lookup"><span data-stu-id="4a8a3-103">Working with Data Definition Language</span></span>

<span data-ttu-id="4a8a3-104">Начиная с платформа .NET Framework версии 4 Entity Framework поддерживает язык описания данных (DDL).</span><span class="sxs-lookup"><span data-stu-id="4a8a3-104">Starting with the .NET Framework version 4, the Entity Framework supports data definition language (DDL).</span></span> <span data-ttu-id="4a8a3-105">Это позволяет создавать и удалять экземпляры базы данных с использованием строки подключения и метаданных модели хранения (SSDL).</span><span class="sxs-lookup"><span data-stu-id="4a8a3-105">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="4a8a3-106">В следующих методах в <xref:System.Data.Objects.ObjectContext> с помощью строки соединения и содержимого SSDL выполняются следующие задачи: создание базы данных, удаление базы данных, проверка наличия базы данных и просмотр сформированного скрипта DDL.</span><span class="sxs-lookup"><span data-stu-id="4a8a3-106">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
> <span data-ttu-id="4a8a3-107">Предполагается наличие достаточных разрешений для выполнения команд DDL.</span><span class="sxs-lookup"><span data-stu-id="4a8a3-107">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="4a8a3-108">Ранее указанные методы делегируют большую часть работы базовому поставщику данных ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="4a8a3-108">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="4a8a3-109">Поставщик отвечает за соблюдение соглашения об именах, применяемых при создании объектов базы данных, в соответствии с правилами, используемыми для запросов и обновлений.</span><span class="sxs-lookup"><span data-stu-id="4a8a3-109">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="4a8a3-110">В следующем примере показано, как создать базу данных по существующей модели.</span><span class="sxs-lookup"><span data-stu-id="4a8a3-110">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="4a8a3-111">Кроме того, новый объект сущности добавляется в контекст объекта, а затем сохраняется в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4a8a3-111">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="4a8a3-112">Процедуры</span><span class="sxs-lookup"><span data-stu-id="4a8a3-112">Procedures</span></span>  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="4a8a3-113">Определение базы данных по существующей модели</span><span class="sxs-lookup"><span data-stu-id="4a8a3-113">To define a database based on the existing model</span></span>  
  
1. <span data-ttu-id="4a8a3-114">Создайте консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="4a8a3-114">Create a console application.</span></span>  
  
2. <span data-ttu-id="4a8a3-115">Добавьте существующую модель в приложение.</span><span class="sxs-lookup"><span data-stu-id="4a8a3-115">Add an existing model to your application.</span></span>  
  
    1. <span data-ttu-id="4a8a3-116">Добавьте пустую модель с именем `SchoolModel` .</span><span class="sxs-lookup"><span data-stu-id="4a8a3-116">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="4a8a3-117">Чтобы создать пустую модель, см. раздел [как создать файл EDMX](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="4a8a3-117">To create an empty model, see the [How to: Create a New .edmx File](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) topic.</span></span>  
  
     <span data-ttu-id="4a8a3-118">В проект будет добавлен файл SchoolModel.edmx.</span><span class="sxs-lookup"><span data-stu-id="4a8a3-118">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1. <span data-ttu-id="4a8a3-119">Скопируйте концептуальное, хранилище и сопоставленное содержимое для модели School из статьи [School Model (учебная модель](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) ).</span><span class="sxs-lookup"><span data-stu-id="4a8a3-119">Copy the conceptual, storage, and mapping content for the School model from the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) topic.</span></span>  
  
    2. <span data-ttu-id="4a8a3-120">Откройте файл SchoolModel.edmx и вставьте нужное содержимое в тегах `edmx:Runtime`.</span><span class="sxs-lookup"><span data-stu-id="4a8a3-120">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3. <span data-ttu-id="4a8a3-121">Добавьте следующий код в функцию main.</span><span class="sxs-lookup"><span data-stu-id="4a8a3-121">Add the following code to your main function.</span></span> <span data-ttu-id="4a8a3-122">Этот код инициализирует строку подключения с сервером базы данных, просматривает скрипт DDL, создает базу данных, добавляет новую сущность в контекст и сохраняет изменения в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4a8a3-122">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
