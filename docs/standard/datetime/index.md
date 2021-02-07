---
description: 'Дополнительные сведения: даты, время и часовые пояса'
title: Даты, время и часовые пояса
ms.date: 04/10/2017
helpviewer_keywords:
- time zone objects [.NET]
- date and time data [.NET]
- time zones [.NET]
- times [.NET], time zones
- time [.NET], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
ms.openlocfilehash: d991e43a9ee816885b41ec4c9cc28df644c87957
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702630"
---
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="68bd5-103">Даты, время и часовые пояса</span><span class="sxs-lookup"><span data-stu-id="68bd5-103">Dates, times, and time zones</span></span>

<span data-ttu-id="68bd5-104">В дополнение к основной структуре <xref:System.DateTime> платформа .NET предоставляет следующие классы, которые поддерживают работу с часовыми поясами.</span><span class="sxs-lookup"><span data-stu-id="68bd5-104">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="68bd5-105">Этот класс используется для работы с локальным часовым поясом и с временем в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="68bd5-105">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.</span></span> <span data-ttu-id="68bd5-106">Функциональные возможности класса в <xref:System.TimeZone> основном заменяются <xref:System.TimeZoneInfo> классом.</span><span class="sxs-lookup"><span data-stu-id="68bd5-106">The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="68bd5-107">Этот класс используется для работы с любым часовым поясом, который является стандартным в системе, для создания новых часовых поясов и для быстрого преобразования значений даты и времени из одного часового пояса в другой.</span><span class="sxs-lookup"><span data-stu-id="68bd5-107">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="68bd5-108">При разработке нового решения используйте класс <xref:System.TimeZoneInfo> вместо класса <xref:System.TimeZone>.</span><span class="sxs-lookup"><span data-stu-id="68bd5-108">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="68bd5-109">Эта структура используется для работы с датами и временем, чье смещение (или различие) от времени в формате UTC известно.</span><span class="sxs-lookup"><span data-stu-id="68bd5-109">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="68bd5-110">Структура <xref:System.DateTimeOffset> объединяет значение даты и времени со смещением этого времени от времени в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="68bd5-110">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="68bd5-111">Благодаря связи со временем в формате UTC отдельное значение даты и времени однозначно идентифицирует единственный момент времени.</span><span class="sxs-lookup"><span data-stu-id="68bd5-111">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="68bd5-112">Это делает значение <xref:System.DateTimeOffset> более пригодным для переноса с одного компьютера на другой, чем значение <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="68bd5-112">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="68bd5-113">Этот раздел документации содержит сведения, необходимые для работы с часовыми поясами и создания приложений, поддерживающих часовые пояса и способных преобразовывать дату и время из одного часового пояса в другой.</span><span class="sxs-lookup"><span data-stu-id="68bd5-113">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="68bd5-114">Содержание раздела</span><span class="sxs-lookup"><span data-stu-id="68bd5-114">In this section</span></span>

