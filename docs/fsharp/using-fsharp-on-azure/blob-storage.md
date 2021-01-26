---
title: 'Приступая к работе с хранилищем BLOB-объектов Azure с помощью F #'
description: Храните неструктурированные данные в облаке с помощью хранилища BLOB-объектов Azure.
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 58c120c26a1e99481b49ae3a0fb096a2188f359e
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794802"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="b2d80-103">Приступая к работе с хранилищем BLOB-объектов Azure с помощью F\#</span><span class="sxs-lookup"><span data-stu-id="b2d80-103">Get started with Azure Blob Storage using F\#</span></span>

<span data-ttu-id="b2d80-104">Хранилище BLOB-объектов Azure — это служба, которая хранит неструктурированные данные в облаке в виде объектов и больших двоичные объекты.</span><span class="sxs-lookup"><span data-stu-id="b2d80-104">Azure Blob Storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="b2d80-105">В хранилище BLOB-объектов могут храниться текстовые или двоичные данные любого типа, например документы, файлы мультимедиа или установщики приложений.</span><span class="sxs-lookup"><span data-stu-id="b2d80-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="b2d80-106">Хранилище BLOB-объектов иногда также называют хранилищем объектов.</span><span class="sxs-lookup"><span data-stu-id="b2d80-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="b2d80-107">В этой статье показано, как выполнять общие задачи с помощью хранилища BLOB-объектов.</span><span class="sxs-lookup"><span data-stu-id="b2d80-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="b2d80-108">Примеры написаны на языке F # с помощью клиентской библиотеки службы хранилища Azure для .NET.</span><span class="sxs-lookup"><span data-stu-id="b2d80-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="b2d80-109">В рассмотренных задачах содержатся сведения о передаче, перечислении, скачивании и удалении больших двоичных объектов.</span><span class="sxs-lookup"><span data-stu-id="b2d80-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="b2d80-110">Общие сведения о хранилище BLOB-объектов см. [в этом](/azure/storage/blobs/storage-quickstart-blobs-dotnet)разделе.</span><span class="sxs-lookup"><span data-stu-id="b2d80-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2d80-111">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="b2d80-111">Prerequisites</span></span>

<span data-ttu-id="b2d80-112">Для работы с этим руководством необходимо сначала [создать учетную запись хранения Azure](/azure/storage/common/storage-account-create).</span><span class="sxs-lookup"><span data-stu-id="b2d80-112">To use this guide, you must first [create an Azure storage account](/azure/storage/common/storage-account-create).</span></span> <span data-ttu-id="b2d80-113">Вам также потребуется ключ доступа к хранилищу для этой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="b2d80-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="b2d80-114">Создание скрипта F # и запуск F# Interactive</span><span class="sxs-lookup"><span data-stu-id="b2d80-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="b2d80-115">Примеры в этой статье можно использовать как в приложении F #, так и в сценарии F #.</span><span class="sxs-lookup"><span data-stu-id="b2d80-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="b2d80-116">Чтобы создать скрипт F #, создайте файл с `.fsx` расширением, например `blobs.fsx` , в среде разработки F #.</span><span class="sxs-lookup"><span data-stu-id="b2d80-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="b2d80-117">Затем используйте [Диспетчер пакетов](package-management.md) , например [пакет](https://fsprojects.github.io/Paket/) или [NuGet](https://www.nuget.org/) , для установки `WindowsAzure.Storage` `Microsoft.WindowsAzure.ConfigurationManager` пакетов и ссылок и `WindowsAzure.Storage.dll` `Microsoft.WindowsAzure.Configuration.dll` в скрипте с помощью `#r` директивы.</span><span class="sxs-lookup"><span data-stu-id="b2d80-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="b2d80-118">Добавление объявлений пространств имен</span><span class="sxs-lookup"><span data-stu-id="b2d80-118">Add namespace declarations</span></span>

<span data-ttu-id="b2d80-119">Добавьте в начало файла `blobs.fsx` следующие инструкции `open`:</span><span class="sxs-lookup"><span data-stu-id="b2d80-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="b2d80-120">Получение строки подключения</span><span class="sxs-lookup"><span data-stu-id="b2d80-120">Get your connection string</span></span>

