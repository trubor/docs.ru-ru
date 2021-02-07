---
description: 'Дополнительные сведения о: структура ASSEMBLYMETADATA'
title: Структура ASSEMBLYMETADATA
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
ms.openlocfilehash: 6fc9c03bea3b1413cd3a8421746137e37d43bd90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678943"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="db478-103">Структура ASSEMBLYMETADATA</span><span class="sxs-lookup"><span data-stu-id="db478-103">ASSEMBLYMETADATA Structure</span></span>

<span data-ttu-id="db478-104">Содержит сведения о сборке, на которую имеется ссылка, включая ее версию и уровень поддержки языковых стандартов, процессоров и операционных систем.</span><span class="sxs-lookup"><span data-stu-id="db478-104">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db478-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="db478-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a><span data-ttu-id="db478-106">Члены</span><span class="sxs-lookup"><span data-stu-id="db478-106">Members</span></span>  
  
|<span data-ttu-id="db478-107">Член</span><span class="sxs-lookup"><span data-stu-id="db478-107">Member</span></span>|<span data-ttu-id="db478-108">Описание</span><span class="sxs-lookup"><span data-stu-id="db478-108">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="db478-109">Основной номер версии сборки, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="db478-109">The major version number of the referenced assembly.</span></span> <span data-ttu-id="db478-110">Это значение не может быть нулевым.</span><span class="sxs-lookup"><span data-stu-id="db478-110">This value cannot be zero.</span></span> <span data-ttu-id="db478-111">Если заданы все биты `usMajorVersion` , основной номер версии не указывается.</span><span class="sxs-lookup"><span data-stu-id="db478-111">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="db478-112">Дополнительный номер версии сборки, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="db478-112">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="db478-113">Это значение не может быть нулевым.</span><span class="sxs-lookup"><span data-stu-id="db478-113">This value cannot be zero.</span></span> <span data-ttu-id="db478-114">Если заданы все биты `usMinorVersion` , дополнительный номер версии не указывается.</span><span class="sxs-lookup"><span data-stu-id="db478-114">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="db478-115">Номер построения сборки, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="db478-115">The build number of the referenced assembly.</span></span> <span data-ttu-id="db478-116">Это значение не может быть нулевым.</span><span class="sxs-lookup"><span data-stu-id="db478-116">This value cannot be zero.</span></span> <span data-ttu-id="db478-117">Если заданы все биты `usBuildNumber` , номер сборки не указывается.</span><span class="sxs-lookup"><span data-stu-id="db478-117">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="db478-118">Номер редакции сборки, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="db478-118">The revision number of the referenced assembly.</span></span> <span data-ttu-id="db478-119">Это значение не может быть нулевым.</span><span class="sxs-lookup"><span data-stu-id="db478-119">This value cannot be zero.</span></span> <span data-ttu-id="db478-120">Если заданы все биты `usRevisionNumber` , номер редакции не указывается.</span><span class="sxs-lookup"><span data-stu-id="db478-120">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="db478-121">Список имен языковых стандартов, которым соответствует спецификация RFC1766, разделенные точкой с запятой, с указанием языковых стандартов, поддерживаемых сборкой, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="db478-121">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="db478-122">Значение NULL указывает на независимость от языкового стандарта.</span><span class="sxs-lookup"><span data-stu-id="db478-122">A null value indicates locale independence.</span></span> <span data-ttu-id="db478-123">**Примечание.**  В платформа .NET Framework версии 1,0 нельзя указать более одного языкового стандарта.</span><span class="sxs-lookup"><span data-stu-id="db478-123">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="db478-124">Размер в расширенных символах `szLocale` .</span><span class="sxs-lookup"><span data-stu-id="db478-124">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="db478-125">Массив идентификаторов, как определено в Winnt. h, для типов процессоров, поддерживаемых сборкой, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="db478-125">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="db478-126">Значение NULL указывает на независимость от процессора.</span><span class="sxs-lookup"><span data-stu-id="db478-126">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="db478-127">Длина массива `rdwProcessor`.</span><span class="sxs-lookup"><span data-stu-id="db478-127">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="db478-128">Массив экземпляров [OSInfo](osinfo-structure.md) , указывающих операционные системы, поддерживаемые сборкой, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="db478-128">An array of [OSINFO](osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="db478-129">Значение NULL указывает на независимость от операционной системы.</span><span class="sxs-lookup"><span data-stu-id="db478-129">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="db478-130">Длина массива `rOS`.</span><span class="sxs-lookup"><span data-stu-id="db478-130">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db478-131">Требования</span><span class="sxs-lookup"><span data-stu-id="db478-131">Requirements</span></span>  

 <span data-ttu-id="db478-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db478-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db478-133">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="db478-133">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db478-134">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db478-134">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db478-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db478-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db478-136">См. также</span><span class="sxs-lookup"><span data-stu-id="db478-136">See also</span></span>

- [<span data-ttu-id="db478-137">Структуры метаданных</span><span class="sxs-lookup"><span data-stu-id="db478-137">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="db478-138">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="db478-138">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="db478-139">Структура OSINFO</span><span class="sxs-lookup"><span data-stu-id="db478-139">OSINFO Structure</span></span>](osinfo-structure.md)
