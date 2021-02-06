---
description: 'Дополнительные сведения о методе ICorDebugThread:: Жеткуррентексцептион'
title: Метод ICorDebugThread::GetCurrentException
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
ms.openlocfilehash: cb241995520f26ca0e35f2b9e3b3187c2a2906a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659170"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="ca19a-103">Метод ICorDebugThread::GetCurrentException</span><span class="sxs-lookup"><span data-stu-id="ca19a-103">ICorDebugThread::GetCurrentException Method</span></span>

<span data-ttu-id="ca19a-104">Возвращает указатель интерфейса на объект ICorDebugValue, представляющий исключение, которое в данный момент вызывается управляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="ca19a-104">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca19a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ca19a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca19a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ca19a-106">Parameters</span></span>  

 `ppExceptionObject`  
 <span data-ttu-id="ca19a-107">заполняет Указатель на адрес `ICorDebugValue` объекта, представляющий исключение, которое в данный момент вызывается управляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="ca19a-107">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca19a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="ca19a-108">Remarks</span></span>  

 <span data-ttu-id="ca19a-109">Объект исключения будет существовать с момента возникновения исключения до конца `catch` блока.</span><span class="sxs-lookup"><span data-stu-id="ca19a-109">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="ca19a-110">Вычисление функции, выполняемое методами ICorDebugEval, очистит объект исключения при установке и восстановит его по завершении.</span><span class="sxs-lookup"><span data-stu-id="ca19a-110">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="ca19a-111">Исключения могут быть вложенными (например, если исключение создается в фильтре или в вычислении функции), поэтому в одном потоке может быть несколько необработанных исключений.</span><span class="sxs-lookup"><span data-stu-id="ca19a-111">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="ca19a-112">`GetCurrentException` Возвращает последнее исключение.</span><span class="sxs-lookup"><span data-stu-id="ca19a-112">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="ca19a-113">Объект и тип исключения могут меняться в течение всего времени существования исключения.</span><span class="sxs-lookup"><span data-stu-id="ca19a-113">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="ca19a-114">Например, после возникновения исключения типа x среда CLR может закончится нехваткой памяти и повысить ее до исключения нехватки памяти.</span><span class="sxs-lookup"><span data-stu-id="ca19a-114">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca19a-115">Требования</span><span class="sxs-lookup"><span data-stu-id="ca19a-115">Requirements</span></span>  

 <span data-ttu-id="ca19a-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca19a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca19a-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca19a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca19a-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca19a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca19a-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca19a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
