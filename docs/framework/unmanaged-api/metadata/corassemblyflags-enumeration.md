---
description: Дополнительные сведения о перечислении Корассемблифлагс
title: Перечисление CorAssemblyFlags
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
ms.openlocfilehash: bd74534b1f607eea15f1d8615f66723428ddae3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678493"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="98f63-103">Перечисление CorAssemblyFlags</span><span class="sxs-lookup"><span data-stu-id="98f63-103">CorAssemblyFlags Enumeration</span></span>

<span data-ttu-id="98f63-104">Содержит значения, которые описывают метаданные, применяемые к компиляции сборки.</span><span class="sxs-lookup"><span data-stu-id="98f63-104">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98f63-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="98f63-105">Syntax</span></span>  
  
```cpp  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="98f63-106">Члены</span><span class="sxs-lookup"><span data-stu-id="98f63-106">Members</span></span>  
  
|<span data-ttu-id="98f63-107">Член</span><span class="sxs-lookup"><span data-stu-id="98f63-107">Member</span></span>|<span data-ttu-id="98f63-108">Описание</span><span class="sxs-lookup"><span data-stu-id="98f63-108">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="98f63-109">Указывает, что ссылка на сборку содержит полный, нехэшированный открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="98f63-109">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="98f63-110">Указывает, что архитектура процессора не определена.</span><span class="sxs-lookup"><span data-stu-id="98f63-110">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="98f63-111">Указывает, что архитектура процессора нейтральна (формат PE32).</span><span class="sxs-lookup"><span data-stu-id="98f63-111">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="98f63-112">Указывает, что архитектура процессора — x86 (формат PE32).</span><span class="sxs-lookup"><span data-stu-id="98f63-112">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="98f63-113">Указывает, что архитектура процессора — Itanium (формат PE32 +).</span><span class="sxs-lookup"><span data-stu-id="98f63-113">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="98f63-114">Указывает, что архитектура процессора — это AMD x64 (формат PE32 +).</span><span class="sxs-lookup"><span data-stu-id="98f63-114">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="98f63-115">Указывает, что архитектура процессора — ARM (формат PE32).</span><span class="sxs-lookup"><span data-stu-id="98f63-115">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="98f63-116">Указывает, что сборка является ссылочной сборкой; то есть он применяется к любой архитектуре, но не может работать в любой архитектуре.</span><span class="sxs-lookup"><span data-stu-id="98f63-116">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="98f63-117">Таким образом, флаг будет таким же, как и `afPA_Mask` .</span><span class="sxs-lookup"><span data-stu-id="98f63-117">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="98f63-118">Указывает, что флаги архитектуры процессора должны распространяться на `AssemblyRef` запись.</span><span class="sxs-lookup"><span data-stu-id="98f63-118">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="98f63-119">Маска, описывающая архитектуру процессора.</span><span class="sxs-lookup"><span data-stu-id="98f63-119">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="98f63-120">Указывает, что включено описание архитектуры процессора.</span><span class="sxs-lookup"><span data-stu-id="98f63-120">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="98f63-121">Указывает число смещений в флагах архитектуры процессора в индекс и из него.</span><span class="sxs-lookup"><span data-stu-id="98f63-121">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="98f63-122">Указывает соответствующее значение из <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> объекта <xref:System.Diagnostics.DebuggableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="98f63-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="98f63-123">Указывает соответствующее значение из <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> объекта <xref:System.Diagnostics.DebuggableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="98f63-123">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="98f63-124">Указывает, что сборка может быть перенацелена во время выполнения в сборку из другого издателя.</span><span class="sxs-lookup"><span data-stu-id="98f63-124">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="98f63-125">Маска, описывающая тип содержимого.</span><span class="sxs-lookup"><span data-stu-id="98f63-125">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="98f63-126">Указывает тип содержимого по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="98f63-126">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="98f63-127">Указывает тип содержимого среда выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="98f63-127">Indicates the Windows Runtime content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98f63-128">Требования</span><span class="sxs-lookup"><span data-stu-id="98f63-128">Requirements</span></span>  

 <span data-ttu-id="98f63-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98f63-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98f63-130">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="98f63-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="98f63-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98f63-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98f63-132">См. также</span><span class="sxs-lookup"><span data-stu-id="98f63-132">See also</span></span>

- [<span data-ttu-id="98f63-133">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="98f63-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
