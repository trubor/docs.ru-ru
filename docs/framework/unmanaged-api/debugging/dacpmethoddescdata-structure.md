---
description: 'Дополнительные сведения о: структура Дакпмесоддескдата'
title: Структура DacpMethodDescData
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: fe5b09874b3f8e123cb2501fcb00e3351aa44757
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801466"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="dd481-103">Структура DacpMethodDescData</span><span class="sxs-lookup"><span data-stu-id="dd481-103">DacpMethodDescData Structure</span></span>

<span data-ttu-id="dd481-104">Определяет транспортный буфер для сведений о среде выполнения метода.</span><span class="sxs-lookup"><span data-stu-id="dd481-104">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="dd481-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dd481-105">Syntax</span></span>

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a><span data-ttu-id="dd481-106">Члены</span><span class="sxs-lookup"><span data-stu-id="dd481-106">Members</span></span>

| <span data-ttu-id="dd481-107">Член</span><span class="sxs-lookup"><span data-stu-id="dd481-107">Member</span></span>                       | <span data-ttu-id="dd481-108">Описание</span><span class="sxs-lookup"><span data-stu-id="dd481-108">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="dd481-109">Указывает, доступен ли в среде выполнения машинный код для данного экземпляра метода.</span><span class="sxs-lookup"><span data-stu-id="dd481-109">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="dd481-110">Указывает, создается ли метод динамически с помощью создания упрощенного кода.</span><span class="sxs-lookup"><span data-stu-id="dd481-110">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="dd481-111">Номер слота метода в таблице методов.</span><span class="sxs-lookup"><span data-stu-id="dd481-111">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="dd481-112">Начальный собственный адрес метода.</span><span class="sxs-lookup"><span data-stu-id="dd481-112">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="dd481-113">Указатель на буфер, который используется средой выполнения для внутренних целей.</span><span class="sxs-lookup"><span data-stu-id="dd481-113">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="dd481-114">Указатель на объект `MethodDesc` в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="dd481-114">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="dd481-115">Указатель на буфер, используемый средой выполнения для трассировки методов.</span><span class="sxs-lookup"><span data-stu-id="dd481-115">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="dd481-116">Указатель на буфер, используемый средой выполнения для сведений о модуле.</span><span class="sxs-lookup"><span data-stu-id="dd481-116">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="dd481-117">Токен, связанный с данным методом.</span><span class="sxs-lookup"><span data-stu-id="dd481-117">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="dd481-118">Указатель на буфер сборки мусора, который используется средой выполнения для внутренних целей.</span><span class="sxs-lookup"><span data-stu-id="dd481-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="dd481-119">Указатель на буфер сборки мусора, который используется средой выполнения для внутренних целей.</span><span class="sxs-lookup"><span data-stu-id="dd481-119">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="dd481-120">Если метод является динамическим, среда выполнения использует этот буфер для внутреннего отслеживания сведений.</span><span class="sxs-lookup"><span data-stu-id="dd481-120">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="dd481-121">Используется для заполнения структуры на запрос при наличии адреса машинного кода.</span><span class="sxs-lookup"><span data-stu-id="dd481-121">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="dd481-122">Сведения о последней инструментированной версии метода.</span><span class="sxs-lookup"><span data-stu-id="dd481-122">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="dd481-123">Rejit сведения для запрошенного собственного адреса.</span><span class="sxs-lookup"><span data-stu-id="dd481-123">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="dd481-124">Сколько раз метод был режиттед с помощью инструментирования.</span><span class="sxs-lookup"><span data-stu-id="dd481-124">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="dd481-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="dd481-125">Remarks</span></span>

<span data-ttu-id="dd481-126">Эта структура находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="dd481-126">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="dd481-127">Чтобы использовать его, определите структуру, как указано выше.</span><span class="sxs-lookup"><span data-stu-id="dd481-127">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="dd481-128">Требования</span><span class="sxs-lookup"><span data-stu-id="dd481-128">Requirements</span></span>

<span data-ttu-id="dd481-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd481-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="dd481-130">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="dd481-130">**Header:** None</span></span>  
<span data-ttu-id="dd481-131">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="dd481-131">**Library:** None</span></span>  
<span data-ttu-id="dd481-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dd481-132">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="dd481-133">См. также</span><span class="sxs-lookup"><span data-stu-id="dd481-133">See also</span></span>

- [<span data-ttu-id="dd481-134">Отладка</span><span class="sxs-lookup"><span data-stu-id="dd481-134">Debugging</span></span>](index.md)
- [<span data-ttu-id="dd481-135">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="dd481-135">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="dd481-136">Общие типы данных</span><span class="sxs-lookup"><span data-stu-id="dd481-136">Common Data Types</span></span>](../common-data-types-unmanaged-api-reference.md)
