---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain:: Name'
title: Метод ICorDebugAppDomain::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 56995f544e1576534e35b899a659ed409972305f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772436"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="787a0-103">Метод ICorDebugAppDomain::GetName</span><span class="sxs-lookup"><span data-stu-id="787a0-103">ICorDebugAppDomain::GetName Method</span></span>

<span data-ttu-id="787a0-104">Возвращает имя домена приложения.</span><span class="sxs-lookup"><span data-stu-id="787a0-104">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="787a0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="787a0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="787a0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="787a0-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="787a0-107">[in] Размер массива `szName`.</span><span class="sxs-lookup"><span data-stu-id="787a0-107">[in] The size of the `szName` array.</span></span> <span data-ttu-id="787a0-108">Присвойте этому параметру значение 0, чтобы перевести этот метод в режим запроса.</span><span class="sxs-lookup"><span data-stu-id="787a0-108">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="787a0-109">заполняет Указатель на размер имени или числа символов, фактически возвращаемых в `szName` .</span><span class="sxs-lookup"><span data-stu-id="787a0-109">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="787a0-110">В режиме запроса это значение позволяет вызывающему объекту понять, насколько большой размер буфера выделяется для имени.</span><span class="sxs-lookup"><span data-stu-id="787a0-110">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="787a0-111">заполняет Массив, в котором хранится имя домена приложения.</span><span class="sxs-lookup"><span data-stu-id="787a0-111">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="787a0-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="787a0-112">Remarks</span></span>  

 <span data-ttu-id="787a0-113">Отладчик вызывает `GetName` метод один раз, чтобы получить размер буфера, необходимого для имени.</span><span class="sxs-lookup"><span data-stu-id="787a0-113">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="787a0-114">Отладчик выделяет буфер, а затем вызывает метод еще раз для заполнения буфера.</span><span class="sxs-lookup"><span data-stu-id="787a0-114">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="787a0-115">Первый вызов для получения размера имени называется *режимом запроса*.</span><span class="sxs-lookup"><span data-stu-id="787a0-115">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="787a0-116">Требования</span><span class="sxs-lookup"><span data-stu-id="787a0-116">Requirements</span></span>  

 <span data-ttu-id="787a0-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="787a0-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="787a0-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="787a0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="787a0-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="787a0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="787a0-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="787a0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
