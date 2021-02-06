---
description: Дополнительные сведения о функции _EFN_GetManagedObjectFieldInfo
title: Функция _EFN_GetManagedObjectFieldInfo
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
ms.openlocfilehash: 749ab286a86db07c1b66ff2b61ff073d15334800
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637892"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a><span data-ttu-id="e81d6-103">\_ЕФН \_ жетманажедобжектфиелдинфо, функция</span><span class="sxs-lookup"><span data-stu-id="e81d6-103">\_EFN\_GetManagedObjectFieldInfo Function</span></span>

<span data-ttu-id="e81d6-104">Возвращает смещение от начала объекта до поля и значение поля, используя предоставленный указатель объекта и имя поля.</span><span class="sxs-lookup"><span data-stu-id="e81d6-104">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e81d6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e81d6-105">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e81d6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e81d6-106">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="e81d6-107">окне Указатель на клиент отладки.</span><span class="sxs-lookup"><span data-stu-id="e81d6-107">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="e81d6-108">окне Указатель на управляемый объект.</span><span class="sxs-lookup"><span data-stu-id="e81d6-108">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="e81d6-109">сзфиелднаме</span><span class="sxs-lookup"><span data-stu-id="e81d6-109">szFieldName</span></span>  
 <span data-ttu-id="e81d6-110">окне Указатель управляемого объекта на имя поля.</span><span class="sxs-lookup"><span data-stu-id="e81d6-110">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e81d6-111">заполняет Значение поля.</span><span class="sxs-lookup"><span data-stu-id="e81d6-111">[out] The field value.</span></span> <span data-ttu-id="e81d6-112">Этот параметр может быть нулевым.</span><span class="sxs-lookup"><span data-stu-id="e81d6-112">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="e81d6-113">заполняет Смещение от `objAddr` до поля.</span><span class="sxs-lookup"><span data-stu-id="e81d6-113">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="e81d6-114">Этот параметр может быть нулевым.</span><span class="sxs-lookup"><span data-stu-id="e81d6-114">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e81d6-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="e81d6-115">Remarks</span></span>  

 <span data-ttu-id="e81d6-116">Если смещение равно 0, смещение не записывается.</span><span class="sxs-lookup"><span data-stu-id="e81d6-116">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="e81d6-117">Если в текущем потоке нет управляемого кода, функция возвращает HRESULT SOS_E_NOMANAGEDCODE со значением устройства 0x82 и кодом ошибки 0x1000.</span><span class="sxs-lookup"><span data-stu-id="e81d6-117">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e81d6-118">Требования</span><span class="sxs-lookup"><span data-stu-id="e81d6-118">Requirements</span></span>  

 <span data-ttu-id="e81d6-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e81d6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e81d6-120">**Заголовок:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="e81d6-120">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="e81d6-121">**Версия платформа .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e81d6-121">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e81d6-122">См. также</span><span class="sxs-lookup"><span data-stu-id="e81d6-122">See also</span></span>

- [<span data-ttu-id="e81d6-123">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="e81d6-123">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
