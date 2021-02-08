---
description: Дополнительные сведения см. в статье интерфейсы метаданных.
title: Интерфейсы метаданных
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4851fbc93bfa29f1b4b5015c82f05c1b200b9092
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799139"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="10e3b-103">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="10e3b-103">Metadata Interfaces</span></span>

<span data-ttu-id="10e3b-104">В этом разделе описываются неуправляемые интерфейсы, обеспечивающие доступ к метаданным, предоставляемым типами, методами, полями и прочими объектами .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="10e3b-104">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10e3b-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="10e3b-105">In This Section</span></span>  

 [<span data-ttu-id="10e3b-106">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="10e3b-106">ICeeGen Interface</span></span>](iceegen-interface.md)  
 <span data-ttu-id="10e3b-107">Предоставляет методы для динамической компиляции кода.</span><span class="sxs-lookup"><span data-stu-id="10e3b-107">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="10e3b-108">Интерфейс IHostFilter</span><span class="sxs-lookup"><span data-stu-id="10e3b-108">IHostFilter Interface</span></span>](ihostfilter-interface.md)  
 <span data-ttu-id="10e3b-109">Предоставляет метод, с помощью которого узел среды выполнения помечает лексемы метаданных для обработки.</span><span class="sxs-lookup"><span data-stu-id="10e3b-109">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="10e3b-110">Интерфейс IMapToken</span><span class="sxs-lookup"><span data-stu-id="10e3b-110">IMapToken Interface</span></span>](imaptoken-interface.md)  
 <span data-ttu-id="10e3b-111">Предоставляет возможности сопоставления между импортированными и выпущенными сигнатурами метаданных.</span><span class="sxs-lookup"><span data-stu-id="10e3b-111">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="10e3b-112">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="10e3b-112">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)  
 <span data-ttu-id="10e3b-113">Предоставляет методы, поддерживающие модель самоописания, которая используется средой CLR для разрешения и потребления ресурсов.</span><span class="sxs-lookup"><span data-stu-id="10e3b-113">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="10e3b-114">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="10e3b-114">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)  
 <span data-ttu-id="10e3b-115">Предоставляет методы для доступа и изучения содержимого манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="10e3b-115">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="10e3b-116">Интерфейс IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="10e3b-116">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)  
 <span data-ttu-id="10e3b-117">Предоставляет методы для сопоставления библиотек типов с их сигнатурами метаданных и для преобразования из одних в другие.</span><span class="sxs-lookup"><span data-stu-id="10e3b-117">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="10e3b-118">Интерфейс IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="10e3b-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)  
 <span data-ttu-id="10e3b-119">`IMetaDataDispenser` устарел.</span><span class="sxs-lookup"><span data-stu-id="10e3b-119">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="10e3b-120">Взамен рекомендуется использовать `IMetaDataDispenserEx`.</span><span class="sxs-lookup"><span data-stu-id="10e3b-120">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="10e3b-121">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="10e3b-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)  
 <span data-ttu-id="10e3b-122">Предоставляет методы, назначающие области памяти для создания или изменения метаданных.</span><span class="sxs-lookup"><span data-stu-id="10e3b-122">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="10e3b-123">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="10e3b-123">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)  
 <span data-ttu-id="10e3b-124">Предоставляет методы для создания, изменения и хранения метаданных о сборке в текущей заданной области.</span><span class="sxs-lookup"><span data-stu-id="10e3b-124">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="10e3b-125">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="10e3b-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)  
 <span data-ttu-id="10e3b-126">Предоставляет методы для определения и изменения сигнатур метаданных методов и конструкторов с помощью параметров типа <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="10e3b-126">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="10e3b-127">Интерфейс IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="10e3b-127">IMetaDataError Interface</span></span>](imetadataerror-interface.md)  
 <span data-ttu-id="10e3b-128">Предоставляет механизм обратного вызова для сообщения об ошибках в процессе разрешения сигнатуры метаданных для сборки.</span><span class="sxs-lookup"><span data-stu-id="10e3b-128">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="10e3b-129">Интерфейс IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="10e3b-129">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)  
 <span data-ttu-id="10e3b-130">Предоставляет методы для пометки и фильтрации лексем метаданных во избежание повторения действий, которые уже были выполнены.</span><span class="sxs-lookup"><span data-stu-id="10e3b-130">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="10e3b-131">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="10e3b-131">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)  
 <span data-ttu-id="10e3b-132">Предоставляет методы для импорта типов из других сборок и манипуляций с ними.</span><span class="sxs-lookup"><span data-stu-id="10e3b-132">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="10e3b-133">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="10e3b-133">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)  
 <span data-ttu-id="10e3b-134">Расширяет `IMetaDataImport` для обеспечения возможности работы с универсальными типами.</span><span class="sxs-lookup"><span data-stu-id="10e3b-134">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="10e3b-135">Интерфейс IMetaDataInfo</span><span class="sxs-lookup"><span data-stu-id="10e3b-135">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)  
 <span data-ttu-id="10e3b-136">Предоставляет метод, который получает сведения о сопоставлении метаданных из файла на диске с памятью.</span><span class="sxs-lookup"><span data-stu-id="10e3b-136">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="10e3b-137">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="10e3b-137">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)  
 <span data-ttu-id="10e3b-138">Предоставляет методы для хранения и извлечения сведений о метаданных в таблицах.</span><span class="sxs-lookup"><span data-stu-id="10e3b-138">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="10e3b-139">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="10e3b-139">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)  
 <span data-ttu-id="10e3b-140">Расширяет `IMetaDataTables` для включения методов работы с потоками метаданных.</span><span class="sxs-lookup"><span data-stu-id="10e3b-140">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="10e3b-141">Интерфейс IMetaDataValidate</span><span class="sxs-lookup"><span data-stu-id="10e3b-141">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)  
 <span data-ttu-id="10e3b-142">Предоставляет методы, используемые для проверки сигнатур метаданных.</span><span class="sxs-lookup"><span data-stu-id="10e3b-142">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="10e3b-143">См. также</span><span class="sxs-lookup"><span data-stu-id="10e3b-143">Related Sections</span></span>  

 [<span data-ttu-id="10e3b-144">Глобальные статические функции метаданных</span><span class="sxs-lookup"><span data-stu-id="10e3b-144">Metadata Global Static Functions</span></span>](metadata-global-static-functions.md)  
  
 [<span data-ttu-id="10e3b-145">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="10e3b-145">Metadata Enumerations</span></span>](metadata-enumerations.md)  
  
 [<span data-ttu-id="10e3b-146">Структуры метаданных</span><span class="sxs-lookup"><span data-stu-id="10e3b-146">Metadata Structures</span></span>](metadata-structures.md)  
  
 [<span data-ttu-id="10e3b-147">Объединения метаданных</span><span class="sxs-lookup"><span data-stu-id="10e3b-147">Metadata Unions</span></span>](metadata-unions.md)
