---
description: 'Дополнительные сведения о свойстве: Пуледстреам. NetworkStream'
title: Свойство Пуледстреам. NetworkStream (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.PooledStream.NetworkStream
- System.Net.PooledStream.get_NetworkStream
- System.Net.PooledStream.set_NetworkStream
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 8a4f1d6bd9297028e763ef73bf96f85cbbfdafd6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699640"
---
# <a name="pooledstreamnetworkstream-property"></a><span data-ttu-id="d8ee0-103">Пуледстреам. NetworkStream, свойство</span><span class="sxs-lookup"><span data-stu-id="d8ee0-103">PooledStream.NetworkStream Property</span></span>

<span data-ttu-id="d8ee0-104">Возвращает или задает сетевой поток для `PooledStream` сокета.</span><span class="sxs-lookup"><span data-stu-id="d8ee0-104">Gets or sets the network stream for the `PooledStream` socket.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8ee0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d8ee0-105">Syntax</span></span>

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="d8ee0-106">Значение свойства</span><span class="sxs-lookup"><span data-stu-id="d8ee0-106">Property value</span></span>

<xref:System.Net.Sockets.NetworkStream>  
<span data-ttu-id="d8ee0-107">Сетевой поток для `PooledStream` сокета.</span><span class="sxs-lookup"><span data-stu-id="d8ee0-107">The network stream for the `PooledStream` socket.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8ee0-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="d8ee0-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d8ee0-109">`PooledStream.NetworkStream`Свойство является внутренним и не предназначено для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="d8ee0-109">The `PooledStream.NetworkStream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d8ee0-110">Корпорация Майкрософт не поддерживает использование этого свойства в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="d8ee0-110">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8ee0-111">Требования</span><span class="sxs-lookup"><span data-stu-id="d8ee0-111">Requirements</span></span>

<span data-ttu-id="d8ee0-112">**Пространство имен:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d8ee0-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d8ee0-113">**Сборка:** Система (в System.dll)</span><span class="sxs-lookup"><span data-stu-id="d8ee0-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="d8ee0-114">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="d8ee0-114">**.NET Framework versions:** Available since 2.0.</span></span>
