---
description: Дополнительные сведения о функции _EFN_GetManagedExcepStack
title: Функция _EFN_GetManagedExcepStack
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
ms.openlocfilehash: a3c7e30a377e10b9d4d0b1dd663a594a0e872f3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738316"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="a453f-103">\_ЕФН \_ жетманажедексцепстакк, функция</span><span class="sxs-lookup"><span data-stu-id="a453f-103">\_EFN\_GetManagedExcepStack Function</span></span>

<span data-ttu-id="a453f-104">Учитывая адрес объекта управляемого исключения, возвращает строковую версию трассировки стека, содержащейся внутри.</span><span class="sxs-lookup"><span data-stu-id="a453f-104">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a453f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a453f-105">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a453f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a453f-106">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="a453f-107">окне Отлаживаемый клиент.</span><span class="sxs-lookup"><span data-stu-id="a453f-107">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="a453f-108">окне Указатель на управляемый объект, производный от <xref:System.Exception> .</span><span class="sxs-lookup"><span data-stu-id="a453f-108">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="a453f-109">сзстаккстринг</span><span class="sxs-lookup"><span data-stu-id="a453f-109">szStackString</span></span>  
 <span data-ttu-id="a453f-110">заполняет Возвращаемая строка.</span><span class="sxs-lookup"><span data-stu-id="a453f-110">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="a453f-111">заполняет Число символов, доступных в буфере строк.</span><span class="sxs-lookup"><span data-stu-id="a453f-111">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a453f-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="a453f-112">Remarks</span></span>  

 <span data-ttu-id="a453f-113">Если в текущем потоке нет управляемого кода, функция возвращает HRESULT SOS_E_NOMANAGEDCODE со значением устройства 0x82 и кодом ошибки 0x1000.</span><span class="sxs-lookup"><span data-stu-id="a453f-113">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a453f-114">Требования</span><span class="sxs-lookup"><span data-stu-id="a453f-114">Requirements</span></span>  

 <span data-ttu-id="a453f-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a453f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a453f-116">**Заголовок:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="a453f-116">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="a453f-117">**Версия платформа .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a453f-117">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a453f-118">См. также</span><span class="sxs-lookup"><span data-stu-id="a453f-118">See also</span></span>

- [<span data-ttu-id="a453f-119">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="a453f-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
