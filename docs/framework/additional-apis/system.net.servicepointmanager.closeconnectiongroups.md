---
description: 'Дополнительные сведения о методе: ServicePointManager. Клосеконнектионграупс'
title: ServicePointManager. Клосеконнектионграупс, метод (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 8cd1a1f0f4dbdaeaee117e6a7ae4219680363a6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699562"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a><span data-ttu-id="047f7-103">ServicePointManager. Клосеконнектионграупс, метод</span><span class="sxs-lookup"><span data-stu-id="047f7-103">ServicePointManager.CloseConnectionGroups method</span></span>

<span data-ttu-id="047f7-104">Выполняет перебор всех точек обслуживания и закрывает группы соединений с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="047f7-104">Iterates through all service points and closes connection groups that have the specified name.</span></span>

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> <span data-ttu-id="047f7-105">Этот метод является внутренним и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="047f7-105">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="047f7-106">Корпорация Майкрософт не поддерживает использование этого метода в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="047f7-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="047f7-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="047f7-107">Parameters</span></span>

<span data-ttu-id="047f7-108">`connectionGroupName` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="047f7-108">`connectionGroupName` <xref:System.String></span></span>

<span data-ttu-id="047f7-109">Имя группы соединений, которую нужно закрыть.</span><span class="sxs-lookup"><span data-stu-id="047f7-109">The name of the connection group to close.</span></span>

## <a name="requirements"></a><span data-ttu-id="047f7-110">Требования</span><span class="sxs-lookup"><span data-stu-id="047f7-110">Requirements</span></span>

<span data-ttu-id="047f7-111">**Пространство имен:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="047f7-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="047f7-112">**Сборка:** Система (в System.dll)</span><span class="sxs-lookup"><span data-stu-id="047f7-112">**Assembly:** System (in System.dll)</span></span>