<span data-ttu-id="b2d80-121">Для работы с этим руководством требуется строка подключения к службе хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="b2d80-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="b2d80-122">Дополнительные сведения о строках подключения см. в разделе [Настройка строк подключения к хранилищу](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="b2d80-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="b2d80-123">В этом руководстве вы вводите строку подключения в скрипте следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b2d80-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="b2d80-124">Однако это **не рекомендуется** для реальных проектов.</span><span class="sxs-lookup"><span data-stu-id="b2d80-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="b2d80-125">Ключ учетной записи хранения похож на корневой пароль для вашей учетной записи хранения.</span><span class="sxs-lookup"><span data-stu-id="b2d80-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="b2d80-126">Не забудьте защитить ключ учетной записи хранения.</span><span class="sxs-lookup"><span data-stu-id="b2d80-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="b2d80-127">Не сообщайте его другим пользователям, не определяйте его в коде и не храните его в текстовом файле, доступном другим пользователям.</span><span class="sxs-lookup"><span data-stu-id="b2d80-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="b2d80-128">Вы можете повторно создать ключ, используя портал Azure, если вы считаете, что он был скомпрометирован.</span><span class="sxs-lookup"><span data-stu-id="b2d80-128">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="b2d80-129">Для реальных приложений лучшим способом поддержания строки подключения к хранилищу является файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b2d80-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="b2d80-130">Чтобы получить строку подключения из файла конфигурации, можно сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="b2d80-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="b2d80-131">Использование диспетчера конфигураций Azure не является обязательным.</span><span class="sxs-lookup"><span data-stu-id="b2d80-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="b2d80-132">Можно также использовать API, например `ConfigurationManager` тип платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2d80-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="b2d80-133">Проанализируйте строку подключения</span><span class="sxs-lookup"><span data-stu-id="b2d80-133">Parse the connection string</span></span>

<span data-ttu-id="b2d80-134">Чтобы проанализировать строку подключения, используйте:</span><span class="sxs-lookup"><span data-stu-id="b2d80-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="b2d80-135">Он возвращает `CloudStorageAccount` .</span><span class="sxs-lookup"><span data-stu-id="b2d80-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="b2d80-136">Создание локальных фиктивных данных</span><span class="sxs-lookup"><span data-stu-id="b2d80-136">Create some local dummy data</span></span>

<span data-ttu-id="b2d80-137">Прежде чем начать, создайте в каталоге нашего скрипта некоторые фиктивные локальные данные.</span><span class="sxs-lookup"><span data-stu-id="b2d80-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="b2d80-138">Позже вы отправите эти данные.</span><span class="sxs-lookup"><span data-stu-id="b2d80-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="b2d80-139">Создание клиента службы BLOB-объектов</span><span class="sxs-lookup"><span data-stu-id="b2d80-139">Create the Blob service client</span></span>

<span data-ttu-id="b2d80-140">`CloudBlobClient`Тип позволяет извлекать контейнеры и большие двоичные объекты, хранящиеся в хранилище BLOB-объектов.</span><span class="sxs-lookup"><span data-stu-id="b2d80-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="b2d80-141">Вот один из способов создать клиента службы.</span><span class="sxs-lookup"><span data-stu-id="b2d80-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="b2d80-142">Теперь вы можете написать код, который считывает и записывает данные в хранилище BLOB-объектов.</span><span class="sxs-lookup"><span data-stu-id="b2d80-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="b2d80-143">Создание контейнера</span><span class="sxs-lookup"><span data-stu-id="b2d80-143">Create a container</span></span>

<span data-ttu-id="b2d80-144">В этом примере показано, как создать контейнер:</span><span class="sxs-lookup"><span data-stu-id="b2d80-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="b2d80-145">По умолчанию новый контейнер является закрытым. Это значит, что вам нужно указать ключ доступа к хранилищу, чтобы загрузить большие двоичные объекты из этого контейнера.</span><span class="sxs-lookup"><span data-stu-id="b2d80-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="b2d80-146">Чтобы сделать файлы в этом контейнере доступными для всех пользователей, сделайте контейнер открытым, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="b2d80-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="b2d80-147">Любой пользователь в Интернете может видеть большие двоичные объекты в открытом контейнере, но изменить или удалить их можно только при наличии ключа доступа или подписанного URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="b2d80-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="b2d80-148">Отправка BLOB-объекта в контейнер</span><span class="sxs-lookup"><span data-stu-id="b2d80-148">Upload a blob into a container</span></span>

