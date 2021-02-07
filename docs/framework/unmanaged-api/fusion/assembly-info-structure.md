---
description: 'Дополнительные сведения: структура ASSEMBLY_INFO'
title: Структура ASSEMBLY_INFO
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
ms.openlocfilehash: c28d9abf13769197b62705d51bbcf4f099616bbc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761291"
---
# <a name="assembly_info-structure"></a><span data-ttu-id="e2af1-103">Структура ASSEMBLY_INFO</span><span class="sxs-lookup"><span data-stu-id="e2af1-103">ASSEMBLY_INFO Structure</span></span>

<span data-ttu-id="e2af1-104">Содержит сведения о сборке, зарегистрированной в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="e2af1-104">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2af1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e2af1-105">Syntax</span></span>  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="e2af1-106">Члены</span><span class="sxs-lookup"><span data-stu-id="e2af1-106">Members</span></span>  
  
|<span data-ttu-id="e2af1-107">Член</span><span class="sxs-lookup"><span data-stu-id="e2af1-107">Member</span></span>|<span data-ttu-id="e2af1-108">Описание</span><span class="sxs-lookup"><span data-stu-id="e2af1-108">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="e2af1-109">Размер структуры в байтах.</span><span class="sxs-lookup"><span data-stu-id="e2af1-109">The size, in bytes, of the structure.</span></span> <span data-ttu-id="e2af1-110">Это поле зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="e2af1-110">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="e2af1-111">Флаги, указывающие сведения об установке сборки.</span><span class="sxs-lookup"><span data-stu-id="e2af1-111">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="e2af1-112">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="e2af1-112">The following values are supported:</span></span><br /><br /> <span data-ttu-id="e2af1-113">— Значение ASSEMBLYINFO_FLAG_INSTALLED, указывающее, что сборка установлена.</span><span class="sxs-lookup"><span data-stu-id="e2af1-113">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="e2af1-114">Текущая версия платформа .NET Framework всегда задает `dwAssemblyFlags` это значение.</span><span class="sxs-lookup"><span data-stu-id="e2af1-114">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="e2af1-115">— Значение ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, указывающее, что сборка является резидентной полезной нагрузкой.</span><span class="sxs-lookup"><span data-stu-id="e2af1-115">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="e2af1-116">Текущая версия платформа .NET Framework никогда не задает `dwAssemblyFlags` это значение.</span><span class="sxs-lookup"><span data-stu-id="e2af1-116">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="e2af1-117">Общий размер файлов, содержащихся в сборке, в килобайтах.</span><span class="sxs-lookup"><span data-stu-id="e2af1-117">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="e2af1-118">Указатель на строковый буфер, содержащий текущий путь к файлу манифеста.</span><span class="sxs-lookup"><span data-stu-id="e2af1-118">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="e2af1-119">Путь должен заканчиваться нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="e2af1-119">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="e2af1-120">Количество расширенных символов, включая знак завершения null, `pszCurrentAssemblyPathBuf` содержащий.</span><span class="sxs-lookup"><span data-stu-id="e2af1-120">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2af1-121">Требования</span><span class="sxs-lookup"><span data-stu-id="e2af1-121">Requirements</span></span>  

 <span data-ttu-id="e2af1-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2af1-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2af1-123">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e2af1-123">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e2af1-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2af1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2af1-125">См. также</span><span class="sxs-lookup"><span data-stu-id="e2af1-125">See also</span></span>

- [<span data-ttu-id="e2af1-126">Структуры Fusion</span><span class="sxs-lookup"><span data-stu-id="e2af1-126">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="e2af1-127">Глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="e2af1-127">Global Assembly Cache</span></span>](../../app-domains/gac.md)
