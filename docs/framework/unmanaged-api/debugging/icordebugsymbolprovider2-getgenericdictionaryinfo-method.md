---
description: 'Дополнительные сведения о методе: ICorDebugSymbolProvider2:: Жетженерикдиктионаринфо'
title: Метод ICorDebugSymbolProvider2::GetGenericDictionaryInfo
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: 3488cab9ee21ea027e16089f066369ab8c6c69d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659547"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="5fd38-103">Метод ICorDebugSymbolProvider2::GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="5fd38-103">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="5fd38-104">Получает универсальную карту словаря</span><span class="sxs-lookup"><span data-stu-id="5fd38-104">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="5fd38-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5fd38-105">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="5fd38-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5fd38-106">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="5fd38-107">заполняет Указатель на адрес объекта [икордебугмеморибуффер](icordebugmemorybuffer-interface.md) , содержащего универсальную карту словаря.</span><span class="sxs-lookup"><span data-stu-id="5fd38-107">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="5fd38-108">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="5fd38-108">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="5fd38-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="5fd38-109">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="5fd38-110">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="5fd38-110">This method is available with .NET Native only.</span></span>

<span data-ttu-id="5fd38-111">Карта состоит из двух разделов верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="5fd38-111">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="5fd38-112">[Каталог](#Directory) , содержащий относительные виртуальные адреса (RVA) всех словарей, входящих в эту карту.</span><span class="sxs-lookup"><span data-stu-id="5fd38-112">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="5fd38-113">[Куча](#Heap) с согласованием байтов, которая содержит сведения о создании экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="5fd38-113">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="5fd38-114">Она запускается сразу после последней записи каталога.</span><span class="sxs-lookup"><span data-stu-id="5fd38-114">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="5fd38-115">Каталог</span><span class="sxs-lookup"><span data-stu-id="5fd38-115">The Directory</span></span>

<span data-ttu-id="5fd38-116">Каждая запись в каталоге ссылается на смещение в куче; то есть это смещение относительно начала кучи.</span><span class="sxs-lookup"><span data-stu-id="5fd38-116">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="5fd38-117">Значения отдельных записей, не обязательно должны быть уникальными; несколько записей каталога могут указывать на одно и то же смещение в куче.</span><span class="sxs-lookup"><span data-stu-id="5fd38-117">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="5fd38-118">Часть каталога универсальной карты словаря имеет следующую структуру.</span><span class="sxs-lookup"><span data-stu-id="5fd38-118">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="5fd38-119">Первые 4 байта содержит число записей словаря (т. е. число относительных виртуальных адресов в словаре).</span><span class="sxs-lookup"><span data-stu-id="5fd38-119">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="5fd38-120">Мы будем называть это значение *N*. Если задан высокий бит, записи сортируются по относительному виртуальному адресу в возрастающем порядке.</span><span class="sxs-lookup"><span data-stu-id="5fd38-120">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="5fd38-121">Далее следуют записи каталога *N* .</span><span class="sxs-lookup"><span data-stu-id="5fd38-121">The *N* directory entries follow.</span></span> <span data-ttu-id="5fd38-122">Каждая запись состоит из 8 байт в двух 4-байтовых сегментах.</span><span class="sxs-lookup"><span data-stu-id="5fd38-122">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="5fd38-123">Байты с 0 по 3: RVA; относительный виртуальный адрес словаря.</span><span class="sxs-lookup"><span data-stu-id="5fd38-123">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="5fd38-124">Байты с 4 по 7: смещение; смещение относительно начала кучи.</span><span class="sxs-lookup"><span data-stu-id="5fd38-124">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="5fd38-125">Куча</span><span class="sxs-lookup"><span data-stu-id="5fd38-125">The Heap</span></span>

<span data-ttu-id="5fd38-126">Размер кучи может быть вычислен модулем чтения потока путем вычитания длины потока из размера каталога + 4.</span><span class="sxs-lookup"><span data-stu-id="5fd38-126">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="5fd38-127">Другими словами:</span><span class="sxs-lookup"><span data-stu-id="5fd38-127">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="5fd38-128">где размер каталога равен `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="5fd38-128">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="5fd38-129">Формат каждого элемента сведений о создании экземпляра в куче выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="5fd38-129">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="5fd38-130">Длина этого элемента сведений о создании экземпляра в байтах в сжатом формате ECMA метаданных.</span><span class="sxs-lookup"><span data-stu-id="5fd38-130">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="5fd38-131">Значение исключает эти сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="5fd38-131">The value excludes this length information.</span></span>

- <span data-ttu-id="5fd38-132">Число универсальных типов создания экземпляров, или *T*, в сжатом формате метаданных ECMA.</span><span class="sxs-lookup"><span data-stu-id="5fd38-132">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="5fd38-133">Типы *T* , каждый из которых представлен в формате сигнатуры типа ECMA.</span><span class="sxs-lookup"><span data-stu-id="5fd38-133">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="5fd38-134">Включение длины для каждого элемента кучи позволяет простую сортировку раздела каталога без влияния на кучу.</span><span class="sxs-lookup"><span data-stu-id="5fd38-134">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="5fd38-135">Требования</span><span class="sxs-lookup"><span data-stu-id="5fd38-135">Requirements</span></span>

<span data-ttu-id="5fd38-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fd38-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5fd38-137">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fd38-137">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="5fd38-138">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fd38-138">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5fd38-139">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fd38-139">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5fd38-140">См. также</span><span class="sxs-lookup"><span data-stu-id="5fd38-140">See also</span></span>

- [<span data-ttu-id="5fd38-141">Интерфейс ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="5fd38-141">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="5fd38-142">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="5fd38-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
