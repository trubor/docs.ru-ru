---
title: Технологии .NET Framework, недоступные в .NET Core и .NET 5 и более поздних версий
titleSuffix: ''
description: Узнайте о технологиях .NET Framework, недоступных в .NET Core и .NET 5.0 и более поздних версий.
author: cartermp
ms.date: 03/08/2021
ms.openlocfilehash: d8eccce7e36552e0d5396779936681227cb1e28a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875126"
---
# <a name="net-framework-technologies-unavailable-on-net-core-and-net-5"></a>Технологии .NET Framework, недоступные в .NET Core и .NET 5 и более поздних версий

Некоторые технологии для библиотек .NET Framework недоступны для использования с .NET 5+ (и .NET Core), например домены приложений, удаленное взаимодействие и управление доступом для кода (CAS). Если в библиотеках применяются технологии, указанные на этой странице, рассмотрите описанные ранее альтернативные подходы.

Дополнительные сведения о совместимости API см. в статье [Критические изменения .NET](../compatibility/breaking-changes.md).

## <a name="application-domains"></a>Домены приложений

Домены приложений позволяют изолировать приложения друг от друга. Для этих доменов требуется поддержка среды выполнения, при этом они требовательны к ресурсам. Создание дополнительных доменов приложений не поддерживается, и в будущем эта возможность не планируется. Для изоляции кода используйте в качестве альтернативы отдельные процессы или контейнеры. Для динамической загрузки сборок используйте класс <xref:System.Runtime.Loader.AssemblyLoadContext>.

Чтобы упростить перенос кода из .NET Framework, в .NET 5 и более поздних версий предоставляются некоторые рабочие области API <xref:System.AppDomain>. Некоторые API-интерфейсы работают без изменений (например, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), одни элементы не выполняют никаких действий (например, <xref:System.AppDomain.SetCachePath%2A>), а другие создают исключение <xref:System.PlatformNotSupportedException> (например, <xref:System.AppDomain.CreateDomain%2A>). Проверьте типы, используемые для [`System.AppDomain` источника ссылки](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) в [репозитории GitHub dotnet/runtime](https://github.com/dotnet/runtime). Убедитесь, что выбрана ветвь, соответствующая реализованной версии.

## <a name="remoting"></a>Удаленное взаимодействие

Удаленное взаимодействие .NET не поддерживается в .NET 5+ (и .NET Core). Архитектура удаленного взаимодействия .NET считается проблемной. Она используется для обмена данными между доменами приложений, которые больше не поддерживаются. Кроме того, для удаленного взаимодействия требуется поддержка среды выполнения, обслуживание которой обходится дорого.

Для взаимодействия между процессами вместо удаленного взаимодействия можно применять механизмы межпроцессного взаимодействия (IPC), например класс <xref:System.IO.Pipes> или <xref:System.IO.MemoryMappedFiles.MemoryMappedFile>.

Для взаимодействия между компьютерами в качестве альтернативы можно использовать сетевое решение, желательно протокол на основе обычного текста с низкими издержками, например HTTP. Еще один вариант — [веб-сервер Kestrel](/aspnet/core/fundamentals/servers/kestrel), используемый платформой ASP.NET Core. Кроме того, для сценариев взаимодействия между компьютерами по сети можно использовать пространство имен <xref:System.Net.Sockets>. Другие варианты см. в разделе об обмене сообщениями статьи [.NET Open Source Developer Projects ](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging) (Проекты разработки с открытым кодом в .NET).

## <a name="code-access-security-cas"></a>Управление доступом для кода

Песочница ограничивает ресурсы, используемые или выполняемые в управляемых приложениях или библиотеках, на основе среды выполнения или платформы. Она [не поддерживается в .NET Framework](../../framework/misc/code-access-security.md) и, следовательно, в .NET Core и .NET 5 и более поздних версий. Часто в .NET Framework и среде выполнения пользователи повышают привилегии, чтобы и дальше использовать CAS в качестве ограничения безопасности. Кроме того, механизм CAS усложняет реализацию и ухудшает производительность и работоспособность приложений, которые не планируют использовать его.

Чтобы свести к минимуму требуемый набор прав, применяйте ограничения безопасности, предусмотренные в операционной системе, например виртуализацию, контейнеры или учетные записи пользователей.

## <a name="security-transparency"></a>Прозрачность безопасности

Аналогично CAS, прозрачность безопасности позволяет декларативно отделить изолированный код от кода, критически важного с точки зрения безопасности, но [больше не поддерживается как ограничение безопасности](../../framework/misc/security-transparent-code.md). Эта функция часто используется в Silverlight.

Чтобы свести к минимуму требуемый набор прав, применяйте ограничения безопасности, предусмотренные в операционной системе, например виртуализацию, контейнеры или учетные записи пользователей.

## <a name="systementerpriseservices"></a>System.EnterpriseServices

<xref:System.EnterpriseServices?displayProperty=fullName> (COM+) не поддерживается в .NET Core и .NET 5+.

## <a name="workflow-foundation-and-wcf"></a>Workflow Foundation и WCF

Windows Workflow Foundation (WF) и Windows Communication Foundation (WCF) не поддерживаются в .NET 5+ (включая .NET Core). Альтернативные варианты см. в разделах [CoreWF](https://github.com/UiPath/corewf) и [CoreWCF](https://github.com/CoreWCF/CoreWCF).

## <a name="see-also"></a>См. также

- [Общие сведения о переносе кода в .NET Framework из .NET](index.md)