<span data-ttu-id="b2d80-149">Хранилище BLOB-объектов Azure поддерживает блочные и страничные BLOB-объекты.</span><span class="sxs-lookup"><span data-stu-id="b2d80-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="b2d80-150">В большинстве случаев рекомендуемым типом для использования является Блочный BLOB-объект.</span><span class="sxs-lookup"><span data-stu-id="b2d80-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="b2d80-151">Для передачи файла в блочный BLOB-объект получите ссылку на контейнер и используйте ее для получения ссылки на блочный BLOB-объект.</span><span class="sxs-lookup"><span data-stu-id="b2d80-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="b2d80-152">После получения ссылки на большой двоичный объект можно передать в него любой поток данных, вызвав `UploadFromFile` метод.</span><span class="sxs-lookup"><span data-stu-id="b2d80-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="b2d80-153">Эта операция создает большой двоичный объект, если он не существовал ранее, или перезаписывает его, если он существует.</span><span class="sxs-lookup"><span data-stu-id="b2d80-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="b2d80-154">Перечисление BLOB-объектов в контейнере</span><span class="sxs-lookup"><span data-stu-id="b2d80-154">List the blobs in a container</span></span>

<span data-ttu-id="b2d80-155">Для перечисления BLOB-объектов в контейнере сначала необходимо получить ссылку на контейнер.</span><span class="sxs-lookup"><span data-stu-id="b2d80-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="b2d80-156">Затем можно использовать `ListBlobs` метод контейнера для извлечения больших двоичных объектов и (или) каталогов внутри него.</span><span class="sxs-lookup"><span data-stu-id="b2d80-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="b2d80-157">Чтобы получить доступ к широкому набору свойств и методов для возвращаемого значения `IListBlobItem` , необходимо привести его `CloudBlockBlob` к `CloudPageBlob` объекту, или `CloudBlobDirectory` .</span><span class="sxs-lookup"><span data-stu-id="b2d80-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="b2d80-158">Если тип неизвестен, можно использовать проверку типов, чтобы определить нужный тип.</span><span class="sxs-lookup"><span data-stu-id="b2d80-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="b2d80-159">Следующий код демонстрирует, как получить и вывести URI каждого элемента в контейнере `mydata` :</span><span class="sxs-lookup"><span data-stu-id="b2d80-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="b2d80-160">Кроме того, в именах больших двоичных объектов можно присвоить сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="b2d80-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="b2d80-161">Таким образом, создается такая структура виртуальных каталогов, которую можно организовывать и просматривать, как и традиционную файловую систему.</span><span class="sxs-lookup"><span data-stu-id="b2d80-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="b2d80-162">Структура каталогов — только виртуальная. единственные ресурсы, доступные в хранилище BLOB-объектов, — это контейнеры и большие двоичные объекты.</span><span class="sxs-lookup"><span data-stu-id="b2d80-162">The directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="b2d80-163">Однако клиентская библиотека хранилища предоставляет `CloudBlobDirectory` объект для ссылки на виртуальный каталог и упрощает процесс работы с большими двоичными объектами, организованными таким образом.</span><span class="sxs-lookup"><span data-stu-id="b2d80-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="b2d80-164">Например, рассмотрим следующий набор блочных BLOB-объектов в контейнере с именем `photos`:</span><span class="sxs-lookup"><span data-stu-id="b2d80-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="b2d80-165">*photo1.jpg*</span><span class="sxs-lookup"><span data-stu-id="b2d80-165">*photo1.jpg*</span></span>\
<span data-ttu-id="b2d80-166">*2015/архитектура/description.txt*</span><span class="sxs-lookup"><span data-stu-id="b2d80-166">*2015/architecture/description.txt*</span></span>\
<span data-ttu-id="b2d80-167">*2015/архитектура/photo3.jpg*</span><span class="sxs-lookup"><span data-stu-id="b2d80-167">*2015/architecture/photo3.jpg*</span></span>\
<span data-ttu-id="b2d80-168">*2015/архитектура/photo4.jpg*</span><span class="sxs-lookup"><span data-stu-id="b2d80-168">*2015/architecture/photo4.jpg*</span></span>\
<span data-ttu-id="b2d80-169">*2016/архитектура/photo5.jpg*</span><span class="sxs-lookup"><span data-stu-id="b2d80-169">*2016/architecture/photo5.jpg*</span></span>\
<span data-ttu-id="b2d80-170">*2016/архитектура/photo6.jpg*</span><span class="sxs-lookup"><span data-stu-id="b2d80-170">*2016/architecture/photo6.jpg*</span></span>\
<span data-ttu-id="b2d80-171">*2016/архитектура/description.txt*</span><span class="sxs-lookup"><span data-stu-id="b2d80-171">*2016/architecture/description.txt*</span></span>\
<span data-ttu-id="b2d80-172">*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="b2d80-172">*2016/photo7.jpg*</span></span>\

