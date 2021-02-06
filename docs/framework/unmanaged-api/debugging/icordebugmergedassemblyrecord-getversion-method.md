---
description: 'Дополнительные сведения о методе: Икордебугмержедассемблирекорд:: метода Version'
title: Метод ICorDebugMergedAssemblyRecord::GetVersion
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 0e87e2bbb1207ebd1eb5775b7f52d5689b4e8727
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650343"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="9384a-103">Метод ICorDebugMergedAssemblyRecord::GetVersion</span><span class="sxs-lookup"><span data-stu-id="9384a-103">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>

<span data-ttu-id="9384a-104">Возвращает сведения о версии сборки.</span><span class="sxs-lookup"><span data-stu-id="9384a-104">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9384a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9384a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9384a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9384a-106">Parameters</span></span>  

 `pMajor`  
 <span data-ttu-id="9384a-107">[out] Указатель на основной номер версии.</span><span class="sxs-lookup"><span data-stu-id="9384a-107">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="9384a-108">[out] Указатель на дополнительный номер версии.</span><span class="sxs-lookup"><span data-stu-id="9384a-108">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="9384a-109">[out] Указатель на номер сборки.</span><span class="sxs-lookup"><span data-stu-id="9384a-109">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="9384a-110">[out] Указатель на номер редакции.</span><span class="sxs-lookup"><span data-stu-id="9384a-110">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9384a-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="9384a-111">Remarks</span></span>  

 <span data-ttu-id="9384a-112">Сведения о версии сборки см в разделе, посвященном классу <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="9384a-112">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9384a-113">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="9384a-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9384a-114">Требования</span><span class="sxs-lookup"><span data-stu-id="9384a-114">Requirements</span></span>  

 <span data-ttu-id="9384a-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9384a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9384a-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9384a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9384a-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9384a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9384a-118">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9384a-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9384a-119">См. также</span><span class="sxs-lookup"><span data-stu-id="9384a-119">See also</span></span>

- [<span data-ttu-id="9384a-120">Интерфейс ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="9384a-120">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="9384a-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="9384a-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
