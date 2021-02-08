---
description: 'Дополнительные сведения о: структура OSINFO'
title: Структура OSINFO
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: 5027ef5cf4137aa1e781134b325407e1251fdd31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799113"
---
# <a name="osinfo-structure"></a><span data-ttu-id="60489-103">Структура OSINFO</span><span class="sxs-lookup"><span data-stu-id="60489-103">OSINFO Structure</span></span>

<span data-ttu-id="60489-104">Содержит сведения об операционной системе для сборки или модуля.</span><span class="sxs-lookup"><span data-stu-id="60489-104">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60489-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="60489-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="60489-106">Члены</span><span class="sxs-lookup"><span data-stu-id="60489-106">Members</span></span>  
  
|<span data-ttu-id="60489-107">Член</span><span class="sxs-lookup"><span data-stu-id="60489-107">Member</span></span>|<span data-ttu-id="60489-108">Описание</span><span class="sxs-lookup"><span data-stu-id="60489-108">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="60489-109">Одно из значений идентификатора, определяемое функцией платформы Microsoft Windows `GetVersionEx` .</span><span class="sxs-lookup"><span data-stu-id="60489-109">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="60489-110">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="60489-110">The following values are supported:</span></span><br /><br /> <span data-ttu-id="60489-111">-VER_PLATFORM_WIN32s или символ 0x0000, чтобы указать Microsoft Windows 3,1.</span><span class="sxs-lookup"><span data-stu-id="60489-111">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="60489-112">-VER_PLATFORM_WIN32_WINDOWS или 0x0001, чтобы указать для Windows 95, Windows 98 или операционных систем по убыванию.</span><span class="sxs-lookup"><span data-stu-id="60489-112">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="60489-113">-VER_PLATFORM_WIN32_NT или 0x0002, чтобы указать Windows NT или операционные системы в обратном порядке.</span><span class="sxs-lookup"><span data-stu-id="60489-113">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="60489-114">Основной номер версии операционной системы или значение NULL для указания любой версии.</span><span class="sxs-lookup"><span data-stu-id="60489-114">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="60489-115">Дополнительный номер версии операционной системы или значение NULL для указания любой версии.</span><span class="sxs-lookup"><span data-stu-id="60489-115">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60489-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="60489-116">Remarks</span></span>  

 <span data-ttu-id="60489-117">`OSINFO` основывается на `OSVERSIONINFOEX` структуре, используемой в вызовах функции платформы Microsoft Windows `GetVersionEx` .</span><span class="sxs-lookup"><span data-stu-id="60489-117">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="60489-118">Эта структура используется структурой ASSEMBLYMETADATA для указания поддержки операционной системы.</span><span class="sxs-lookup"><span data-stu-id="60489-118">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60489-119">Требования</span><span class="sxs-lookup"><span data-stu-id="60489-119">Requirements</span></span>  

 <span data-ttu-id="60489-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60489-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60489-121">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="60489-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60489-122">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="60489-122">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60489-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60489-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60489-124">См. также</span><span class="sxs-lookup"><span data-stu-id="60489-124">See also</span></span>

- [<span data-ttu-id="60489-125">Структуры метаданных</span><span class="sxs-lookup"><span data-stu-id="60489-125">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="60489-126">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="60489-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