<span data-ttu-id="b2d80-173">При вызове `ListBlobs` в контейнере (как в приведенном выше примере) возвращается иерархический список.</span><span class="sxs-lookup"><span data-stu-id="b2d80-173">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="b2d80-174">Если он содержит `CloudBlobDirectory` объекты и `CloudBlockBlob` , представляющие каталоги и большие двоичные объекты в контейнере соответственно, то результирующие выходные данные выглядят примерно так:</span><span class="sxs-lookup"><span data-stu-id="b2d80-174">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="b2d80-175">При необходимости можно задать `UseFlatBlobListing` `ListBlobs` для параметра метода значение `true` .</span><span class="sxs-lookup"><span data-stu-id="b2d80-175">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="b2d80-176">В этом случае каждый большой двоичный объект в контейнере возвращается как `CloudBlockBlob` объект.</span><span class="sxs-lookup"><span data-stu-id="b2d80-176">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="b2d80-177">Вызов для `ListBlobs` возврата плоского списка выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b2d80-177">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="b2d80-178">в зависимости от текущего содержимого контейнера результаты выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b2d80-178">and, depending on the current contents of your container, the results look like this:</span></span>

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a><span data-ttu-id="b2d80-179">Скачивание больших двоичных объектов</span><span class="sxs-lookup"><span data-stu-id="b2d80-179">Download blobs</span></span>

<span data-ttu-id="b2d80-180">Чтобы скачать большие двоичные объекты, сначала извлеките ссылку на большой двоичный объект, а затем вызовите `DownloadToStream` метод.</span><span class="sxs-lookup"><span data-stu-id="b2d80-180">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="b2d80-181">В следующем примере метод используется `DownloadToStream` для передачи содержимого большого двоичного объекта в объект потока, который затем можно сохранить в локальный файл.</span><span class="sxs-lookup"><span data-stu-id="b2d80-181">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="b2d80-182">Можно также использовать `DownloadToStream` метод для загрузки содержимого большого двоичного объекта в виде текстовой строки.</span><span class="sxs-lookup"><span data-stu-id="b2d80-182">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="b2d80-183">Удаление blob-объектов</span><span class="sxs-lookup"><span data-stu-id="b2d80-183">Delete blobs</span></span>

<span data-ttu-id="b2d80-184">Чтобы удалить большой двоичный объект, сначала получите ссылку на большой двоичный объект, а затем вызовите `Delete` для него метод.</span><span class="sxs-lookup"><span data-stu-id="b2d80-184">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="b2d80-185">Асинхронное перечисление BLOB-объектов в страницах</span><span class="sxs-lookup"><span data-stu-id="b2d80-185">List blobs in pages asynchronously</span></span>

