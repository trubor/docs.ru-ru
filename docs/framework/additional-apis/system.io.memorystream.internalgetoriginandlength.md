---
description: Дополнительные сведения о методе MemoryStream. Интерналжеторигинандленгс
title: Метод MemoryStream. Интерналжеторигинандленгс (System.IO)
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 4232852c0835a43454f36271a43062e1240297a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802545"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a><span data-ttu-id="f470c-103">Метод MemoryStream.InternalGetOriginAndLength</span><span class="sxs-lookup"><span data-stu-id="f470c-103">MemoryStream.InternalGetOriginAndLength method</span></span>

<span data-ttu-id="f470c-104">Возвращает внутренние значения источника и длину потока памяти.</span><span class="sxs-lookup"><span data-stu-id="f470c-104">Gets the internal values of origin and length of the memory stream.</span></span>

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a><span data-ttu-id="f470c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="f470c-105">Parameters</span></span>

- <span data-ttu-id="f470c-106">`origin` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="f470c-106">`origin` <xref:System.Int32></span></span>\
  <span data-ttu-id="f470c-107">При возврате из этого метода смещение массива байтов, указанного при создании нового <xref:System.IO.MemoryStream> объекта.</span><span class="sxs-lookup"><span data-stu-id="f470c-107">When this method returns, the offset of the byte array specified when creating a new <xref:System.IO.MemoryStream> object.</span></span> <span data-ttu-id="f470c-108">Содержит 0, если массив байтов был создан <xref:System.IO.MemoryStream> .</span><span class="sxs-lookup"><span data-stu-id="f470c-108">Contains 0 if the byte array was created by <xref:System.IO.MemoryStream>.</span></span>

- <span data-ttu-id="f470c-109">`length` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="f470c-109">`length` <xref:System.Int32></span></span>\
  <span data-ttu-id="f470c-110">При возврате из этого метода число байтов в потоке памяти.</span><span class="sxs-lookup"><span data-stu-id="f470c-110">When this method returns, the number of bytes within the memory stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="f470c-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f470c-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f470c-112">`MemoryStream.InternalGetOriginAndLength`Метод является внутренним и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="f470c-112">The `MemoryStream.InternalGetOriginAndLength` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f470c-113">Корпорация Майкрософт не поддерживает использование этого метода в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="f470c-113">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f470c-114">Требования</span><span class="sxs-lookup"><span data-stu-id="f470c-114">Requirements</span></span>

<span data-ttu-id="f470c-115">**Пространство имен:** <xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="f470c-115">**Namespace:** <xref:System.IO></span></span>

<span data-ttu-id="f470c-116">**Сборка:** mscorlib.dll (в mscorlib.dll)</span><span class="sxs-lookup"><span data-stu-id="f470c-116">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="f470c-117">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="f470c-117">**.NET Framework versions:** Available since 2.0.</span></span>
