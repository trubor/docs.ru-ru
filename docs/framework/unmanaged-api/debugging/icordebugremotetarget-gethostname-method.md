---
description: 'См. Дополнительные сведения о методе ICorDebugRemoteTarget:: onhostname'
title: Метод ICorDebugRemoteTarget::GetHostName
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
ms.openlocfilehash: a24f34dd638c7031211c2185cd761af0aa24105e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803530"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="d9844-103">Метод ICorDebugRemoteTarget::GetHostName</span><span class="sxs-lookup"><span data-stu-id="d9844-103">ICorDebugRemoteTarget::GetHostName Method</span></span>

<span data-ttu-id="d9844-104">Возвращает полное доменное имя или IPv4-адрес целевого компьютера удаленной отладки.</span><span class="sxs-lookup"><span data-stu-id="d9844-104">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="d9844-105">В настоящее время IPV6 не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="d9844-105">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9844-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9844-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9844-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="d9844-107">Parameters</span></span>  

 `cchHostName`  
 <span data-ttu-id="d9844-108">окне Размер буфера (в символах) `szHostName` .</span><span class="sxs-lookup"><span data-stu-id="d9844-108">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="d9844-109">Если этот параметр равен 0 (нулю), он `szHostName` должен иметь значение null.</span><span class="sxs-lookup"><span data-stu-id="d9844-109">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="d9844-110">заполняет Количество символов, включая знак завершения null, в имени узла или IP-адресе.</span><span class="sxs-lookup"><span data-stu-id="d9844-110">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="d9844-111">Этот параметр может быть нулевым.</span><span class="sxs-lookup"><span data-stu-id="d9844-111">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="d9844-112">заполняет Буфер, содержащий имя узла или IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d9844-112">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9844-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d9844-113">Return Value</span></span>  

 <span data-ttu-id="d9844-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9844-114">S_OK</span></span>  
 <span data-ttu-id="d9844-115">Имя узла или IP-адрес успешно возвращены.</span><span class="sxs-lookup"><span data-stu-id="d9844-115">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="d9844-116">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="d9844-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="d9844-117">Не удалось вернуть имя узла или IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d9844-117">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9844-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="d9844-118">Remarks</span></span>  

 <span data-ttu-id="d9844-119">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="d9844-119">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="d9844-120">Он должен следовать парадигме нескольких вызовов: при первом вызове вызывающий объект передает значение NULL и `cchHostName` в `szHostName` , и `pcchHostName` возвращает размер требуемого буфера.</span><span class="sxs-lookup"><span data-stu-id="d9844-120">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="d9844-121">При втором вызове передается размер, который был ранее возвращен `cchHostName` , и передается буфер соответствующего размера `szHostName` .</span><span class="sxs-lookup"><span data-stu-id="d9844-121">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9844-122">Требования</span><span class="sxs-lookup"><span data-stu-id="d9844-122">Requirements</span></span>  

 <span data-ttu-id="d9844-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9844-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9844-124">**Заголовок:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="d9844-124">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="d9844-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9844-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9844-126">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="d9844-126">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9844-127">См. также</span><span class="sxs-lookup"><span data-stu-id="d9844-127">See also</span></span>

- [<span data-ttu-id="d9844-128">Интерфейс ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="d9844-128">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="d9844-129">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="d9844-129">ICorDebug Interface</span></span>](icordebug-interface.md)