<span data-ttu-id="b2d80-186">Если вам нужно расположить большое количество BLOB-объектов или вы хотите управлять отображением количества объектов в результате запроса, вы можете задать расположение BLOB-объектов на странице.</span><span class="sxs-lookup"><span data-stu-id="b2d80-186">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="b2d80-187">В этом примере вы узнаете, как расположить запрошенные результаты на странице асинхронно для того, чтобы не блокировать выполнение задачи ожиданием большого объема возвращаемых данных.</span><span class="sxs-lookup"><span data-stu-id="b2d80-187">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="b2d80-188">В этом примере показан плоский список больших двоичных объектов, но можно также выполнить иерархическое построение, задав `useFlatBlobListing` `ListBlobsSegmentedAsync` для параметра метода значение `false` .</span><span class="sxs-lookup"><span data-stu-id="b2d80-188">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="b2d80-189">В примере определяется асинхронный метод с помощью `async` блока.</span><span class="sxs-lookup"><span data-stu-id="b2d80-189">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="b2d80-190">``let!``Ключевое слово приостанавливает выполнение метода Sample до завершения задачи листинга.</span><span class="sxs-lookup"><span data-stu-id="b2d80-190">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="b2d80-191">Теперь мы можем использовать эту асинхронную подпрограммы, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="b2d80-191">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="b2d80-192">Сначала необходимо отправить некоторые фиктивные данные (с помощью локального файла, созданного ранее в этом руководстве).</span><span class="sxs-lookup"><span data-stu-id="b2d80-192">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="b2d80-193">Теперь вызовите подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="b2d80-193">Now, call the routine.</span></span> <span data-ttu-id="b2d80-194">Используется `Async.RunSynchronously` для принудительного выполнения асинхронной операции.</span><span class="sxs-lookup"><span data-stu-id="b2d80-194">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="b2d80-195">Запись в расширенный большой двоичный объект</span><span class="sxs-lookup"><span data-stu-id="b2d80-195">Writing to an append blob</span></span>

