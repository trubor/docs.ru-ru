---
description: 'Дополнительные сведения о: структура Кодечункинфо'
title: Структура CodeChunkInfo
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
ms.openlocfilehash: 017a9ee8c608d4efae98eb0a342a3371ef8ec310
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712354"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="41d07-103">Структура CodeChunkInfo</span><span class="sxs-lookup"><span data-stu-id="41d07-103">CodeChunkInfo Structure</span></span>

<span data-ttu-id="41d07-104">Представляет одинарный блок кода в памяти.</span><span class="sxs-lookup"><span data-stu-id="41d07-104">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41d07-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="41d07-105">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="41d07-106">Члены</span><span class="sxs-lookup"><span data-stu-id="41d07-106">Members</span></span>  
  
|<span data-ttu-id="41d07-107">Член</span><span class="sxs-lookup"><span data-stu-id="41d07-107">Member</span></span>|<span data-ttu-id="41d07-108">Описание</span><span class="sxs-lookup"><span data-stu-id="41d07-108">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="41d07-109">`CORDB_ADDRESS`Значение, указывающее начальный адрес фрагмента.</span><span class="sxs-lookup"><span data-stu-id="41d07-109">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="41d07-110">Размер блока в байтах.</span><span class="sxs-lookup"><span data-stu-id="41d07-110">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41d07-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="41d07-111">Remarks</span></span>  

 <span data-ttu-id="41d07-112">Единственный фрагмент кода — это область машинного кода, которая является частью объекта кода, например функции.</span><span class="sxs-lookup"><span data-stu-id="41d07-112">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41d07-113">Требования</span><span class="sxs-lookup"><span data-stu-id="41d07-113">Requirements</span></span>  

 <span data-ttu-id="41d07-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41d07-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41d07-115">**Заголовок:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="41d07-115">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="41d07-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41d07-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41d07-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41d07-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d07-118">См. также</span><span class="sxs-lookup"><span data-stu-id="41d07-118">See also</span></span>

- [<span data-ttu-id="41d07-119">Метод GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="41d07-119">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="41d07-120">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="41d07-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="41d07-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="41d07-121">Debugging</span></span>](index.md)
