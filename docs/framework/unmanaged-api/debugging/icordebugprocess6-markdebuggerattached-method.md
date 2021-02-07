---
description: 'Дополнительные сведения о методе: ICorDebugProcess6:: MarkDebuggerAttached'
title: Метод ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: adbe16049cea73ca5e797f7758a17902b33645c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691384"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="56341-103">Метод ICorDebugProcess6::MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="56341-103">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>

<span data-ttu-id="56341-104">Изменяет внутреннее состояние отлаживаемого кода таким образом, что метод <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> в библиотеке классов платформы .NET Framework возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="56341-104">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56341-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="56341-105">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56341-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="56341-106">Parameters</span></span>  

 `fIsAttached`  
 <span data-ttu-id="56341-107">`true`, если метод <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> должен указать, что отладчик присоединен; в противном случае, `false`.</span><span class="sxs-lookup"><span data-stu-id="56341-107">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56341-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="56341-108">Return Value</span></span>  

 <span data-ttu-id="56341-109">Метод может возвращать значения, перечисленные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="56341-109">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="56341-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="56341-110">Return value</span></span>|<span data-ttu-id="56341-111">Описание</span><span class="sxs-lookup"><span data-stu-id="56341-111">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="56341-112">Отлаживаемый объект успешно обновлен.</span><span class="sxs-lookup"><span data-stu-id="56341-112">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="56341-113">Сборка, содержащая метод <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>, не загружена, или другие ошибки, например, отсутствующие метаданные не позволяют ее распознать.</span><span class="sxs-lookup"><span data-stu-id="56341-113">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="56341-114">Эта ошибка является общей и носит информационный характер.</span><span class="sxs-lookup"><span data-stu-id="56341-114">This error is common and benign.</span></span> <span data-ttu-id="56341-115">Метод следует вызвать снова при загрузке дополнительных сборок.</span><span class="sxs-lookup"><span data-stu-id="56341-115">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="56341-116">Другие ошибочные значения `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="56341-116">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="56341-117">Скорее всего, другие значения указывают некорректно работающие компоненты отладчика или компилятора.</span><span class="sxs-lookup"><span data-stu-id="56341-117">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56341-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="56341-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56341-119">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="56341-119">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56341-120">Требования</span><span class="sxs-lookup"><span data-stu-id="56341-120">Requirements</span></span>  

 <span data-ttu-id="56341-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56341-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56341-122">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56341-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56341-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56341-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56341-124">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56341-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56341-125">См. также</span><span class="sxs-lookup"><span data-stu-id="56341-125">See also</span></span>

- [<span data-ttu-id="56341-126">Интерфейс ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="56341-126">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="56341-127">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="56341-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
