---
title: HttpWebRequest._CoreResponse поле
description: Прочитайте о поле HttpWebRequest._CoreResponse в .NET. Это поле является объектом Коререспонседата или Exception, содержащим результат синтаксического анализа ответа HTTP.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: f5fb71c21922285c0e18c2d1f28eeaf2353dcaee
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873839"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="1af8d-104">HttpWebRequest. \_ Поле Коререспонсе</span><span class="sxs-lookup"><span data-stu-id="1af8d-104">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="1af8d-105">`HttpWebRequest._CoreResponse` — Это объект ( [коререспонседата](coreresponsedata.md) или <xref:System.Exception> ), содержащий результат синтаксического анализа ответа HTTP.</span><span class="sxs-lookup"><span data-stu-id="1af8d-105">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="1af8d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1af8d-106">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="1af8d-107">Этот API не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="1af8d-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="1af8d-108">Вместо этого следует использовать <xref:System.Diagnostics.DiagnosticSource> для подключения сетевого кода.</span><span class="sxs-lookup"><span data-stu-id="1af8d-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="1af8d-109">Ознакомьтесь с [руководством пользователя DiagnosticSource](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="1af8d-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="1af8d-110">Корпорация Майкрософт не поддерживает использование этого класса в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="1af8d-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="1af8d-111">Требования</span><span class="sxs-lookup"><span data-stu-id="1af8d-111">Requirements</span></span>

<span data-ttu-id="1af8d-112">**Пространство имен:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="1af8d-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="1af8d-113">**Сборка:** Система (в System.dll)</span><span class="sxs-lookup"><span data-stu-id="1af8d-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="1af8d-114">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="1af8d-114">**.NET Framework versions:** Available since 2.0.</span></span>
