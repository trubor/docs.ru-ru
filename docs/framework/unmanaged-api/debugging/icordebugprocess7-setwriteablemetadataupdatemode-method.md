---
description: 'Дополнительные сведения о методе: ICorDebugProcess7:: SetWriteableMetadataUpdateMode'
title: Метод ICorDebugProcess7::SetWriteableMetadataUpdateMode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
ms.openlocfilehash: 86ece68e160fbd61f44adcf495656c7b5d6b5153
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691267"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="b7e99-103">Метод ICorDebugProcess7::SetWriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="b7e99-103">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>

<span data-ttu-id="b7e99-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="b7e99-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b7e99-105">Настраивает порядок, согласно которому отладчик обрабатывает обновления находящихся в памяти метаданных в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="b7e99-105">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e99-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b7e99-106">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7e99-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="b7e99-107">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="b7e99-108">Значение перечисления [вритеаблеметадатаупдатемоде](writeablemetadataupdatemode-enumeration.md) , указывающее, являются ли обновления в памяти для метаданных в целевом процессе видимыми ( `WriteableMetadataUpdateMode::AlwaysShowUpdates` ) или невидимыми ( `WriteableMetadataUpdateMode::LegacyCompatPolicy` ) для отладчика.</span><span class="sxs-lookup"><span data-stu-id="b7e99-108">A [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7e99-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="b7e99-109">Remarks</span></span>  

 <span data-ttu-id="b7e99-110">Обновления для метаданных в целевом процессе могут поступать из режима "Изменить и продолжить", профилировщика или <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7e99-110">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7e99-111">Требования</span><span class="sxs-lookup"><span data-stu-id="b7e99-111">Requirements</span></span>  

 <span data-ttu-id="b7e99-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7e99-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7e99-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7e99-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7e99-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7e99-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7e99-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7e99-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e99-116">См. также</span><span class="sxs-lookup"><span data-stu-id="b7e99-116">See also</span></span>

- [<span data-ttu-id="b7e99-117">Интерфейс ICorDebugProcess7</span><span class="sxs-lookup"><span data-stu-id="b7e99-117">ICorDebugProcess7 Interface</span></span>](icordebugprocess7-interface.md)
- [<span data-ttu-id="b7e99-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b7e99-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
