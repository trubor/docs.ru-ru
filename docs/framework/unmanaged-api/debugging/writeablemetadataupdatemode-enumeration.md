---
description: Дополнительные сведения о перечислении Вритеаблеметадатаупдатемоде
title: Перечисление WriteableMetadataUpdateMode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
ms.openlocfilehash: b8136963e315c429643bd0ebf4bdb509d5173bec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800517"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="f0acf-103">Перечисление WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="f0acf-103">WriteableMetadataUpdateMode Enumeration</span></span>

<span data-ttu-id="f0acf-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="f0acf-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f0acf-105">Предоставляет значения, указывающие, будут ли видны в отладчике обновления копии метаданных в памяти.</span><span class="sxs-lookup"><span data-stu-id="f0acf-105">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0acf-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f0acf-106">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="f0acf-107">Члены</span><span class="sxs-lookup"><span data-stu-id="f0acf-107">Members</span></span>  
  
|<span data-ttu-id="f0acf-108">Имя участника</span><span class="sxs-lookup"><span data-stu-id="f0acf-108">Member name</span></span>|<span data-ttu-id="f0acf-109">Описание</span><span class="sxs-lookup"><span data-stu-id="f0acf-109">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="f0acf-110">Поддерживает совместимость с предыдущими версиями платформы .NET Framework, делая видимыми обновления находящихся в памяти метаданных.</span><span class="sxs-lookup"><span data-stu-id="f0acf-110">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="f0acf-111">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="f0acf-111">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="f0acf-112">Делает обновления находящихся в памяти метаданных видимыми в отладчике.</span><span class="sxs-lookup"><span data-stu-id="f0acf-112">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0acf-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="f0acf-113">Remarks</span></span>  

 <span data-ttu-id="f0acf-114">Член `WriteableMetadataUpdateMode` перечисления может быть передан методу [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) для управления тем, являются ли обновления в памяти в целевом процессе доступными для отладчика.</span><span class="sxs-lookup"><span data-stu-id="f0acf-114">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="f0acf-115">Параметр `LegacyCompatPolicy` обеспечивает такое же поведение, как и до версии 4.5.2 платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f0acf-115">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="f0acf-116">Чаще всего это означает, что метаданные из обновлений не видны.</span><span class="sxs-lookup"><span data-stu-id="f0acf-116">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="f0acf-117">В то же время вызовы ряда методов отладчика неявно вынуждают его делать обновления видимыми.</span><span class="sxs-lookup"><span data-stu-id="f0acf-117">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="f0acf-118">Например, если отладчик передает [ICorDebugILFrame:: жетлокалвариабле](icordebugilframe-getlocalvariable-method.md) индекс переменной, не найденной в исходных метаданных метода, все метаданные модуля обновляются до моментального снимка, соответствующего текущему состоянию процесса.</span><span class="sxs-lookup"><span data-stu-id="f0acf-118">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="f0acf-119">Другими словами, при наличии параметра `LegacyCompatPolicy` отладчик может не видеть вообще, видеть частично или видеть все доступные обновления метаданных в зависимости от того, как он использует другие части неуправляемого API отладки.</span><span class="sxs-lookup"><span data-stu-id="f0acf-119">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0acf-120">Требования</span><span class="sxs-lookup"><span data-stu-id="f0acf-120">Requirements</span></span>  

 <span data-ttu-id="f0acf-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0acf-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0acf-122">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0acf-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0acf-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0acf-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0acf-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0acf-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0acf-125">См. также</span><span class="sxs-lookup"><span data-stu-id="f0acf-125">See also</span></span>

- [<span data-ttu-id="f0acf-126">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="f0acf-126">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="f0acf-127">Метод SetWriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="f0acf-127">SetWriteableMetadataUpdateMode Method</span></span>](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
