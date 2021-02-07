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
ms.openlocfilehash: c6567ebb76c7a3c415c9978dc50941cb0b8985a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717879"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="b7dd4-103">Интерфейс ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="b7dd4-103">ICorDebugRemoteTarget Interface</span></span>

<span data-ttu-id="b7dd4-104">Предоставляет методы, позволяющие разработчикам выполнять отладку приложений на основе Silverlight в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="b7dd4-104">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7dd4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b7dd4-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b7dd4-106">Методы</span><span class="sxs-lookup"><span data-stu-id="b7dd4-106">Methods</span></span>  
  
|<span data-ttu-id="b7dd4-107">Метод</span><span class="sxs-lookup"><span data-stu-id="b7dd4-107">Method</span></span>|<span data-ttu-id="b7dd4-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b7dd4-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7dd4-109">Метод ICorDebugRemoteTarget::GetHostName</span><span class="sxs-lookup"><span data-stu-id="b7dd4-109">ICorDebugRemoteTarget::GetHostName Method</span></span>](icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="b7dd4-110">Возвращает имя узла или IP-адрес удаленного компьютера.</span><span class="sxs-lookup"><span data-stu-id="b7dd4-110">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7dd4-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="b7dd4-111">Remarks</span></span>  

 <span data-ttu-id="b7dd4-112">Отладка в смешанном режиме (управляемый и машинный код) не поддерживается в Windows 95, Windows 98 или Windows ME, а также на платформах, отличных от x86 (например, IA-64 и AMD64).</span><span class="sxs-lookup"><span data-stu-id="b7dd4-112">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7dd4-113">Требования</span><span class="sxs-lookup"><span data-stu-id="b7dd4-113">Requirements</span></span>  

 <span data-ttu-id="b7dd4-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7dd4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7dd4-115">**Заголовок:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="b7dd4-115">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="b7dd4-116">**Библиотека:** : коргуидс. lib</span><span class="sxs-lookup"><span data-stu-id="b7dd4-116">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7dd4-117">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="b7dd4-117">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7dd4-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b7dd4-118">See also</span></span>

- [<span data-ttu-id="b7dd4-119">Интерфейс ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="b7dd4-119">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="b7dd4-120">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="b7dd4-120">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="b7dd4-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b7dd4-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
