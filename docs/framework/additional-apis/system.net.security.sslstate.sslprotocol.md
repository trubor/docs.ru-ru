---
description: 'Дополнительные сведения о свойстве: Сслстате. Сслпротокол'
title: Свойство Сслстате. Сслпротокол (System .NET. Security)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Security.SslState.SslProtocol
- System.Net.Security.SslState.get_SslProtocol
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: b0b9bebf23fcd8d643d06f1cff10c260c77a7c08
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699627"
---
# <a name="sslstatesslprotocol-property"></a><span data-ttu-id="52f6c-103">Сслстате. Сслпротокол, свойство</span><span class="sxs-lookup"><span data-stu-id="52f6c-103">SslState.SslProtocol Property</span></span>

<span data-ttu-id="52f6c-104">Возвращает версии протокола SSL.</span><span class="sxs-lookup"><span data-stu-id="52f6c-104">Gets the SSL protocol versions.</span></span>

## <a name="syntax"></a><span data-ttu-id="52f6c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="52f6c-105">Syntax</span></span>

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a><span data-ttu-id="52f6c-106">Значение свойства</span><span class="sxs-lookup"><span data-stu-id="52f6c-106">Property value</span></span>

<xref:System.Security.Authentication.SslProtocols>  
<span data-ttu-id="52f6c-107">Побитовое сочетание значений перечисления, определяющих версии протокола SSL.</span><span class="sxs-lookup"><span data-stu-id="52f6c-107">A bitwise combination of the enumeration values that specify the SSL protocol versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="52f6c-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="52f6c-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="52f6c-109">`SslState.SslProtocol`Свойство является внутренним и не предназначено для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="52f6c-109">The `SslState.SslProtocol` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="52f6c-110">Корпорация Майкрософт не поддерживает использование этого свойства в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="52f6c-110">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="52f6c-111">Требования</span><span class="sxs-lookup"><span data-stu-id="52f6c-111">Requirements</span></span>

<span data-ttu-id="52f6c-112">**Пространство имен:** <xref:System.Net.Security></span><span class="sxs-lookup"><span data-stu-id="52f6c-112">**Namespace:** <xref:System.Net.Security></span></span>

<span data-ttu-id="52f6c-113">**Сборка:** Система (в System.dll)</span><span class="sxs-lookup"><span data-stu-id="52f6c-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="52f6c-114">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="52f6c-114">**.NET Framework versions:** Available since 2.0.</span></span>
