---
title: 'Приступая к работе с хранилищем таблиц Azure с помощью F #'
description: Храните структурированные данные в облаке с помощью хранилища таблиц Azure или Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.custom: devx-track-fsharp
ms.openlocfilehash: bc8e111636013930f7c7d4f59d1ef0720298cb9f
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899286"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="6b402-103">Приступая к работе с хранилищем таблиц Azure и Azure Cosmos DB API таблиц с помощью F\#</span><span class="sxs-lookup"><span data-stu-id="6b402-103">Get started with Azure Table Storage and the Azure Cosmos DB Table API using F\#</span></span>

<span data-ttu-id="6b402-104">Хранилище таблиц Azure — это служба, которая хранит структурированные данные NoSQL в облаке.</span><span class="sxs-lookup"><span data-stu-id="6b402-104">Azure Table Storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="6b402-105">Хранилище таблиц — это хранилище ключей и атрибутов, реализованное в виде бессхемной конструкции.</span><span class="sxs-lookup"><span data-stu-id="6b402-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="6b402-106">Такая конструкция хранилища таблиц позволяет легко адаптировать данные по мере расширения приложения.</span><span class="sxs-lookup"><span data-stu-id="6b402-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="6b402-107">Быстрый и экономичный доступ к данным предоставляется приложениям всех видов.</span><span class="sxs-lookup"><span data-stu-id="6b402-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="6b402-108">Табличное хранилище обычно значительно дешевле, чем традиционная база данных SQL для тех же объемов данных.</span><span class="sxs-lookup"><span data-stu-id="6b402-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="6b402-109">Табличное хранилище можно использовать для хранения гибких наборов данных, например пользовательских данных для веб-приложений, адресных книг, сведений об устройстве, а также метаданных любого другого типа, которые требуются вашей службе.</span><span class="sxs-lookup"><span data-stu-id="6b402-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="6b402-110">В таблице можно хранить любое количество сущностей, а учетная запись хранения может содержать любое количество таблиц в пределах емкости учетной записи.</span><span class="sxs-lookup"><span data-stu-id="6b402-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="6b402-111">Azure Cosmos DB предоставляет API таблиц для приложений, написанных для хранилища таблиц Azure и требующих таких возможностей:</span><span class="sxs-lookup"><span data-stu-id="6b402-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table Storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="6b402-112">Комплексные возможности глобального распределения.</span><span class="sxs-lookup"><span data-stu-id="6b402-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="6b402-113">выделенная пропускная способность в любой точке мира;</span><span class="sxs-lookup"><span data-stu-id="6b402-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="6b402-114">задержка меньше 10 миллисекунд на уровне 99-го процентиля;</span><span class="sxs-lookup"><span data-stu-id="6b402-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="6b402-115">гарантированно высокий уровень доступности;</span><span class="sxs-lookup"><span data-stu-id="6b402-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="6b402-116">автоматическое вторичное индексирование.</span><span class="sxs-lookup"><span data-stu-id="6b402-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="6b402-117">Приложения, написанные для хранилища таблиц Azure, можно перенести в Azure Cosmos DB с помощью API таблиц без изменений кода и воспользоваться преимуществами расширенных возможностей.</span><span class="sxs-lookup"><span data-stu-id="6b402-117">Applications written for Azure Table Storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="6b402-118">API таблицы включает клиентские пакеты SDK для .NET., Java, Python и Node.js.</span><span class="sxs-lookup"><span data-stu-id="6b402-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="6b402-119">Дополнительные сведения см. [в статье Введение в Azure Cosmos DB API таблиц](/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="6b402-119">For more information, see [Introduction to Azure Cosmos DB Table API](/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="6b402-120">О данном учебнике</span><span class="sxs-lookup"><span data-stu-id="6b402-120">About this tutorial</span></span>

<span data-ttu-id="6b402-121">В этом руководстве показано, как написать код F # для выполнения некоторых распространенных задач с помощью хранилища таблиц Azure или Azure Cosmos DB API таблиц, включая создание и удаление таблицы, а также вставку, обновление, удаление и выполнение запросов к данным таблицы.</span><span class="sxs-lookup"><span data-stu-id="6b402-121">This tutorial shows how to write F# code to do some common tasks using Azure Table Storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6b402-122">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="6b402-122">Prerequisites</span></span>

