---
description: 'Дополнительные сведения о: s_isDebuggerCheckDisabledForTestPurposes поле'
title: s_isDebuggerCheckDisabledForTestPurposes поле
ms.date: 03/30/2017
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: a71235c13a7a35872bcf5374be8077bafad5ff9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802662"
---
# <a name="s_isdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="e5191-103">s_isDebuggerCheckDisabledForTestPurposes поле</span><span class="sxs-lookup"><span data-stu-id="e5191-103">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="e5191-104">Это частное поле в `System.Windows.Diagnostics.VisualDiagnostics` классе используется в Visual Studio для определения, будет ли выполняться внутренняя проверка активного отладчика.</span><span class="sxs-lookup"><span data-stu-id="e5191-104">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5191-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e5191-105">Syntax</span></span>

```csharp
private static bool s_isDebuggerCheckDisabledForTestPurposes
```

> [!WARNING]
> <span data-ttu-id="e5191-106">API-интерфейсы в `System.Windows.Diagnostics.VisualDiagnostics` классе доступны только в том случае, если приложение выполняется в отладчике.</span><span class="sxs-lookup"><span data-stu-id="e5191-106">APIs in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="e5191-107">Задайте для значение, чтобы `s_isDebuggerCheckDisabledForTestPurposes` `true` получить доступ к API за пределами отладчика.</span><span class="sxs-lookup"><span data-stu-id="e5191-107">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>
>
> <span data-ttu-id="e5191-108">Корпорация Майкрософт не поддерживает использование этого поля в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="e5191-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5191-109">Требования</span><span class="sxs-lookup"><span data-stu-id="e5191-109">Requirements</span></span>

<span data-ttu-id="e5191-110">**Пространство имен:** <xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="e5191-110">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="e5191-111">**Сборка:** PresentationCore (в PresentationCore.dll)</span><span class="sxs-lookup"><span data-stu-id="e5191-111">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="e5191-112">**Платформа .NET Framework версии:** Доступно с 4,6.</span><span class="sxs-lookup"><span data-stu-id="e5191-112">**.NET Framework versions:** Available since 4.6.</span></span>
