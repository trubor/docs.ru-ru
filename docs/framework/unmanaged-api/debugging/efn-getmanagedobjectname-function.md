---
description: Дополнительные сведения о функции _EFN_GetManagedObjectName
title: Функция _EFN_GetManagedObjectName
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
ms.openlocfilehash: 4fa47848ace973f43acbcf8ab0322db4b974b205
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637902"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="cbbbb-103">\_ЕФН \_ жетманажедобжектнаме, функция</span><span class="sxs-lookup"><span data-stu-id="cbbbb-103">\_EFN\_GetManagedObjectName Function</span></span>

<span data-ttu-id="cbbbb-104">Возвращает имя типа, используя предоставленный указатель управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="cbbbb-104">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbbbb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cbbbb-105">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbbbb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cbbbb-106">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="cbbbb-107">окне Указатель на клиент отладки.</span><span class="sxs-lookup"><span data-stu-id="cbbbb-107">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="cbbbb-108">окне Указатель на управляемый объект.</span><span class="sxs-lookup"><span data-stu-id="cbbbb-108">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="cbbbb-109">szName</span><span class="sxs-lookup"><span data-stu-id="cbbbb-109">szName</span></span>  
 <span data-ttu-id="cbbbb-110">заполняет Имя типа.</span><span class="sxs-lookup"><span data-stu-id="cbbbb-110">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="cbbbb-111">заполняет Число символов, доступных в буфере строк.</span><span class="sxs-lookup"><span data-stu-id="cbbbb-111">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbbbb-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="cbbbb-112">Remarks</span></span>  

 <span data-ttu-id="cbbbb-113">Если в текущем потоке нет управляемого кода, функция возвращает HRESULT SOS_E_NOMANAGEDCODE со значением устройства 0x82 и кодом ошибки 0x1000.</span><span class="sxs-lookup"><span data-stu-id="cbbbb-113">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbbbb-114">Требования</span><span class="sxs-lookup"><span data-stu-id="cbbbb-114">Requirements</span></span>  

 <span data-ttu-id="cbbbb-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbbbb-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbbbb-116">**Заголовок:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="cbbbb-116">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="cbbbb-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbbbb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbbbb-118">См. также</span><span class="sxs-lookup"><span data-stu-id="cbbbb-118">See also</span></span>

- [<span data-ttu-id="cbbbb-119">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="cbbbb-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
