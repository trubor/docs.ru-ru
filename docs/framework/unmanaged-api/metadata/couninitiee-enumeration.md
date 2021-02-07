---
description: Дополнительные сведения о перечислении КАУНИНИТИИ
title: Перечисление COUNINITIEE
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
ms.openlocfilehash: 893ab96851e9c762a888f3c4cac98b486a0b4614
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707238"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="444ae-103">Перечисление COUNINITIEE</span><span class="sxs-lookup"><span data-stu-id="444ae-103">COUNINITIEE Enumeration</span></span>

<span data-ttu-id="444ae-104">Указывает константы, используемые [CoUninitializeEE](../hosting/couninitializeee-function.md) при инициализации среды CLR.</span><span class="sxs-lookup"><span data-stu-id="444ae-104">Specifies constants used by [CoUninitializeEE](../hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="444ae-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="444ae-105">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="444ae-106">Члены</span><span class="sxs-lookup"><span data-stu-id="444ae-106">Members</span></span>  
  
|<span data-ttu-id="444ae-107">Член</span><span class="sxs-lookup"><span data-stu-id="444ae-107">Member</span></span>|<span data-ttu-id="444ae-108">Описание</span><span class="sxs-lookup"><span data-stu-id="444ae-108">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="444ae-109">Указывает режим деинициализации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="444ae-109">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="444ae-110">Указывает режим отмены инициализации для выгрузки сборки.</span><span class="sxs-lookup"><span data-stu-id="444ae-110">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="444ae-111">Требования</span><span class="sxs-lookup"><span data-stu-id="444ae-111">Requirements</span></span>  

 <span data-ttu-id="444ae-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="444ae-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="444ae-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="444ae-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="444ae-114">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="444ae-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="444ae-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="444ae-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="444ae-116">См. также</span><span class="sxs-lookup"><span data-stu-id="444ae-116">See also</span></span>

- [<span data-ttu-id="444ae-117">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="444ae-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
