---
title: CoreResponseData.m_ResponseHeaders поле
description: Изучите поле CoreResponseData.m_ResponseHeaders в .NET. Это поле является типом Вебхеадерколлектион, который содержит заголовки, связанные с ответом сервера.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 6e0203094376de6ec2870649dd3c025e88639bb8
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875932"
---
# <a name="coreresponsedatam_responseheaders-field"></a><span data-ttu-id="efe1a-104">Поле ResponseHeaders Коререспонседата. m \_</span><span class="sxs-lookup"><span data-stu-id="efe1a-104">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="efe1a-105">`CoreResponseData.m_ResponseHeaders` — Это <xref:System.Net.WebHeaderCollection> заголовок, связанный с ответом сервера.</span><span class="sxs-lookup"><span data-stu-id="efe1a-105">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="efe1a-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="efe1a-106">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="efe1a-107">Этот API не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="efe1a-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="efe1a-108">Вместо этого следует использовать <xref:System.Diagnostics.DiagnosticSource> для подключения сетевого кода.</span><span class="sxs-lookup"><span data-stu-id="efe1a-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="efe1a-109">Ознакомьтесь с [руководством пользователя DiagnosticSource](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="efe1a-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="efe1a-110">Корпорация Майкрософт не поддерживает использование этого класса в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="efe1a-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="efe1a-111">Требования</span><span class="sxs-lookup"><span data-stu-id="efe1a-111">Requirements</span></span>

<span data-ttu-id="efe1a-112">**Пространство имен:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="efe1a-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="efe1a-113">**Сборка:** Система (в System.dll)</span><span class="sxs-lookup"><span data-stu-id="efe1a-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="efe1a-114">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="efe1a-114">**.NET Framework versions:** Available since 2.0.</span></span>
