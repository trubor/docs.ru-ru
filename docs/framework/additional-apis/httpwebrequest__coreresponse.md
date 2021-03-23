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
# <a name="httpwebrequest_coreresponse-field"></a>HttpWebRequest. \_ Поле Коререспонсе

`HttpWebRequest._CoreResponse` — Это объект ( [коререспонседата](coreresponsedata.md) или <xref:System.Exception> ), содержащий результат синтаксического анализа ответа HTTP.

## <a name="syntax"></a>Синтаксис
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> Этот API не предназначен для непосредственного использования в коде. Вместо этого следует использовать <xref:System.Diagnostics.DiagnosticSource> для подключения сетевого кода. Ознакомьтесь с [руководством пользователя DiagnosticSource](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
>
> Корпорация Майкрософт не поддерживает использование этого класса в рабочем приложении при каких-либо обстоятельствах.

## <a name="requirements"></a>Требования

**Пространство имен:** <xref:System.Net>

**Сборка:** Система (в System.dll)

**Платформа .NET Framework версии:** Доступно с 2,0.
