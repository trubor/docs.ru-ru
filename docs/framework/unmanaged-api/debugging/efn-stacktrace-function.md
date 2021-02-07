---
description: Дополнительные сведения о функции _EFN_StackTrace
title: Функция _EFN_StackTrace
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
ms.openlocfilehash: 6092d0793967cc422e30342783ab4dfd70b33de9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738290"
---
# <a name="_efn_stacktrace-function"></a><span data-ttu-id="21d86-103">\_ЕФН \_ StackTrace, функция</span><span class="sxs-lookup"><span data-stu-id="21d86-103">\_EFN\_StackTrace Function</span></span>

<span data-ttu-id="21d86-104">Предоставляет текстовое представление трассировки управляемого стека и массив записей `CONTEXT`, по одной для каждого перехода между неуправляемым и управляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="21d86-104">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21d86-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="21d86-105">Syntax</span></span>  
  
```cpp  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21d86-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="21d86-106">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="21d86-107">окне Отлаживаемый клиент.</span><span class="sxs-lookup"><span data-stu-id="21d86-107">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="21d86-108">заполняет Текстовое представление трассировки стека.</span><span class="sxs-lookup"><span data-stu-id="21d86-108">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="21d86-109">заполняет Указатель на число символов в `wszTextOut` .</span><span class="sxs-lookup"><span data-stu-id="21d86-109">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="21d86-110">заполняет Массив контекстов перехода.</span><span class="sxs-lookup"><span data-stu-id="21d86-110">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="21d86-111">заполняет Указатель на число контекстов перехода в массиве.</span><span class="sxs-lookup"><span data-stu-id="21d86-111">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="21d86-112">окне Размер структуры контекста.</span><span class="sxs-lookup"><span data-stu-id="21d86-112">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="21d86-113">окне Задайте значение 0 или SOS_STACKTRACE_SHOWADDRESSES (0x01) для отображения регистра EBP и указателя ввода стека (ESP) перед каждой `module!functionname` строкой.</span><span class="sxs-lookup"><span data-stu-id="21d86-113">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21d86-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="21d86-114">Remarks</span></span>  

 <span data-ttu-id="21d86-115">`_EFN_StackTrace`Структуру можно вызвать из программного интерфейса WinDbg.</span><span class="sxs-lookup"><span data-stu-id="21d86-115">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="21d86-116">Параметры используются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="21d86-116">Parameters are used as follows:</span></span>  
  
- <span data-ttu-id="21d86-117">Если значение `wszTextOut` равно NULL и не равно `puiTextLength` null, функция возвращает длину строки в `puiTextLength` .</span><span class="sxs-lookup"><span data-stu-id="21d86-117">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
- <span data-ttu-id="21d86-118">Если `wszTextOut` параметр не равен null, функция сохраняет текст в `wszTextOut` расположении, указанном параметром `puiTextLength` .</span><span class="sxs-lookup"><span data-stu-id="21d86-118">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="21d86-119">Он возвращает значение, если в буфере достаточно места, или возвращает E_OUTOFMEMORY, если буфер недостаточно длинный.</span><span class="sxs-lookup"><span data-stu-id="21d86-119">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
- <span data-ttu-id="21d86-120">Часть перехода функции игнорируется, если `pTransitionContexts` и `puiTransitionContextCount` равны NULL.</span><span class="sxs-lookup"><span data-stu-id="21d86-120">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="21d86-121">В этом случае функция предоставляет вызывающим объектам текстовые выходные данные только имен функций.</span><span class="sxs-lookup"><span data-stu-id="21d86-121">In this case, the function provides callers with text output of only the function names.</span></span>  
  
- <span data-ttu-id="21d86-122">Если `pTransitionContexts` параметр имеет значение NULL и не равен `puiTransitionContextCount` null, функция возвращает необходимое число контекстных записей в `puiTransitionContextCount` .</span><span class="sxs-lookup"><span data-stu-id="21d86-122">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
- <span data-ttu-id="21d86-123">Если `pTransitionContexts` параметр не равен null, функция обрабатывает ее как массив структур с длиной `puiTransitionContextCount` .</span><span class="sxs-lookup"><span data-stu-id="21d86-123">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="21d86-124">Размер структуры определяется параметром `uiSizeOfContext` и должен быть размером [симплеконтекст](stacktrace-simplecontext-structure.md) или `CONTEXT` для архитектуры.</span><span class="sxs-lookup"><span data-stu-id="21d86-124">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
- <span data-ttu-id="21d86-125">`wszTextOut` записывается в следующем формате:</span><span class="sxs-lookup"><span data-stu-id="21d86-125">`wszTextOut` is written in the following format:</span></span>  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- <span data-ttu-id="21d86-126">Если смещение в шестнадцатеричном формате имеет значение 0x0, смещение не записывается.</span><span class="sxs-lookup"><span data-stu-id="21d86-126">If the offset in hex is 0x0, no offset is written.</span></span>  
  
- <span data-ttu-id="21d86-127">Если в текущем потоке нет управляемого кода, функция возвращает SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="21d86-127">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
- <span data-ttu-id="21d86-128">`Flags`Параметр имеет значение 0 или SOS_STACKTRACE_SHOWADDRESSES, чтобы видеть ebp и ESP в начале каждой `module!functionname` строки.</span><span class="sxs-lookup"><span data-stu-id="21d86-128">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="21d86-129">По умолчанию это 0.</span><span class="sxs-lookup"><span data-stu-id="21d86-129">By default, it is 0.</span></span>  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="21d86-130">Требования</span><span class="sxs-lookup"><span data-stu-id="21d86-130">Requirements</span></span>  

 <span data-ttu-id="21d86-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21d86-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21d86-132">**Заголовок:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="21d86-132">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="21d86-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21d86-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21d86-134">См. также</span><span class="sxs-lookup"><span data-stu-id="21d86-134">See also</span></span>

- [<span data-ttu-id="21d86-135">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="21d86-135">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
