---
description: 'Дополнительные сведения о методе: Вебхеадерколлектион. Аддинтернал'
title: Вебхеадерколлектион. Аддинтернал, метод (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 7bc84f84e6656dba5230b627fe9decfc4e0b4746
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699484"
---
# <a name="webheadercollectionaddinternal-method"></a><span data-ttu-id="d8304-103">Вебхеадерколлектион. Аддинтернал, метод</span><span class="sxs-lookup"><span data-stu-id="d8304-103">WebHeaderCollection.AddInternal method</span></span>

<span data-ttu-id="d8304-104">Добавляет новый заголовок с указанным именем и значением в коллекцию, минуя проверки.</span><span class="sxs-lookup"><span data-stu-id="d8304-104">Adds a new header with the specified name and value to the collection, bypassing checks.</span></span>

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> <span data-ttu-id="d8304-105">Этот метод является внутренним и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="d8304-105">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d8304-106">Корпорация Майкрософт не поддерживает использование этого метода в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="d8304-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="d8304-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="d8304-107">Parameters</span></span>

- <span data-ttu-id="d8304-108">`name` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="d8304-108">`name` <xref:System.String></span></span>

  <span data-ttu-id="d8304-109">Имя заголовка.</span><span class="sxs-lookup"><span data-stu-id="d8304-109">The name of the header.</span></span>

- <span data-ttu-id="d8304-110">`value` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="d8304-110">`value` <xref:System.String></span></span>

  <span data-ttu-id="d8304-111">Значение заголовка.</span><span class="sxs-lookup"><span data-stu-id="d8304-111">The value of the header.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8304-112">Требования</span><span class="sxs-lookup"><span data-stu-id="d8304-112">Requirements</span></span>

<span data-ttu-id="d8304-113">**Пространство имен:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d8304-113">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d8304-114">**Сборка:** Система (в System.dll)</span><span class="sxs-lookup"><span data-stu-id="d8304-114">**Assembly:** System (in System.dll)</span></span>
