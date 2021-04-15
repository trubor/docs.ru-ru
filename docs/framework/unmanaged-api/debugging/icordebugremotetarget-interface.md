---
description: 'Дополнительные сведения о: интерфейс ICorDebugRemoteTarget'
title: Интерфейс ICorDebugRemoteTarget
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
ms.openlocfilehash: a14dc9d94d83a662d996ebb027e2e6ca3ef62c03
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494055"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="73b95-103">Интерфейс ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="73b95-103">ICorDebugRemoteTarget Interface</span></span>

<span data-ttu-id="73b95-104">Предоставляет методы, позволяющие разработчикам выполнять отладку приложений на основе Silverlight в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="73b95-104">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73b95-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="73b95-105">Syntax</span></span>  
  
```cpp  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="73b95-106">Методы</span><span class="sxs-lookup"><span data-stu-id="73b95-106">Methods</span></span>  
  
|<span data-ttu-id="73b95-107">Метод</span><span class="sxs-lookup"><span data-stu-id="73b95-107">Method</span></span>|<span data-ttu-id="73b95-108">Описание</span><span class="sxs-lookup"><span data-stu-id="73b95-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73b95-109">Метод ICorDebugRemoteTarget::GetHostName</span><span class="sxs-lookup"><span data-stu-id="73b95-109">ICorDebugRemoteTarget::GetHostName Method</span></span>](icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="73b95-110">Возвращает имя узла или IP-адрес удаленного компьютера.</span><span class="sxs-lookup"><span data-stu-id="73b95-110">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73b95-111">Комментарии</span><span class="sxs-lookup"><span data-stu-id="73b95-111">Remarks</span></span>  

 <span data-ttu-id="73b95-112">Отладка в смешанном режиме (управляемый и машинный код) не поддерживается на платформах, отличных от x86 (например, IA-64 и AMD64).</span><span class="sxs-lookup"><span data-stu-id="73b95-112">Mixed-mode (that is, managed and native code) debugging is not supported on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73b95-113">Требования</span><span class="sxs-lookup"><span data-stu-id="73b95-113">Requirements</span></span>  

 <span data-ttu-id="73b95-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73b95-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73b95-115">**Заголовок:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="73b95-115">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="73b95-116">**Библиотека:** : коргуидс. lib</span><span class="sxs-lookup"><span data-stu-id="73b95-116">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="73b95-117">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="73b95-117">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73b95-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="73b95-118">See also</span></span>

- [<span data-ttu-id="73b95-119">Интерфейс ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="73b95-119">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="73b95-120">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="73b95-120">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="73b95-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="73b95-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