<span data-ttu-id="b2d80-196">Добавочный большой двоичный объект оптимизирован для операций добавления, например ведения журналов.</span><span class="sxs-lookup"><span data-stu-id="b2d80-196">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="b2d80-197">Как и блочный BLOB-объект, добавочный большой двоичный объект состоит из блоков, но при добавлении нового блока в добавочный большой двоичный объект всегда добавляется в конец большого двоичного объекта.</span><span class="sxs-lookup"><span data-stu-id="b2d80-197">Like a block blob, an append blob is composed of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="b2d80-198">Вы не можете обновить или удалить существующий блок в добавочном большом двоичном объекте.</span><span class="sxs-lookup"><span data-stu-id="b2d80-198">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="b2d80-199">Идентификаторы блоков в добавочном большом двоичном объекте не отображаются, как в блочном BLOB-объекте.</span><span class="sxs-lookup"><span data-stu-id="b2d80-199">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="b2d80-200">Каждый блок в добавочном большом двоичном объекте может иметь разный размер (не более 4 МБ), кроме того, добавочный большой двоичный объект может содержать не более 50 000 блоков.</span><span class="sxs-lookup"><span data-stu-id="b2d80-200">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="b2d80-201">Таким образом, максимальный размер добавочного большого двоичного объекта немного превышает 195 ГБ (4 МБ X 50 000 блоков).</span><span class="sxs-lookup"><span data-stu-id="b2d80-201">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="b2d80-202">В следующем примере создается новый добавочный BLOB-объект и к нему добавляются некоторые данные, имитируя простую операцию ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="b2d80-202">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="b2d80-203">Дополнительные сведения о различиях между тремя типами больших двоичных объектов см. в статье [Основные сведения о блочных, страничных и добавочных BLOB-объектах](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs).</span><span class="sxs-lookup"><span data-stu-id="b2d80-203">See [Understanding Block Blobs, Page Blobs, and Append Blobs](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="b2d80-204">Одновременный доступ</span><span class="sxs-lookup"><span data-stu-id="b2d80-204">Concurrent access</span></span>

<span data-ttu-id="b2d80-205">Чтобы реализовать одновременный доступ нескольких клиентов или экземпляров процесса к BLOB-объекту, можно использовать **ETags** или **lease**.</span><span class="sxs-lookup"><span data-stu-id="b2d80-205">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

- <span data-ttu-id="b2d80-206">**Etag** — позволяет обнаружить, что BLOB-объект или контейнер были изменены другим процессом</span><span class="sxs-lookup"><span data-stu-id="b2d80-206">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

- <span data-ttu-id="b2d80-207">**Аренда** — предоставляет способ получения монопольного доступа, устанавливать возобновляемую, записи или удаления большого двоичного объекта в течение определенного периода времени.</span><span class="sxs-lookup"><span data-stu-id="b2d80-207">**Lease** - provides a way to obtain exclusive, renewable, write, or delete access to a blob for a period of time</span></span>

<span data-ttu-id="b2d80-208">Дополнительные сведения см. [в разделе Управление параллелизмом в Служба хранилища Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="b2d80-208">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="b2d80-209">Именование контейнеров</span><span class="sxs-lookup"><span data-stu-id="b2d80-209">Naming containers</span></span>

<span data-ttu-id="b2d80-210">Каждый BLOB-объект в Azure должен располагаться в контейнере.</span><span class="sxs-lookup"><span data-stu-id="b2d80-210">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="b2d80-211">Контейнер составляет часть имени BLOB-объекта.</span><span class="sxs-lookup"><span data-stu-id="b2d80-211">The container forms part of the blob name.</span></span> <span data-ttu-id="b2d80-212">Например, `mydata` — имя контейнера в таких взятых в качестве образца URI BLOB-объектов:</span><span class="sxs-lookup"><span data-stu-id="b2d80-212">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

<span data-ttu-id="b2d80-213">Имя контейнера должно быть допустимым DNS-именем и соответствовать указанным ниже правилам именования.</span><span class="sxs-lookup"><span data-stu-id="b2d80-213">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="b2d80-214">Имена контейнеров должны начинаться с буквы или цифры и могут содержать только буквы, цифры и тире (-).</span><span class="sxs-lookup"><span data-stu-id="b2d80-214">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="b2d80-215">Каждое тире (-) должно стоять непосредственно перед буквой или цифрой и после нее. В именах контейнеров запрещено использовать несколько тире подряд.</span><span class="sxs-lookup"><span data-stu-id="b2d80-215">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="b2d80-216">Все знаки в имени контейнера должны быть строчными.</span><span class="sxs-lookup"><span data-stu-id="b2d80-216">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="b2d80-217">Имя контейнера должно содержать от 3 до 63 знаков.</span><span class="sxs-lookup"><span data-stu-id="b2d80-217">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="b2d80-218">Имя контейнера всегда должно быть строчным.</span><span class="sxs-lookup"><span data-stu-id="b2d80-218">The name of a container must always be lowercase.</span></span> <span data-ttu-id="b2d80-219">При использовании заглавных букв в имени контейнера или другом нарушении правил именования контейнера может появиться ошибка 400 (Ошибка запроса).</span><span class="sxs-lookup"><span data-stu-id="b2d80-219">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="b2d80-220">Управление системой безопасности больших двоичных объектов</span><span class="sxs-lookup"><span data-stu-id="b2d80-220">Managing security for blobs</span></span>

<span data-ttu-id="b2d80-221">По умолчанию служба хранилища Azure защищает данные, ограничивая доступ к учетной записи пользователя, который владеет ключами доступа к учетной записи.</span><span class="sxs-lookup"><span data-stu-id="b2d80-221">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="b2d80-222">Если вы хотите предоставить доступ к данным больших двоичных объектов в своей учетной записи хранения, важно сделать это без ущерба для безопасности ключей доступа к учетной записи.</span><span class="sxs-lookup"><span data-stu-id="b2d80-222">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="b2d80-223">Кроме того, вы можете зашифровать данные больших двоичных объектов, чтобы обеспечить их безопасную отправку по сети в службу хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="b2d80-223">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="b2d80-224">Управление доступом к данным больших двоичных объектов</span><span class="sxs-lookup"><span data-stu-id="b2d80-224">Controlling access to blob data</span></span>

<span data-ttu-id="b2d80-225">По умолчанию данные больших двоичных объектов в учетной записи хранения доступны только владельцу учетной записи хранения.</span><span class="sxs-lookup"><span data-stu-id="b2d80-225">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="b2d80-226">По умолчанию для проверки подлинности запросов к хранилищу BLOB-объектов требуется ключ доступа к учетной записи.</span><span class="sxs-lookup"><span data-stu-id="b2d80-226">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="b2d80-227">Однако может потребоваться предоставить другим пользователям доступ к данным большого двоичного объекта.</span><span class="sxs-lookup"><span data-stu-id="b2d80-227">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="b2d80-228">Шифрование данных больших двоичных объектов</span><span class="sxs-lookup"><span data-stu-id="b2d80-228">Encrypting blob data</span></span>

<span data-ttu-id="b2d80-229">Служба хранилища Azure поддерживает шифрование данных большого двоичного объекта как на клиенте, так и на сервере.</span><span class="sxs-lookup"><span data-stu-id="b2d80-229">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b2d80-230">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="b2d80-230">Next steps</span></span>

<span data-ttu-id="b2d80-231">Вы ознакомились с базовыми понятиями о хранилище BLOB-объектов. Дополнительные сведения см. по следующим ссылкам.</span><span class="sxs-lookup"><span data-stu-id="b2d80-231">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="b2d80-232">Инструменты</span><span class="sxs-lookup"><span data-stu-id="b2d80-232">Tools</span></span>

- <span data-ttu-id="b2d80-233">[Азуресторажетипепровидер F #](https://fsprojects.github.io/AzureStorageTypeProvider/)</span><span class="sxs-lookup"><span data-stu-id="b2d80-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span></span>\
<span data-ttu-id="b2d80-234">Поставщик типов F #, который можно использовать для просмотра ресурсов хранилища Azure BLOB-объектов, таблиц и очередей, а также для простого применения операций CRUD к ним.</span><span class="sxs-lookup"><span data-stu-id="b2d80-234">An F# Type Provider that can be used to explore Blob, Table, and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="b2d80-235">[FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span><span class="sxs-lookup"><span data-stu-id="b2d80-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span></span>\
<span data-ttu-id="b2d80-236">API F # для использования службы хранилища таблиц Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="b2d80-236">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="b2d80-237">[Обозреватель службы хранилища Microsoft Azure (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span><span class="sxs-lookup"><span data-stu-id="b2d80-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span></span>\
<span data-ttu-id="b2d80-238">Бесплатное автономное приложение от корпорации Майкрософт, позволяющее визуально работать с данными службы хранилища Azure в Windows, OS X и Linux.</span><span class="sxs-lookup"><span data-stu-id="b2d80-238">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="b2d80-239">Справочная документация по хранилищу BLOB-объектов</span><span class="sxs-lookup"><span data-stu-id="b2d80-239">Blob storage reference</span></span>

- [<span data-ttu-id="b2d80-240">API-интерфейсы службы хранилища Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="b2d80-240">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- <span data-ttu-id="b2d80-241">[Azure Storage Services REST API Reference](/rest/api/storageservices/) (Справочник по REST API службы хранилища Azure)</span><span class="sxs-lookup"><span data-stu-id="b2d80-241">[Azure Storage Services REST API Reference](/rest/api/storageservices/)</span></span>

### <a name="related-guides"></a><span data-ttu-id="b2d80-242">Связанные руководства</span><span class="sxs-lookup"><span data-stu-id="b2d80-242">Related guides</span></span>

- <span data-ttu-id="b2d80-243">[Azure Blob Storage Samples for .NET](/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/) (Примеры для хранилища BLOB-объектов Azure для .NET)</span><span class="sxs-lookup"><span data-stu-id="b2d80-243">[Azure Blob Storage Samples for .NET](/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)</span></span>
- [<span data-ttu-id="b2d80-244">Начало работы с AzCopy</span><span class="sxs-lookup"><span data-stu-id="b2d80-244">Get started with AzCopy</span></span>](/azure/storage/common/storage-use-azcopy-v10)
- [<span data-ttu-id="b2d80-245">Настройка строк подключения службы хранилища Azure</span><span class="sxs-lookup"><span data-stu-id="b2d80-245">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="b2d80-246">Блог рабочей группы службы хранилища Azure</span><span class="sxs-lookup"><span data-stu-id="b2d80-246">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="b2d80-247">Краткое руководство. Использование .NET для создания большого двоичного объекта в хранилище объектов</span><span class="sxs-lookup"><span data-stu-id="b2d80-247">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
