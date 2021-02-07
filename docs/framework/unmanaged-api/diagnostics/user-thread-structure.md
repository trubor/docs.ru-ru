---
description: 'Дополнительные сведения: структура USER_THREAD'
title: Структура USER_THREAD
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
ms.openlocfilehash: a4bd22073b7610307e67107781bdb68a15ef795f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761272"
---
# <a name="user_thread-structure"></a><span data-ttu-id="b70a3-103">Структура USER_THREAD</span><span class="sxs-lookup"><span data-stu-id="b70a3-103">USER_THREAD Structure</span></span>

<span data-ttu-id="b70a3-104">Предоставляет сведения отладчику о потоке.</span><span class="sxs-lookup"><span data-stu-id="b70a3-104">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="b70a3-105">Дополнительные сведения см. в описании метода [INotifySource2:: сетнотифифилтер](inotifysource2-setnotifyfilter-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b70a3-105">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b70a3-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b70a3-106">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="b70a3-107">Члены</span><span class="sxs-lookup"><span data-stu-id="b70a3-107">Members</span></span>  
  
|<span data-ttu-id="b70a3-108">Член</span><span class="sxs-lookup"><span data-stu-id="b70a3-108">Member</span></span>|<span data-ttu-id="b70a3-109">Описание</span><span class="sxs-lookup"><span data-stu-id="b70a3-109">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="b70a3-110">Адрес буфера потока.</span><span class="sxs-lookup"><span data-stu-id="b70a3-110">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="b70a3-111">Длина буфера потока в байтах.</span><span class="sxs-lookup"><span data-stu-id="b70a3-111">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="b70a3-112">Идентификатор потока.</span><span class="sxs-lookup"><span data-stu-id="b70a3-112">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b70a3-113">Требования</span><span class="sxs-lookup"><span data-stu-id="b70a3-113">Requirements</span></span>  

 <span data-ttu-id="b70a3-114">**Заголовок:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="b70a3-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b70a3-115">См. также</span><span class="sxs-lookup"><span data-stu-id="b70a3-115">See also</span></span>

- [<span data-ttu-id="b70a3-116">Метод SetNotifyFilter</span><span class="sxs-lookup"><span data-stu-id="b70a3-116">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="b70a3-117">Структуры хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="b70a3-117">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
