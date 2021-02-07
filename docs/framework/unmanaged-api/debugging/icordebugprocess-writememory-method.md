---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: WriteMemory'
title: Метод ICorDebugProcess::WriteMemory
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
ms.openlocfilehash: 6ea48aff2e1ea812d851a228976b458f58a60e14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746629"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="be3cd-103">Метод ICorDebugProcess::WriteMemory</span><span class="sxs-lookup"><span data-stu-id="be3cd-103">ICorDebugProcess::WriteMemory Method</span></span>

<span data-ttu-id="be3cd-104">Записывает данные в область памяти в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="be3cd-104">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be3cd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="be3cd-105">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be3cd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="be3cd-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="be3cd-107">окне `CORDB_ADDRESS` Значение, являющееся базовым адресом области памяти, в которую записываются данные.</span><span class="sxs-lookup"><span data-stu-id="be3cd-107">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="be3cd-108">Перед передачей данных система проверяет, что область памяти указанного размера, начиная с базового адреса, доступна для записи.</span><span class="sxs-lookup"><span data-stu-id="be3cd-108">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="be3cd-109">Если он недоступен, метод завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="be3cd-109">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="be3cd-110">окне Число байтов, записываемых в область памяти.</span><span class="sxs-lookup"><span data-stu-id="be3cd-110">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="be3cd-111">окне Буфер, содержащий записываемые данные.</span><span class="sxs-lookup"><span data-stu-id="be3cd-111">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="be3cd-112">заполняет Указатель на переменную, которая получает число байтов, записанных в область памяти в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="be3cd-112">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="be3cd-113">Если `written` аргумент имеет значение null, этот параметр игнорируется.</span><span class="sxs-lookup"><span data-stu-id="be3cd-113">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be3cd-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="be3cd-114">Remarks</span></span>  

 <span data-ttu-id="be3cd-115">Данные автоматически записываются за любые точки останова.</span><span class="sxs-lookup"><span data-stu-id="be3cd-115">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="be3cd-116">В платформа .NET Framework версии 2,0 отладчики машинного кода не должны использовать этот метод для вставки точек останова в поток инструкций.</span><span class="sxs-lookup"><span data-stu-id="be3cd-116">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="be3cd-117">Вместо этого используйте [ICorDebugProcess2:: сетунманажедбреакпоинт](icordebugprocess2-setunmanagedbreakpoint-method.md) .</span><span class="sxs-lookup"><span data-stu-id="be3cd-117">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="be3cd-118">`WriteMemory`Метод следует использовать только за пределами управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="be3cd-118">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="be3cd-119">Этот метод может повредить среду выполнения при неправильном использовании.</span><span class="sxs-lookup"><span data-stu-id="be3cd-119">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be3cd-120">Требования</span><span class="sxs-lookup"><span data-stu-id="be3cd-120">Requirements</span></span>  

 <span data-ttu-id="be3cd-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be3cd-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be3cd-122">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be3cd-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be3cd-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be3cd-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be3cd-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be3cd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
