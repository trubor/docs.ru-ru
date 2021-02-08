---
description: 'Дополнительные сведения о: интерфейс метод icordebugmodule3'
title: Интерфейс ICorDebugModule3
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
ms.openlocfilehash: 5b47cffb267ab97de2cd225aca2998962ba66d99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790767"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="6fff0-103">Интерфейс ICorDebugModule3</span><span class="sxs-lookup"><span data-stu-id="6fff0-103">ICorDebugModule3 Interface</span></span>

<span data-ttu-id="6fff0-104">Создает средство чтения символов для динамического модуля.</span><span class="sxs-lookup"><span data-stu-id="6fff0-104">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fff0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6fff0-105">Syntax</span></span>  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6fff0-106">Методы</span><span class="sxs-lookup"><span data-stu-id="6fff0-106">Methods</span></span>  
  
|<span data-ttu-id="6fff0-107">Метод</span><span class="sxs-lookup"><span data-stu-id="6fff0-107">Method</span></span>|<span data-ttu-id="6fff0-108">Описание</span><span class="sxs-lookup"><span data-stu-id="6fff0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6fff0-109">Метод ICorDebugModule3::CreateReaderForInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="6fff0-109">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="6fff0-110">Создает средство чтения символов (обычно [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md)) для динамического модуля.</span><span class="sxs-lookup"><span data-stu-id="6fff0-110">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fff0-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="6fff0-111">Remarks</span></span>  

 <span data-ttu-id="6fff0-112">Этот интерфейс логически расширяет интерфейсы "ICorDebugModule" и "ICorDebugModule2".</span><span class="sxs-lookup"><span data-stu-id="6fff0-112">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fff0-113">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="6fff0-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fff0-114">Требования</span><span class="sxs-lookup"><span data-stu-id="6fff0-114">Requirements</span></span>  

 <span data-ttu-id="6fff0-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fff0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fff0-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fff0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fff0-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fff0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fff0-118">**Платформа .NET Framework версии:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="6fff0-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6fff0-119">См. также</span><span class="sxs-lookup"><span data-stu-id="6fff0-119">See also</span></span>

- [<span data-ttu-id="6fff0-120">Интерфейс ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="6fff0-120">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="6fff0-121">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="6fff0-121">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="6fff0-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6fff0-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