<span data-ttu-id="6b402-123">Для работы с этим руководством необходимо сначала [создать учетную запись хранения Azure](/azure/storage/storage-create-storage-account) или [Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="6b402-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="6b402-124">Создание скрипта F # и запуск F# Interactive</span><span class="sxs-lookup"><span data-stu-id="6b402-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="6b402-125">Примеры в этой статье можно использовать как в приложении F #, так и в сценарии F #.</span><span class="sxs-lookup"><span data-stu-id="6b402-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="6b402-126">Чтобы создать скрипт F #, создайте файл с `.fsx` расширением, например `tables.fsx` , в среде разработки F #.</span><span class="sxs-lookup"><span data-stu-id="6b402-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="6b402-127">Затем используйте [Диспетчер пакетов](package-management.md) , например [пакет](https://fsprojects.github.io/Paket/) или [NuGet](https://www.nuget.org/) , для установки `WindowsAzure.Storage` пакета и ссылки `WindowsAzure.Storage.dll` в скрипте с помощью `#r` директивы.</span><span class="sxs-lookup"><span data-stu-id="6b402-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="6b402-128">Повторите эту операцию для `Microsoft.WindowsAzure.ConfigurationManager` , чтобы получить пространство имен Microsoft. Azure.</span><span class="sxs-lookup"><span data-stu-id="6b402-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="6b402-129">Добавление объявлений пространств имен</span><span class="sxs-lookup"><span data-stu-id="6b402-129">Add namespace declarations</span></span>

<span data-ttu-id="6b402-130">Добавьте в начало файла `tables.fsx` следующие инструкции `open`:</span><span class="sxs-lookup"><span data-stu-id="6b402-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="6b402-131">Получение строки подключения к службе хранилища Azure</span><span class="sxs-lookup"><span data-stu-id="6b402-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="6b402-132">Если вы подключаетесь к службе таблиц службы хранилища Azure, вам потребуется строка подключения для этого руководства.</span><span class="sxs-lookup"><span data-stu-id="6b402-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="6b402-133">Строку подключения можно скопировать из портал Azure.</span><span class="sxs-lookup"><span data-stu-id="6b402-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="6b402-134">Дополнительные сведения о строках подключения см. в разделе [Настройка строк подключения к хранилищу](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="6b402-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="6b402-135">Получение строки подключения Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6b402-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="6b402-136">Если вы подключаетесь к Azure Cosmos DB, вам потребуется строка подключения для этого руководства.</span><span class="sxs-lookup"><span data-stu-id="6b402-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="6b402-137">Строку подключения можно скопировать из портал Azure.</span><span class="sxs-lookup"><span data-stu-id="6b402-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="6b402-138">В портал Azure в учетной записи Cosmos DB перейдите в раздел **Параметры**  >  **строка подключения** и нажмите кнопку **Копировать** , чтобы скопировать основную строку подключения.</span><span class="sxs-lookup"><span data-stu-id="6b402-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and select the **Copy** button to copy your Primary Connection String.</span></span>

<span data-ttu-id="6b402-139">Для этого руководства введите в скрипт строку подключения, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="6b402-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="6b402-140">Однако это **не рекомендуется** для реальных проектов.</span><span class="sxs-lookup"><span data-stu-id="6b402-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="6b402-141">Ключ учетной записи хранения похож на корневой пароль для вашей учетной записи хранения.</span><span class="sxs-lookup"><span data-stu-id="6b402-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="6b402-142">Не забудьте защитить ключ учетной записи хранения.</span><span class="sxs-lookup"><span data-stu-id="6b402-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="6b402-143">Не сообщайте его другим пользователям, не определяйте его в коде и не храните его в текстовом файле, доступном другим пользователям.</span><span class="sxs-lookup"><span data-stu-id="6b402-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="6b402-144">Вы можете повторно создать ключ, используя портал Azure, если вы считаете, что он был скомпрометирован.</span><span class="sxs-lookup"><span data-stu-id="6b402-144">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="6b402-145">Для реальных приложений лучшим способом поддержания строки подключения к хранилищу является файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6b402-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="6b402-146">Чтобы получить строку подключения из файла конфигурации, можно сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="6b402-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="6b402-147">Использование диспетчера конфигураций Azure не является обязательным.</span><span class="sxs-lookup"><span data-stu-id="6b402-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="6b402-148">Можно также использовать API, например `ConfigurationManager` тип платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b402-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="6b402-149">Проанализируйте строку подключения</span><span class="sxs-lookup"><span data-stu-id="6b402-149">Parse the connection string</span></span>

<span data-ttu-id="6b402-150">Чтобы проанализировать строку подключения, используйте:</span><span class="sxs-lookup"><span data-stu-id="6b402-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="6b402-151">Он возвращает `CloudStorageAccount` .</span><span class="sxs-lookup"><span data-stu-id="6b402-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="6b402-152">Создание клиента службы таблиц</span><span class="sxs-lookup"><span data-stu-id="6b402-152">Create the Table service client</span></span>

<span data-ttu-id="6b402-153">`CloudTableClient`Класс позволяет извлекать таблицы и сущности в хранилище таблиц.</span><span class="sxs-lookup"><span data-stu-id="6b402-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="6b402-154">Вот один из способов создать клиента службы.</span><span class="sxs-lookup"><span data-stu-id="6b402-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="6b402-155">Теперь вы можете написать код, который считывает и записывает данные в хранилище таблиц.</span><span class="sxs-lookup"><span data-stu-id="6b402-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="6b402-156">Создание таблицы</span><span class="sxs-lookup"><span data-stu-id="6b402-156">Create a table</span></span>

<span data-ttu-id="6b402-157">В этом примере показано, как создать таблицу, если она не существует:</span><span class="sxs-lookup"><span data-stu-id="6b402-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="6b402-158">Добавление сущности в таблицу</span><span class="sxs-lookup"><span data-stu-id="6b402-158">Add an entity to a table</span></span>

<span data-ttu-id="6b402-159">Сущность должна иметь тип, наследующий от `TableEntity` .</span><span class="sxs-lookup"><span data-stu-id="6b402-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="6b402-160">Можно расширить `TableEntity` любым способом, но у вашего типа *должен* быть конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="6b402-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="6b402-161">Только свойства, имеющие `get` и, и, `set` хранятся в таблице Azure.</span><span class="sxs-lookup"><span data-stu-id="6b402-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="6b402-162">Ключ секции и строки сущности уникально идентифицируют сущность в таблице.</span><span class="sxs-lookup"><span data-stu-id="6b402-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="6b402-163">Сущности с одинаковым ключом раздела можно запрашивать быстрее, чем с разными ключами раздела, но использование различных ключей разделов обеспечивает более высокую масштабируемость параллельных операций.</span><span class="sxs-lookup"><span data-stu-id="6b402-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="6b402-164">Ниже приведен пример `Customer` , в котором в `lastName` качестве ключа секции используется, а в `firstName` качестве ключа строки.</span><span class="sxs-lookup"><span data-stu-id="6b402-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="6b402-165">Теперь добавьте `Customer` в таблицу.</span><span class="sxs-lookup"><span data-stu-id="6b402-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="6b402-166">Для этого создайте объект `TableOperation` , который выполняется для таблицы.</span><span class="sxs-lookup"><span data-stu-id="6b402-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="6b402-167">В этом случае создается `Insert` операция.</span><span class="sxs-lookup"><span data-stu-id="6b402-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="6b402-168">Вставка пакета сущностей</span><span class="sxs-lookup"><span data-stu-id="6b402-168">Insert a batch of entities</span></span>

<span data-ttu-id="6b402-169">Пакет сущностей можно вставить в таблицу с помощью одной операции записи.</span><span class="sxs-lookup"><span data-stu-id="6b402-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="6b402-170">Пакетные операции позволяют объединять операции в одно выполнение, но имеют некоторые ограничения.</span><span class="sxs-lookup"><span data-stu-id="6b402-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="6b402-171">Обновления, удаления и вставки можно выполнять в одной и той же пакетной операции.</span><span class="sxs-lookup"><span data-stu-id="6b402-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="6b402-172">Пакетная операция может включать до 100 сущностей.</span><span class="sxs-lookup"><span data-stu-id="6b402-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="6b402-173">Все сущности в пакетной операции должны иметь один и тот же ключ секции.</span><span class="sxs-lookup"><span data-stu-id="6b402-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="6b402-174">Хотя можно выполнить запрос в пакетной операции, он должен быть единственной операцией в пакете.</span><span class="sxs-lookup"><span data-stu-id="6b402-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="6b402-175">Ниже приведен код, объединяющий две операции вставки в пакетную операцию:</span><span class="sxs-lookup"><span data-stu-id="6b402-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="6b402-176">Получение всех сущностей в разделе</span><span class="sxs-lookup"><span data-stu-id="6b402-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="6b402-177">Чтобы запросить все сущности из таблицы, используйте объект `TableQuery`.</span><span class="sxs-lookup"><span data-stu-id="6b402-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="6b402-178">Здесь выполняется фильтрация для сущностей, где "Иванов" — ключ секции.</span><span class="sxs-lookup"><span data-stu-id="6b402-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="6b402-179">Теперь результаты будут напечатаны следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6b402-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="6b402-180">Получение диапазона сущностей в разделе</span><span class="sxs-lookup"><span data-stu-id="6b402-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="6b402-181">Если вы не хотите запрашивать все сущности в разделе, можно указать диапазон, объединив фильтр ключа раздела с фильтром ключа строк.</span><span class="sxs-lookup"><span data-stu-id="6b402-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="6b402-182">Здесь используются два фильтра для получения всех сущностей в разделе "Smith", где ключ строки (имя) начинается с буквы, предшествующей "M", в алфавите.</span><span class="sxs-lookup"><span data-stu-id="6b402-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="6b402-183">Теперь результаты будут напечатаны следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6b402-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="6b402-184">Извлечение одной сущности</span><span class="sxs-lookup"><span data-stu-id="6b402-184">Retrieve a single entity</span></span>

<span data-ttu-id="6b402-185">Можно написать запрос для получения отдельной сущности.</span><span class="sxs-lookup"><span data-stu-id="6b402-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="6b402-186">Здесь `TableOperation` для указания клиента «Бен Смит» используется.</span><span class="sxs-lookup"><span data-stu-id="6b402-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="6b402-187">Вместо коллекции вы получаете обратную передачу `Customer` .</span><span class="sxs-lookup"><span data-stu-id="6b402-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="6b402-188">Указание как ключа секции, так и ключа строки в запросе — самый быстрый способ извлечь одну сущность из службы таблиц.</span><span class="sxs-lookup"><span data-stu-id="6b402-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="6b402-189">Теперь результаты будут напечатаны следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6b402-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a><span data-ttu-id="6b402-190">Замена сущности</span><span class="sxs-lookup"><span data-stu-id="6b402-190">Replace an entity</span></span>

<span data-ttu-id="6b402-191">Чтобы обновить сущность, извлеките ее из службы таблиц, измените объект сущности, а затем сохраните изменения обратно в службу таблиц с помощью `Replace` операции.</span><span class="sxs-lookup"><span data-stu-id="6b402-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="6b402-192">Это приводит к тому, что сущность будет полностью заменена на сервере, если только сущность на сервере не изменялась с момента получения. в этом случае операция завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="6b402-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="6b402-193">Этот сбой заключается в предотвращении непреднамеренной перезаписи изменений из других источников в приложении.</span><span class="sxs-lookup"><span data-stu-id="6b402-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="6b402-194">Вставка или замена сущности</span><span class="sxs-lookup"><span data-stu-id="6b402-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="6b402-195">Иногда неизвестно, существует ли сущность в таблице.</span><span class="sxs-lookup"><span data-stu-id="6b402-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="6b402-196">Если это так, текущие значения, хранящиеся в нем, больше не нужны.</span><span class="sxs-lookup"><span data-stu-id="6b402-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="6b402-197">С помощью можно `InsertOrReplace` создать сущность или заменить ее, если она существует, независимо от ее состояния.</span><span class="sxs-lookup"><span data-stu-id="6b402-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="6b402-198">Запрос подмножества свойств сущности</span><span class="sxs-lookup"><span data-stu-id="6b402-198">Query a subset of entity properties</span></span>

<span data-ttu-id="6b402-199">Запрос таблицы может получить лишь несколько свойств сущности, а не все.</span><span class="sxs-lookup"><span data-stu-id="6b402-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="6b402-200">Этот метод, называемый проекцией, может повысить производительность запросов, особенно для больших сущностей.</span><span class="sxs-lookup"><span data-stu-id="6b402-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="6b402-201">Здесь вы возвращаете только адреса электронной почты с помощью `DynamicTableEntity` и `EntityResolver` .</span><span class="sxs-lookup"><span data-stu-id="6b402-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="6b402-202">Проекция не поддерживается в эмуляторе локального хранилища, поэтому этот код выполняется, только если вы используете учетную запись службы таблиц.</span><span class="sxs-lookup"><span data-stu-id="6b402-202">Projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="6b402-203">Асинхронное получение объектов со страниц</span><span class="sxs-lookup"><span data-stu-id="6b402-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="6b402-204">Если вы читаете большое количество сущностей и хотите обрабатывать их по мере их извлечения, а не ждать их возврата, можно использовать сегментированный запрос.</span><span class="sxs-lookup"><span data-stu-id="6b402-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="6b402-205">Здесь вы возвращаете результаты на страницах с помощью асинхронного рабочего процесса, чтобы выполнение не блокировалось, пока не будет возвращен большой набор результатов.</span><span class="sxs-lookup"><span data-stu-id="6b402-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="6b402-206">Теперь это вычисление выполняется синхронно:</span><span class="sxs-lookup"><span data-stu-id="6b402-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="6b402-207">Удаление сущности</span><span class="sxs-lookup"><span data-stu-id="6b402-207">Delete an entity</span></span>

<span data-ttu-id="6b402-208">Сущность можно удалить после ее получения.</span><span class="sxs-lookup"><span data-stu-id="6b402-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="6b402-209">Как и при обновлении сущности, эта ошибка возникает, если сущность изменилась со времени ее получения.</span><span class="sxs-lookup"><span data-stu-id="6b402-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="6b402-210">Удаление таблицы</span><span class="sxs-lookup"><span data-stu-id="6b402-210">Delete a table</span></span>

<span data-ttu-id="6b402-211">Вы можете удалить таблицу из учетной записи хранения.</span><span class="sxs-lookup"><span data-stu-id="6b402-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="6b402-212">Удаленную таблицу нельзя воссоздать в течение определенного времени после удаления.</span><span class="sxs-lookup"><span data-stu-id="6b402-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="6b402-213">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="6b402-213">Next steps</span></span>

<span data-ttu-id="6b402-214">Теперь, когда вы узнали основные сведения о хранилище таблиц, перейдите по следующим ссылкам, чтобы узнать о более сложных задачах хранилища и Azure Cosmos DB API таблиц.</span><span class="sxs-lookup"><span data-stu-id="6b402-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="6b402-215">Общие сведения о Azure Cosmos DB API таблиц</span><span class="sxs-lookup"><span data-stu-id="6b402-215">Introduction to Azure Cosmos DB Table API</span></span>](/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="6b402-216">Справочник по клиентской библиотеке хранилища для .NET</span><span class="sxs-lookup"><span data-stu-id="6b402-216">Storage Client Library for .NET reference</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="6b402-217">Поставщик типов службы хранилища Azure</span><span class="sxs-lookup"><span data-stu-id="6b402-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="6b402-218">Блог рабочей группы службы хранилища Azure</span><span class="sxs-lookup"><span data-stu-id="6b402-218">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="6b402-219">Настройка строк подключения</span><span class="sxs-lookup"><span data-stu-id="6b402-219">Configuring Connection Strings</span></span>](/azure/storage/common/storage-configure-connection-string)
