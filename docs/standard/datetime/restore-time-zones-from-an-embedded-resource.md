---
description: Дополнительные сведения о том, как восстановить Часовые пояса из внедренного ресурса.
title: Практическое руководство. Восстановление часовых поясов из внедренного ресурса
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], deserializing
- time zones [.NET], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: 593fb392c073ca0a3b557b7d82d430b024b3d13a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702487"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="6d674-103">Практическое руководство. Восстановление часовых поясов из внедренного ресурса</span><span class="sxs-lookup"><span data-stu-id="6d674-103">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="6d674-104">В этом разделе описывается восстановление часовых поясов, сохраненных в файле ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6d674-104">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="6d674-105">Сведения и инструкции по сохранению часовых поясов см. в статье [как сохранить Часовые пояса во внедренном ресурсе](save-time-zones-to-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="6d674-105">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="6d674-106">Десериализация объекта TimeZoneInfo из внедренного ресурса</span><span class="sxs-lookup"><span data-stu-id="6d674-106">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="6d674-107">Если часовой пояс для извлечения не является пользовательским часовым поясом, попробуйте создать его экземпляр с помощью <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="6d674-107">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="6d674-108">Создайте экземпляр <xref:System.Resources.ResourceManager> объекта, передав полное имя внедренного файла ресурсов и ссылку на сборку, содержащую файл ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6d674-108">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="6d674-109">Если не удается определить полное имя внедренного файла ресурсов, используйте [Ildasm.exe (IL-файл)](../../framework/tools/ildasm-exe-il-disassembler.md) для проверки манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="6d674-109">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="6d674-110">`.mresource`Запись идентифицирует ресурс.</span><span class="sxs-lookup"><span data-stu-id="6d674-110">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="6d674-111">В этом примере полное имя ресурса — `SerializeTimeZoneData.SerializedTimeZones` .</span><span class="sxs-lookup"><span data-stu-id="6d674-111">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="6d674-112">Если файл ресурсов внедрен в ту же сборку, которая содержит код создания экземпляра часового пояса, можно получить ссылку на него, вызвав `static` `Shared` метод (в Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> .</span><span class="sxs-lookup"><span data-stu-id="6d674-112">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="6d674-113">Если вызов <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> метода завершается с ошибкой или если требуется создать пользовательский часовой пояс, извлеките строку, содержащую сериализованный часовой пояс, вызвав <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="6d674-113">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="6d674-114">Десериализация данных часового пояса путем вызова <xref:System.TimeZoneInfo.FromSerializedString%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="6d674-114">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="6d674-115">Пример</span><span class="sxs-lookup"><span data-stu-id="6d674-115">Example</span></span>

<span data-ttu-id="6d674-116">В следующем примере десериализуется <xref:System.TimeZoneInfo> объект, хранящийся во внедренном XML-файле ресурсов .NET.</span><span class="sxs-lookup"><span data-stu-id="6d674-116">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="6d674-117">Этот код иллюстрирует обработку исключений, чтобы убедиться в <xref:System.TimeZoneInfo> наличии объекта, требуемого для приложения.</span><span class="sxs-lookup"><span data-stu-id="6d674-117">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="6d674-118">Сначала он пытается создать экземпляр <xref:System.TimeZoneInfo> объекта, извлекая его из реестра с помощью <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="6d674-118">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="6d674-119">Если не удается создать экземпляр часового пояса, код извлекает его из файла внедренных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6d674-119">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="6d674-120">Поскольку данные для пользовательских часовых поясов (часовые пояса, созданные с помощью <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> метода) не хранятся в реестре, код не вызывает метод <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> для создания экземпляра часового пояса для Палмер, Антарктида.</span><span class="sxs-lookup"><span data-stu-id="6d674-120">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="6d674-121">Вместо этого он сразу же обращается к внедренному файлу ресурсов для получения строки, содержащей данные часового пояса перед вызовом <xref:System.TimeZoneInfo.FromSerializedString%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="6d674-121">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="6d674-122">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="6d674-122">Compiling the code</span></span>

<span data-ttu-id="6d674-123">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="6d674-123">This example requires:</span></span>

- <span data-ttu-id="6d674-124">Для добавления в проект ссылки на System.Windows.Forms.dll и System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="6d674-124">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="6d674-125">Для импорта следующих пространств имен:</span><span class="sxs-lookup"><span data-stu-id="6d674-125">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="6d674-126">См. также</span><span class="sxs-lookup"><span data-stu-id="6d674-126">See also</span></span>

- [<span data-ttu-id="6d674-127">Даты, время и часовые пояса</span><span class="sxs-lookup"><span data-stu-id="6d674-127">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="6d674-128">Общие сведения о часовых поясах</span><span class="sxs-lookup"><span data-stu-id="6d674-128">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="6d674-129">Как сохранять Часовые пояса во внедренном ресурсе</span><span class="sxs-lookup"><span data-stu-id="6d674-129">How to: Save time zones to an embedded resource</span></span>](save-time-zones-to-an-embedded-resource.md)