<span data-ttu-id="68bd5-115">[Общие сведения о часовых поясах](time-zone-overview.md) Описание терминологии, основных понятий и вопросов, связанных с созданием приложений, поддерживающих часовые пояса.</span><span class="sxs-lookup"><span data-stu-id="68bd5-115">[Time zone overview](time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="68bd5-116">[Выбор между типами datetime, DateTimeOffset, TimeSpan и TimeZoneInfo](choosing-between-datetime.md) Описывает, когда следует использовать <xref:System.DateTime> типы, <xref:System.DateTimeOffset> и <xref:System.TimeZoneInfo> при работе с данными даты и времени.</span><span class="sxs-lookup"><span data-stu-id="68bd5-116">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="68bd5-117">[Поиск часового пояса, заданного в локальной системе](finding-the-time-zones-on-local-system.md). Описание того, как перечислять часовые пояса, находящиеся в локальной системе.</span><span class="sxs-lookup"><span data-stu-id="68bd5-117">[Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="68bd5-118">[Практическое руководство. Перечисление присутствующих на компьютере часовых поясов](enumerate-time-zones.md). Примеры, в которых перечисляются часовые пояса, определенные в реестре компьютера, и которые предоставляют пользователям возможность выбрать предопределенный часовой пояс из списка.</span><span class="sxs-lookup"><span data-stu-id="68bd5-118">[How to: Enumerate time zones present on a computer](enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="68bd5-119">[Практическое руководство. Доступ к предварительно определенным объектам UTC и объектам местных часовых поясов](access-utc-and-local.md). Описание способов доступа ко времени в формате UTC и локальному часовому поясу.</span><span class="sxs-lookup"><span data-stu-id="68bd5-119">[How to: Access the predefined UTC and local time zone objects](access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="68bd5-120">[Практическое руководство. Создание экземпляра объекта TimeZoneInfo](instantiate-time-zone-info.md). Описание способов создания экземпляра объекта <xref:System.TimeZoneInfo> из локального системного реестра.</span><span class="sxs-lookup"><span data-stu-id="68bd5-120">[How to: Instantiate a TimeZoneInfo object](instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="68bd5-121">[Создание экземпляра объекта DateTimeOffset](instantiating-a-datetimeoffset-object.md). Описание способов, с помощью которых можно создать экземпляр объекта <xref:System.DateTimeOffset> и преобразовать значение <xref:System.DateTime> в значение <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="68bd5-121">[Instantiating a DateTimeOffset object](instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="68bd5-122">[Практическое руководство. Создание часовых поясов без правил коррекции](create-time-zones-without-adjustment-rules.md). Описание того, как можно создать пользовательский часовой пояс, который не поддерживает переход на летнее время и обратно.</span><span class="sxs-lookup"><span data-stu-id="68bd5-122">[How to: Create time zones without adjustment rules](create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="68bd5-123">[Практическое руководство. Создание часовых поясов с правилами коррекции](create-time-zones-with-adjustment-rules.md). Описание того, как можно создать пользовательский часовой пояс, который поддерживает переход на летнее время и обратно.</span><span class="sxs-lookup"><span data-stu-id="68bd5-123">[How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="68bd5-124">[Сохранение и восстановление часовых поясов](saving-and-restoring-time-zones.md). Описание сериализации и десериализации данных часового пояса в <xref:System.TimeZoneInfo> и демонстрация некоторых сценариев, в которых эти функции могут использоваться.</span><span class="sxs-lookup"><span data-stu-id="68bd5-124">[Saving and restoring time zones](saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="68bd5-125">[Практическое руководство. Сохранение часовых поясов во внедренном ресурсе](save-time-zones-to-an-embedded-resource.md). Описание того, как создать пользовательский часовой пояс и сохранить связанные сведения в файле ресурсов.</span><span class="sxs-lookup"><span data-stu-id="68bd5-125">[How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="68bd5-126">[Практическое руководство. Восстановление часовых поясов из внедренного ресурса](restore-time-zones-from-an-embedded-resource.md). Описание того, как восстановить пользовательский часовой пояс, сохраненный в файл ресурсов.</span><span class="sxs-lookup"><span data-stu-id="68bd5-126">[How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="68bd5-127">[Выполнение арифметических операций с датами и временем](performing-arithmetic-operations.md). Обзор вопросов, связанных со сложением, вычитанием и сравнением значений <xref:System.DateTime> и <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="68bd5-127">[Performing arithmetic operations with dates and times](performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="68bd5-128">[Практическое руководство. Использование часовых поясов в арифметических операциях с датами и временем](use-time-zones-in-arithmetic.md). Описание того, как выполнять с датами и временем арифметические действия, которые отражают правила коррекции часовых поясов.</span><span class="sxs-lookup"><span data-stu-id="68bd5-128">[How to: Use time zones in date and time arithmetic](use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="68bd5-129">[Взаимное преобразование структур DateTime и DateTimeOffset](converting-between-datetime-and-offset.md). Описание преобразований между значениями <xref:System.DateTime> и <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="68bd5-129">[Converting between DateTime and DateTimeOffset](converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="68bd5-130">[Преобразование времени из одного часового пояса в другой](converting-between-time-zones.md). Описание того, как преобразовать время из одного часового пояса в другой.</span><span class="sxs-lookup"><span data-stu-id="68bd5-130">[Converting times between time zones](converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="68bd5-131">[Практическое руководство. Разрешение проблемы неоднозначности времени](resolve-ambiguous-times.md). Сведения об устранении неоднозначного времени с помощью его сопоставления с часовым поясом стандартного времени.</span><span class="sxs-lookup"><span data-stu-id="68bd5-131">[How to: Resolve ambiguous times](resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="68bd5-132">[Практическое руководство. Предоставление пользователям возможности разрешения неоднозначности времени](let-users-resolve-ambiguous-times.md) Сведения о том, как позволить пользователю определять сопоставление между неоднозначными местным временем и временем в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="68bd5-132">[How to: Let users resolve ambiguous times](let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="68bd5-133">Справочник</span><span class="sxs-lookup"><span data-stu-id="68bd5-133">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
