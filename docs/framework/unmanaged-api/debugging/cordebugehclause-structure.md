---
description: 'Дополнительные сведения о: структура Кордебужехклаусе'
title: Структура CorDebugEHClause
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
ms.openlocfilehash: ecb00e2a110719ab82de32fb1f1c861e2033a528
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801674"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="3c26e-103">Структура CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="3c26e-103">CorDebugEHClause Structure</span></span>

<span data-ttu-id="3c26e-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="3c26e-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3c26e-105">Представляет предложение обработки исключений для данного фрагмента кода промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="3c26e-105">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c26e-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3c26e-106">Syntax</span></span>  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a><span data-ttu-id="3c26e-107">Члены</span><span class="sxs-lookup"><span data-stu-id="3c26e-107">Members</span></span>  
  
|<span data-ttu-id="3c26e-108">Член</span><span class="sxs-lookup"><span data-stu-id="3c26e-108">Member</span></span>|<span data-ttu-id="3c26e-109">Описание</span><span class="sxs-lookup"><span data-stu-id="3c26e-109">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="3c26e-110">Битовое поле, описывающее информацию об исключениях в предложении обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="3c26e-110">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="3c26e-111">Дополнительные сведения см. в разделе «Примечания».</span><span class="sxs-lookup"><span data-stu-id="3c26e-111">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="3c26e-112">Смещение блока `try` в байтах от начала тела метода.</span><span class="sxs-lookup"><span data-stu-id="3c26e-112">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="3c26e-113">Длина блока `try` в байтах.</span><span class="sxs-lookup"><span data-stu-id="3c26e-113">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="3c26e-114">Расположение обработчика для этого блока `try`.</span><span class="sxs-lookup"><span data-stu-id="3c26e-114">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="3c26e-115">Размер кода обработчика в байтах.</span><span class="sxs-lookup"><span data-stu-id="3c26e-115">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="3c26e-116">Токен метаданных для обработчика исключений на основе типа.</span><span class="sxs-lookup"><span data-stu-id="3c26e-116">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="3c26e-117">Смещение в байтах от начала тела метода для обработчика исключений на основе фильтра.</span><span class="sxs-lookup"><span data-stu-id="3c26e-117">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c26e-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="3c26e-118">Remarks</span></span>  

 <span data-ttu-id="3c26e-119">Массив `CoreDebugEHClause` значений возвращается методом [GetEHClauses](icordebugilcode-getehclauses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3c26e-119">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="3c26e-120">Информация о предложении обработки исключений определяется спецификацией CLI.</span><span class="sxs-lookup"><span data-stu-id="3c26e-120">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="3c26e-121">Дополнительные сведения см. в разделе [Standard ECMA-355: Common Language Infrastructure (CLI), 6-й выпуск](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="3c26e-121">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="3c26e-122">Поле `flags` может содержать следующие флаги.</span><span class="sxs-lookup"><span data-stu-id="3c26e-122">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="3c26e-123">Обратите внимание, что они не определены в CorDebug.idl или CorDebug.h.</span><span class="sxs-lookup"><span data-stu-id="3c26e-123">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="3c26e-124">Флаг</span><span class="sxs-lookup"><span data-stu-id="3c26e-124">Flag</span></span>|<span data-ttu-id="3c26e-125">Значение</span><span class="sxs-lookup"><span data-stu-id="3c26e-125">Value</span></span>|<span data-ttu-id="3c26e-126">Описание</span><span class="sxs-lookup"><span data-stu-id="3c26e-126">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="3c26e-127">0x00000000</span><span class="sxs-lookup"><span data-stu-id="3c26e-127">0x00000000</span></span>|<span data-ttu-id="3c26e-128">Введенное предложение исключений.</span><span class="sxs-lookup"><span data-stu-id="3c26e-128">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="3c26e-129">0x00000001</span><span class="sxs-lookup"><span data-stu-id="3c26e-129">0x00000001</span></span>|<span data-ttu-id="3c26e-130">Фильтр исключений и предложение обработчика.</span><span class="sxs-lookup"><span data-stu-id="3c26e-130">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="3c26e-131">0x00000002</span><span class="sxs-lookup"><span data-stu-id="3c26e-131">0x00000002</span></span>|<span data-ttu-id="3c26e-132">Предложение `finally`.</span><span class="sxs-lookup"><span data-stu-id="3c26e-132">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="3c26e-133">0x00000004</span><span class="sxs-lookup"><span data-stu-id="3c26e-133">0x00000004</span></span>|<span data-ttu-id="3c26e-134">Неправильное предложение (предложение `finally`, которое вызывается только при возникновении исключения).</span><span class="sxs-lookup"><span data-stu-id="3c26e-134">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c26e-135">Требования</span><span class="sxs-lookup"><span data-stu-id="3c26e-135">Requirements</span></span>  

 <span data-ttu-id="3c26e-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c26e-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c26e-137">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c26e-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c26e-138">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c26e-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c26e-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c26e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c26e-140">См. также</span><span class="sxs-lookup"><span data-stu-id="3c26e-140">See also</span></span>

- [<span data-ttu-id="3c26e-141">Метод GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="3c26e-141">GetEHClauses Method</span></span>](icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="3c26e-142">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="3c26e-142">Debugging Structures</span></span>](debugging-structures.md)
