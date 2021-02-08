---
description: 'Дополнительные сведения: структура CALL_ID'
title: Структура CALL_ID
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
ms.openlocfilehash: 4ef6023e382e8c5fead48494f428648a37f3bef4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800491"
---
# <a name="call_id-structure"></a><span data-ttu-id="59a2c-103">Структура CALL_ID</span><span class="sxs-lookup"><span data-stu-id="59a2c-103">CALL_ID Structure</span></span>

<span data-ttu-id="59a2c-104">Предоставляет сведения отладчику о вызываемой функции.</span><span class="sxs-lookup"><span data-stu-id="59a2c-104">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="59a2c-105">Дополнительные сведения см. в интерфейсе [INotifySink2](inotifysink2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="59a2c-105">See the [INotifySink2](inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59a2c-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="59a2c-106">Syntax</span></span>  
  
```cpp  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a><span data-ttu-id="59a2c-107">Члены</span><span class="sxs-lookup"><span data-stu-id="59a2c-107">Members</span></span>  
  
|<span data-ttu-id="59a2c-108">Член</span><span class="sxs-lookup"><span data-stu-id="59a2c-108">Member</span></span>|<span data-ttu-id="59a2c-109">Описание</span><span class="sxs-lookup"><span data-stu-id="59a2c-109">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="59a2c-110">Идентифицирует компьютер, выполняющий вызов.</span><span class="sxs-lookup"><span data-stu-id="59a2c-110">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="59a2c-111">Идентифицирует процессор компьютера.</span><span class="sxs-lookup"><span data-stu-id="59a2c-111">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="59a2c-112">Идентифицирует поток, который исполняет вызов.</span><span class="sxs-lookup"><span data-stu-id="59a2c-112">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="59a2c-113">Задает адрес стека вызовов.</span><span class="sxs-lookup"><span data-stu-id="59a2c-113">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="59a2c-114">Задает адрес вызова.</span><span class="sxs-lookup"><span data-stu-id="59a2c-114">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="59a2c-115">Определяет компьютер, который будет выполнять вызов.</span><span class="sxs-lookup"><span data-stu-id="59a2c-115">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59a2c-116">Требования</span><span class="sxs-lookup"><span data-stu-id="59a2c-116">Requirements</span></span>  

 <span data-ttu-id="59a2c-117">**Заголовок:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="59a2c-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59a2c-118">См. также</span><span class="sxs-lookup"><span data-stu-id="59a2c-118">See also</span></span>

- [<span data-ttu-id="59a2c-119">Интерфейс INotifySink2</span><span class="sxs-lookup"><span data-stu-id="59a2c-119">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="59a2c-120">Структуры хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="59a2c-120">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
