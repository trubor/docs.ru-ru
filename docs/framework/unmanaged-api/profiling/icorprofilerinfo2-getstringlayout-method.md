---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: GetStringLayout'
title: Метод ICorProfilerInfo2::GetStringLayout
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
ms.openlocfilehash: 145d748d756fd30ef0522d1c516f8f63ca604545
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716371"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="e57f9-103">Метод ICorProfilerInfo2::GetStringLayout</span><span class="sxs-lookup"><span data-stu-id="e57f9-103">ICorProfilerInfo2::GetStringLayout Method</span></span>

<span data-ttu-id="e57f9-104">Получает сведения о структуре строкового объекта.</span><span class="sxs-lookup"><span data-stu-id="e57f9-104">Gets information about the layout of a string object.</span></span> <span data-ttu-id="e57f9-105">Этот метод является устаревшим в платформа .NET Framework 4 и заменяется методом [ICorProfilerInfo3:: GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e57f9-105">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e57f9-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e57f9-106">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e57f9-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="e57f9-107">Parameters</span></span>  

 `pBufferLengthOffset`  
 <span data-ttu-id="e57f9-108">заполняет Указатель на смещение расположения относительно `ObjectID` указателя, в котором хранится длина строки.</span><span class="sxs-lookup"><span data-stu-id="e57f9-108">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="e57f9-109">Длина хранится в виде `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="e57f9-109">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e57f9-110">Этот параметр возвращает длину самой строки, а не длину буфера.</span><span class="sxs-lookup"><span data-stu-id="e57f9-110">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="e57f9-111">Длина буфера больше недоступна.</span><span class="sxs-lookup"><span data-stu-id="e57f9-111">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="e57f9-112">заполняет Указатель на смещение расположения относительно `ObjectID` указателя, в котором хранится длина строки.</span><span class="sxs-lookup"><span data-stu-id="e57f9-112">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="e57f9-113">Длина хранится в виде `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="e57f9-113">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="e57f9-114">заполняет Указатель на смещение буфера относительно указателя, в `ObjectID` котором хранится строка расширенных символов.</span><span class="sxs-lookup"><span data-stu-id="e57f9-114">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e57f9-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="e57f9-115">Remarks</span></span>  

 <span data-ttu-id="e57f9-116">`GetStringLayout`Метод получает смещения, относящиеся к `ObjectID` указателю, для расположений, в которых хранятся следующие значения:</span><span class="sxs-lookup"><span data-stu-id="e57f9-116">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="e57f9-117">Длина буфера строки.</span><span class="sxs-lookup"><span data-stu-id="e57f9-117">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="e57f9-118">Длина самой строки.</span><span class="sxs-lookup"><span data-stu-id="e57f9-118">The length of the string itself.</span></span>  
  
- <span data-ttu-id="e57f9-119">Буфер, содержащий фактическую строку расширенных символов.</span><span class="sxs-lookup"><span data-stu-id="e57f9-119">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="e57f9-120">Строки могут завершаться нулем.</span><span class="sxs-lookup"><span data-stu-id="e57f9-120">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e57f9-121">Требования</span><span class="sxs-lookup"><span data-stu-id="e57f9-121">Requirements</span></span>  

 <span data-ttu-id="e57f9-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e57f9-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e57f9-123">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e57f9-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e57f9-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e57f9-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e57f9-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e57f9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e57f9-126">См. также</span><span class="sxs-lookup"><span data-stu-id="e57f9-126">See also</span></span>

- [<span data-ttu-id="e57f9-127">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="e57f9-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="e57f9-128">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="e57f9-128">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
