---
description: 'Дополнительные сведения о методе: ICorDebugProcess6:: Жетекспортстепинфо'
title: Метод ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: e14b5e66d90fb2ece91991b3634fc2ad86fac895
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722013"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="01fa4-103">Метод ICorDebugProcess6::GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="01fa4-103">ICorDebugProcess6::GetExportStepInfo Method</span></span>

<span data-ttu-id="01fa4-104">Предоставляет информацию о функциях, экспортируемых в ходе выполнения, для пошагового перемещения по управляемому коду.</span><span class="sxs-lookup"><span data-stu-id="01fa4-104">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01fa4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="01fa4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01fa4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="01fa4-106">Parameters</span></span>  

 <span data-ttu-id="01fa4-107">pszExportName</span><span class="sxs-lookup"><span data-stu-id="01fa4-107">pszExportName</span></span>  
 <span data-ttu-id="01fa4-108">[входной] Имя функции экспорта во время выполнения, записываемой в таблице экспорта PE.</span><span class="sxs-lookup"><span data-stu-id="01fa4-108">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="01fa4-109">invokeKind</span><span class="sxs-lookup"><span data-stu-id="01fa4-109">invokeKind</span></span>  
 <span data-ttu-id="01fa4-110">заполняет Указатель на член перечисления [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) , описывающий, как экспортируемая функция будет вызывать управляемый код.</span><span class="sxs-lookup"><span data-stu-id="01fa4-110">[out] A pointer to a member of the [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="01fa4-111">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="01fa4-111">invokePurpose</span></span>  
 <span data-ttu-id="01fa4-112">заполняет Указатель на член перечисления [кордебугкодеинвокепурпосе](cordebugcodeinvokepurpose-enumeration.md) , описывающий, почему экспортируемая функция будет вызывать управляемый код.</span><span class="sxs-lookup"><span data-stu-id="01fa4-112">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01fa4-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="01fa4-113">Return Value</span></span>  

 <span data-ttu-id="01fa4-114">Метод может возвращать значения, перечисленные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="01fa4-114">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="01fa4-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="01fa4-115">Return value</span></span>|<span data-ttu-id="01fa4-116">Описание</span><span class="sxs-lookup"><span data-stu-id="01fa4-116">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="01fa4-117">Успешный вызов метода.</span><span class="sxs-lookup"><span data-stu-id="01fa4-117">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="01fa4-118">`pInvokeKind` или `pInvokePurpose` имеет **значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="01fa4-118">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="01fa4-119">Другие ошибочные значения `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="01fa4-119">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="01fa4-120">По мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="01fa4-120">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01fa4-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="01fa4-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01fa4-122">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="01fa4-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01fa4-123">Требования</span><span class="sxs-lookup"><span data-stu-id="01fa4-123">Requirements</span></span>  

 <span data-ttu-id="01fa4-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01fa4-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01fa4-125">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01fa4-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01fa4-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01fa4-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01fa4-127">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01fa4-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01fa4-128">См. также</span><span class="sxs-lookup"><span data-stu-id="01fa4-128">See also</span></span>

- [<span data-ttu-id="01fa4-129">Интерфейс ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="01fa4-129">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="01fa4-130">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="01fa4-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
