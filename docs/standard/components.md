---
title: Архитектурные компоненты .NET
description: Описание ключевых компонентов архитектуры .NET, таких как .NET Standard, реализации .NET, среды выполнения .NET и инструменты.
author: cartermp
ms.date: 10/05/2020
ms.openlocfilehash: d1780d8f85159c12ef4e11b2ac53091b61629352
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605325"
---
# <a name="net-architectural-components"></a>Архитектурные компоненты .NET

Приложение .NET разрабатывается и выполняется в одной *реализации .NET* или нескольких. К реализации .NET относятся .NET Framework, .NET 5 (и .NET Core) и Mono. Существует спецификация API, общая для нескольких реализаций .NET, которая называется .NET Standard. В этой статье дается краткое описание каждого из этих понятий.

## <a name="net-standard"></a>.NET Standard

.NET Standard — это набор API, которые реализуются библиотекой базовых классов реализации .NET. Фактически это спецификация API .NET, представляющая единый набор контрактов, на основе которых компилируется код. Эти контракты реализуются в нескольких реализациях .NET.

.NET Standard является [требуемой версией .NET Framework](glossary.md#target-framework). Если код предназначен для версии .NET Standard, он будет работать в любой реализации .NET, которая поддерживает эту версию .NET Standard.

Версия .NET Standard была создана с целью обеспечить возможности переноса между различными реализациями .NET, но теперь в .NET 5 предлагается лучший способ совместного использования кода для нескольких платформ и рабочих нагрузок. Дополнительные сведения см. в статье [.NET 5 и .NET Standard](net-standard.md#net-5-and-net-standard).

## <a name="net-implementations"></a>Реализации .NET

Каждая реализация .NET включает в себя следующие компоненты.

- Одна среда выполнения или несколько. Примеры: .NET Framework CLR, .NET 5 CLR.
- Библиотека классов. Примеры: библиотека базовых классов .NET Framework, библиотека базовых классов .NET 5.
- (Необязательно) Одна платформа приложений или несколько. Примеры [ASP.NET](https://www.asp.net/), [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview) и [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) входят в .NET Framework и .NET 5.
- (Необязательно) Средства разработки. Некоторые средства разработки, являются общими для нескольких реализаций.

Корпорация Майкрософт поддерживает четыре реализации .NET:

- .NET 5 (и .NET Core) и более поздние версии
- .NET Framework
- Mono
- UWP

На данный момент .NET 5 является основной реализацией, которая используется в текущих задачах разработки. Платформа .NET 5 построена на основе единой базы кода, которая поддерживает несколько платформ и множество рабочих нагрузок, таких как классические приложения Windows и кроссплатформенные консольные приложения, облачные службы и веб-сайты.

### <a name="net-5"></a>.NET 5

.NET 5 — это кроссплатформенная реализация .NET, предназначенная для обработки обширного ряда серверных и облачных рабочих нагрузок. Она также поддерживает и другие рабочие нагрузки, включая классические приложения. Это решение работает в Windows, macOS и Linux. Она реализует .NET Standard, а значит, любой код, предназначенный для .NET Standard, может работать на платформе .NET 5. [ASP.NET](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core), [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview) и [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) работают на основе .NET 5.

Дополнительные сведения см. в следующих ресурсах:

- [Общие сведения о платформе .NET](../core/introduction.md)
- [Выбор между .NET 5 и .NET Framework для серверных приложений](choosing-core-framework-server.md)
- [.NET 5 и .NET Standard](net-standard.md#net-5-and-net-standard)

### <a name="net-framework"></a>.NET Framework

.NET Framework является исходной реализацией .NET, выпущенной в 2002 г. Версии 4.5 и более поздние реализуют .NET Standard, а значит, любой код, предназначенный для .NET Standard, может работать в этих версиях .NET Framework. Она содержит дополнительные API для Windows, например API для разработки настольных приложений с помощью Windows Forms и WPF. .NET Framework оптимизирована для создания настольных приложений для Windows.

Дополнительные сведения см. в [руководстве по платформе .NET Framework](../framework/index.yml).

### <a name="mono"></a>Mono

Mono является реализацией .NET, которая в основном используется, если требуется небольшая среда выполнения. Это среда выполнения, которая может работать в приложениях Xamarin на Android, macOS, iOS, tvOS и watchOS и которая предназначена для небольших разработок. Mono также подходит для работы игр, созданных на базе подсистемы Unity.

Она поддерживает все текущие опубликованные версии .NET Standard.

Исторически Mono реализовывала крупный API .NET Framework и эмулировала некоторые из наиболее популярных возможностей в Unix. Иногда она использовалась для запуска приложений .NET, которые применяют эти возможности в Unix.

Mono обычно используется с JIT-компилятором, но также располагает полным статическим компилятором (заблаговременная компиляция), который используется на таких платформах, как iOS.

Дополнительные сведения см. в [документации по Mono](https://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Универсальная платформа Windows (UWP)

UWP представляет собой реализацию .NET, которая используется для создания современных приложений Windows с поддержкой сенсорного ввода и программного обеспечения для Интернета вещей (IoT). Она предназначена для объединения различных типов устройств, которые могут потребоваться, включая ПК, планшеты, телефоны и даже Xbox. UWP предоставляет много служб, таких как централизованный магазин приложений, среда выполнения (AppContainer) и набор API-интерфейсов Windows для использования вместо Win32 (WinRT). Приложения могут быть написаны на C++, C#, Visual Basic и JavaScript.

Дополнительные сведения см. в статье [Общие сведения об универсальной платформе Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Среды выполнения .NET

Среда выполнения — это среда выполнения для управляемой программы. Операционная система является частью среды выполнения, но не входит в среду выполнения .NET. Ниже приведены несколько примеров сред выполнения .NET.

- Среда CLR для .NET Framework
- Среда CLR для .NET 5
- .NET Native для универсальной платформы Windows
- Среда выполнения Mono для Xamarin.iOS, Xamarin.Android, Xamarin.Mac и платформы Mono для рабочего стола

## <a name="net-tooling-and-common-infrastructure"></a>Инструменты для .NET и общая инфраструктура

Вы можете использовать широкий набор средств и компонентов инфраструктуры, которые работают в каждой реализации платформы .NET. К этим средствам и компонентам относятся:

- языки .NET и соответствующие компиляторы;
- систему проектов .NET (на основе файлов *CSPROJ*, *VBPROJ* и *FSPROJ*);
- [MSBuild](/visualstudio/msbuild/msbuild), обработчик для сборки проектов;
- [NuGet](/nuget/), диспетчер пакетов корпорации Майкрософт для .NET;
- инструменты для управления сборкой с открытым исходным кодом, например [CAKE](https://cakebuild.net/) и [FAKE](https://fake.build/).

Дополнительные сведения см. в статье [Инструменты и производительность](../core/introduction.md#tools-and-productivity).

## <a name="applicable-standards"></a>Применимые стандарты

Спецификации языка C# и Common Language Infrastructure (CLI) стандартизированы в [ECMA&reg;](https://www.ecma-international.org/). Первые выпуски этих стандартов были опубликованы в Ecma в декабре 2001 г.

Последующие редакции стандартов были разработаны группами задач TC49-TG2 (C#) и TC49-TG3 (CLI) в рамках технического комитета по языкам программирования ([TC49](https://www.ecma-international.org/technical-committees/tc49/)) и приняты в Генеральной ассамблее Ecma и затем в ISO/IEC JTC 1 в рамках процесса ISO Fast-Track.

### <a name="latest-standards"></a>Новейшие стандарты

Следующие официальные документы Ecma доступны для [C#](https://www.ecma-international.org/publications-and-standards/standards/ecma-334/) и [CLI](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) ([TR-84](https://www.ecma-international.org/publications-and-standards/technical-reports/ecma-tr-84/)):

- **Стандарт языка C# (версия 5.0)** : [ECMA-334.pdf](https://www.ecma-international.org/wp-content/uploads/ECMA-334_5th_edition_december_2017.pdf)
- **Common Language Infrastructure**: [ECMA-335.pdf](https://www.ecma-international.org/wp-content/uploads/ECMA-335_6th_edition_june_2012.pdf).
- **Сведения, полученные из файла XML раздела IV**: Формат [ECMA-084.pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf).

Официальные документы ISO/IEC доступны на странице [общедоступных стандартов](https://standards.iso.org/ittf/PubliclyAvailableStandards/) ISO/IEC. Эти ссылки указываются непосредственно на этой странице:

- **Информационные технологии — языки программирования — C#** : [ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **Информационные технологии — Common Language Infrastructure (CLI), разделы I–VI**: [ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **Информационные технологии — Common Language Infrastructure (CLI) — технический отчет о данных, полученных из файла XML раздела IV**: [ISO/IEC TR 23272:2011](https://www.ecma-international.org/wp-content/uploads/ECMA_TR-84_6th_edition_june_2012.pdf)

## <a name="see-also"></a>См. также

- [Общие сведения о платформе .NET](../core/introduction.md)
- [.NET Standard](net-standard.md)
- [Выбор между .NET 5 и .NET Framework для серверных приложений](choosing-core-framework-server.md)
- [Руководство по .NET Framework](../framework/index.yml)
- [Руководство по языку C#](../csharp/index.yml)
- [Руководство по языку F#](../fsharp/index.yml)
- [Руководство по Visual Basic](../visual-basic/index.yml)
