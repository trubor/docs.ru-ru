---
description: 'Дополнительные сведения: служебная программа клиента службы данных WCF (DataSvcUtil.exe)'
title: Служебная программа клиента служб данных WCF (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 1e232538284072d82eed3f1b9e8d41f2ae950adf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791703"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a><span data-ttu-id="856df-103">Служебная программа клиента служб данных WCF (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="856df-103">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="856df-104">DataSvcUtil.exe — это средство командной строки, предоставляемое службы данных WCF, которое использует канал Open Data Protocol (OData) и создает классы клиентских служб данных, необходимые для доступа к службе данных из клиентского приложения платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="856df-104">DataSvcUtil.exe is a command-line tool provided by WCF Data Services that consumes an Open Data Protocol (OData) feed and generates the client data service classes that are needed to access a data service from a .NET Framework client application.</span></span> <span data-ttu-id="856df-105">Эта программа формирует классы данных с использованием следующих источников метаданных.</span><span class="sxs-lookup"><span data-stu-id="856df-105">This utility can generate data classes by using the following metadata sources:</span></span>

- <span data-ttu-id="856df-106">Корневой URI службы данных.</span><span class="sxs-lookup"><span data-stu-id="856df-106">The root URI of a data service.</span></span> <span data-ttu-id="856df-107">Эта программа запрашивает документ метаданных службы, в котором описывается модель данных, предоставленная службой данных.</span><span class="sxs-lookup"><span data-stu-id="856df-107">The utility requests the service metadata document, which describes the data model exposed by the data service.</span></span> <span data-ttu-id="856df-108">Дополнительные сведения см. в разделе [AtomPub (RFC5023)](https://tools.ietf.org/html/rfc5023#section-8).</span><span class="sxs-lookup"><span data-stu-id="856df-108">For more information, see [AtomPub (RFC5023)](https://tools.ietf.org/html/rfc5023#section-8).</span></span>

- <span data-ttu-id="856df-109">Файл модели данных (CSDL), определяемый на языке CSDL, как определено в спецификации [ \[ файла MC-CSDL \] : определение концептуальной схемы](/openspecs/windows_protocols/mc-csdl/c03ad8c3-e8b7-4306-af96-a9e52bb3df12) .</span><span class="sxs-lookup"><span data-stu-id="856df-109">A data model file (.csdl) defined by using the conceptual schema definition language (CSDL), as defined in the [\[MC-CSDL\]: Conceptual Schema Definition File Format](/openspecs/windows_protocols/mc-csdl/c03ad8c3-e8b7-4306-af96-a9e52bb3df12) specification.</span></span>

- <span data-ttu-id="856df-110">Файл EDMX, созданный при помощи программ для работы с моделью EDM, входящих в комплект Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="856df-110">An .edmx file created by using the Entity Data Model tools that are provided with the Entity Framework.</span></span> <span data-ttu-id="856df-111">Дополнительные сведения см. в описании [ \[ пакета MC-EDMX \] : EDM for Data Services](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16) .</span><span class="sxs-lookup"><span data-stu-id="856df-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16) specification.</span></span>

<span data-ttu-id="856df-112">Дополнительные сведения см. [в разделе как вручную создавать классы службы данных клиента](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="856df-112">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>

<span data-ttu-id="856df-113">Средство DataSvcUtil.exe устанавливается в каталог платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="856df-113">The DataSvcUtil.exe tool is installed in the .NET Framework directory.</span></span> <span data-ttu-id="856df-114">Во многих случаях это находится в *C:\Windows\Microsoft.NET\Framework\v4.0*.</span><span class="sxs-lookup"><span data-stu-id="856df-114">In many cases, this is located in *C:\Windows\Microsoft.NET\Framework\v4.0*.</span></span> <span data-ttu-id="856df-115">Для 64-разрядных систем это расположение находится в *C:\Windows\Microsoft.NET\Framework64\v4.0*.</span><span class="sxs-lookup"><span data-stu-id="856df-115">For 64-bit systems, this is located in *C:\Windows\Microsoft.NET\Framework64\v4.0*.</span></span> <span data-ttu-id="856df-116">Вы также можете получить доступ к средству DataSvcUtil.exe из Командная строка разработчика для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="856df-116">You can also access the DataSvcUtil.exe tool from Developer Command Prompt for Visual Studio.</span></span>

## <a name="syntax"></a><span data-ttu-id="856df-117">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="856df-117">Syntax</span></span>

```console
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a><span data-ttu-id="856df-118">Параметры</span><span class="sxs-lookup"><span data-stu-id="856df-118">Parameters</span></span>

|<span data-ttu-id="856df-119">Параметр</span><span class="sxs-lookup"><span data-stu-id="856df-119">Option</span></span>|<span data-ttu-id="856df-120">Описание</span><span class="sxs-lookup"><span data-stu-id="856df-120">Description</span></span>|
|------------|-----------------|
|`/dataservicecollection`|<span data-ttu-id="856df-121">Указывает, что будет также сформирован код, необходимый для привязки объектов к элементам управления.</span><span class="sxs-lookup"><span data-stu-id="856df-121">Specifies that the code required to bind objects to controls is also generated.</span></span>|
|`/help`<br /><br /> <span data-ttu-id="856df-122">-или-</span><span class="sxs-lookup"><span data-stu-id="856df-122">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="856df-123">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="856df-123">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="856df-124">`/in:` *\<file>*</span><span class="sxs-lookup"><span data-stu-id="856df-124">`/in:` *\<file>*</span></span>|<span data-ttu-id="856df-125">Указывает файл CSDL или EDMX либо каталог, в котором находится этот файл.</span><span class="sxs-lookup"><span data-stu-id="856df-125">Specifies the .csdl or .edmx file or a directory where the file is located.</span></span>|
|<span data-ttu-id="856df-126">`/language:`[VB&#124;CSharp]</span><span class="sxs-lookup"><span data-stu-id="856df-126">`/language:`[VB&#124;CSharp]</span></span>|<span data-ttu-id="856df-127">Задает язык для сформированных файлов с исходным кодом.</span><span class="sxs-lookup"><span data-stu-id="856df-127">Specifies the language for the generated source code files.</span></span> <span data-ttu-id="856df-128">Язык по умолчанию — C#.</span><span class="sxs-lookup"><span data-stu-id="856df-128">The language defaults to C#.</span></span>|
|`/nologo`|<span data-ttu-id="856df-129">Отключает вывод сообщения об авторских правах.</span><span class="sxs-lookup"><span data-stu-id="856df-129">Suppresses the copyright message from displaying.</span></span>|
|<span data-ttu-id="856df-130">`/out:` *\<file>*</span><span class="sxs-lookup"><span data-stu-id="856df-130">`/out:` *\<file>*</span></span>|<span data-ttu-id="856df-131">Задает имя файла с исходным кодом, в котором содержатся сформированные клиентские классы службы данных.</span><span class="sxs-lookup"><span data-stu-id="856df-131">Specifies the name of the source code file that contains the generated client data service classes.</span></span>|
|<span data-ttu-id="856df-132">`/uri:` *\<string>*</span><span class="sxs-lookup"><span data-stu-id="856df-132">`/uri:` *\<string>*</span></span>|<span data-ttu-id="856df-133">URI веб-канала OData.</span><span class="sxs-lookup"><span data-stu-id="856df-133">The URI of the OData feed.</span></span>|
|<span data-ttu-id="856df-134">`/version:`[1,0&#124;2,0]</span><span class="sxs-lookup"><span data-stu-id="856df-134">`/version:`[1.0&#124;2.0]</span></span>|<span data-ttu-id="856df-135">Указывает максимально допустимую версию OData.</span><span class="sxs-lookup"><span data-stu-id="856df-135">Specifies the highest accepted version of OData.</span></span> <span data-ttu-id="856df-136">Версия определяется на основе `DataServiceVersion` атрибута элемента данных в возвращенных метаданных службы данных.</span><span class="sxs-lookup"><span data-stu-id="856df-136">The version is determined based on the `DataServiceVersion` attribute of the DataService element in the returned data service metadata.</span></span> <span data-ttu-id="856df-137">Дополнительные сведения см. в разделе [Управление версиями службы данных](data-service-versioning-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="856df-137">For more information, see [Data Service Versioning](data-service-versioning-wcf-data-services.md).</span></span> <span data-ttu-id="856df-138">При указании `/dataservicecollection` параметра необходимо также указать, `/version:2.0` чтобы включить привязку данных.</span><span class="sxs-lookup"><span data-stu-id="856df-138">When you specify the `/dataservicecollection` parameter, you must also specify `/version:2.0` to enable data binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="856df-139">См. также</span><span class="sxs-lookup"><span data-stu-id="856df-139">See also</span></span>

- [<span data-ttu-id="856df-140">Создание библиотеки клиентов службы данных</span><span class="sxs-lookup"><span data-stu-id="856df-140">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="856df-141">Практическое руководство. Добавление ссылки на службу данных</span><span class="sxs-lookup"><span data-stu-id="856df-141">How to: Add a Data Service Reference</span></span>](how-to-add-a-data-service-reference-wcf-data-services.md)
