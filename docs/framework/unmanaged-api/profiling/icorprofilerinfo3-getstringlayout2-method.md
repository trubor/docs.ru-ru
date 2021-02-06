---
description: 'Дополнительные сведения о методе: ICorProfilerInfo3:: GetStringLayout2'
title: Метод ICorProfilerInfo3::GetStringLayout2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: 398d06dc62245e6a2201feacb62ebbb1e4839ccb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646677"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="f685d-103">Метод ICorProfilerInfo3::GetStringLayout2</span><span class="sxs-lookup"><span data-stu-id="f685d-103">ICorProfilerInfo3::GetStringLayout2 Method</span></span>

<span data-ttu-id="f685d-104">Получает сведения о структуре строкового объекта.</span><span class="sxs-lookup"><span data-stu-id="f685d-104">Gets information about the layout of a string object.</span></span> <span data-ttu-id="f685d-105">Этот метод заменяет метод [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f685d-105">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f685d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f685d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f685d-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="f685d-107">Parameters</span></span>  

 `pStringLengthOffset`  
 <span data-ttu-id="f685d-108">заполняет Указатель на смещение расположения относительно `ObjectID` указателя, в котором хранится длина строки.</span><span class="sxs-lookup"><span data-stu-id="f685d-108">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="f685d-109">Длина хранится в виде `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="f685d-109">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="f685d-110">заполняет Указатель на смещение буфера относительно `ObjectID` указателя, в котором хранится строка расширенных символов.</span><span class="sxs-lookup"><span data-stu-id="f685d-110">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f685d-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f685d-111">Remarks</span></span>  

 <span data-ttu-id="f685d-112">Строки могут завершаться или не заканчиваться нулем.</span><span class="sxs-lookup"><span data-stu-id="f685d-112">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f685d-113">Требования</span><span class="sxs-lookup"><span data-stu-id="f685d-113">Requirements</span></span>  

 <span data-ttu-id="f685d-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f685d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f685d-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f685d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f685d-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f685d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f685d-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f685d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f685d-118">См. также</span><span class="sxs-lookup"><span data-stu-id="f685d-118">See also</span></span>

- [<span data-ttu-id="f685d-119">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="f685d-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f685d-120">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="f685d-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
