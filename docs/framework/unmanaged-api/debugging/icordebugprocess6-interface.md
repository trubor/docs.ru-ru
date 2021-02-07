---
description: 'Дополнительные сведения о: интерфейс ICorDebugProcess6'
title: Интерфейс ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: f303670d0667a80507bc623f9af037759fdde463
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691462"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="691be-103">Интерфейс ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="691be-103">ICorDebugProcess6 Interface</span></span>

<span data-ttu-id="691be-104">Логически расширяет интерфейс ICorDebugProcess, чтобы включить такие возможности как декодирование событий управляемой отладки, которые кодируются в события отладки собственных исключений и разделение виртуальных модулей.</span><span class="sxs-lookup"><span data-stu-id="691be-104">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="691be-105">Методы</span><span class="sxs-lookup"><span data-stu-id="691be-105">Methods</span></span>  
  
|<span data-ttu-id="691be-106">Метод</span><span class="sxs-lookup"><span data-stu-id="691be-106">Method</span></span>|<span data-ttu-id="691be-107">Описание</span><span class="sxs-lookup"><span data-stu-id="691be-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="691be-108">Метод DecodeEvent</span><span class="sxs-lookup"><span data-stu-id="691be-108">DecodeEvent Method</span></span>](icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="691be-109">Декодирует события управляемой отладки, которые были инкапсулированы в полезную нагрузку из событий отладки специально созданных собственных исключений.</span><span class="sxs-lookup"><span data-stu-id="691be-109">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="691be-110">Метод EnableVirtualModuleSplitting</span><span class="sxs-lookup"><span data-stu-id="691be-110">EnableVirtualModuleSplitting Method</span></span>](icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="691be-111">Позволяет включить или отключить разделение виртуальных модулей.</span><span class="sxs-lookup"><span data-stu-id="691be-111">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="691be-112">Метод GetCode</span><span class="sxs-lookup"><span data-stu-id="691be-112">GetCode Method</span></span>](icordebugprocess6-getcode-method.md)|<span data-ttu-id="691be-113">Получает информацию об управляемом коде по адресу определенного кода.</span><span class="sxs-lookup"><span data-stu-id="691be-113">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="691be-114">Метод GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="691be-114">GetExportStepInfo Method</span></span>](icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="691be-115">Предоставляет информацию о функциях, экспортируемых в ходе выполнения, для пошагового перемещения по управляемому коду.</span><span class="sxs-lookup"><span data-stu-id="691be-115">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="691be-116">Метод MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="691be-116">MarkDebuggerAttached Method</span></span>](icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="691be-117">Изменяет внутреннее состояние отлаживаемого кода таким образом, что метод <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> в библиотеке классов платформы .NET Framework возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="691be-117">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="691be-118">Метод ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="691be-118">ProcessStateChanged Method</span></span>](icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="691be-119">Уведомляет [ICorDebug](icordebug-interface.md) о том, что процесс выполняется.</span><span class="sxs-lookup"><span data-stu-id="691be-119">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="691be-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="691be-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="691be-121">Этот интерфейс доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="691be-121">The interface is available with .NET Native only.</span></span> <span data-ttu-id="691be-122">Попытка вызова метода `QueryInterface` для получения указателя интерфейса возвращает `E_NOINTERFACE` для сценариев ICorDebug вне .NET Native.</span><span class="sxs-lookup"><span data-stu-id="691be-122">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="691be-123">Требования</span><span class="sxs-lookup"><span data-stu-id="691be-123">Requirements</span></span>  

 <span data-ttu-id="691be-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="691be-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="691be-125">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="691be-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="691be-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="691be-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="691be-127">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="691be-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691be-128">См. также</span><span class="sxs-lookup"><span data-stu-id="691be-128">See also</span></span>

- [<span data-ttu-id="691be-129">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="691be-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="691be-130">Отладка</span><span class="sxs-lookup"><span data-stu-id="691be-130">Debugging</span></span>](index.md)
