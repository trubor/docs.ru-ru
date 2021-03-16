---
title: Предупреждение SYSLIB0005
description: Сведения об устаревших элементах, которые приводят к появлению предупреждения во время компиляции SYSLIB0005.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 9ed36d247d31bcebc499bd7ed3945490d9d901f9
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256376"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a><span data-ttu-id="59aa3-103">SYSLIB0005. Глобальный кэш сборок не поддерживается</span><span class="sxs-lookup"><span data-stu-id="59aa3-103">SYSLIB0005: The global assembly cache (GAC) is not supported</span></span>

<span data-ttu-id="59aa3-104">В .NET Core и .NET 5 и более поздних версий больше не используется концепция глобального кэша сборок, которая присутствует в .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59aa3-104">.NET Core and .NET 5 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="59aa3-105">Чтобы помочь разработчикам отказаться от этих API, некоторые связанные с глобальным кэшем сборок API были помечены как устаревшие, начиная с версии .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="59aa3-105">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="59aa3-106">При использовании этих API во время компиляции создается предупреждение `SYSLIB0005`.</span><span class="sxs-lookup"><span data-stu-id="59aa3-106">Using these APIs generates warning `SYSLIB0005` at compile time.</span></span>

<span data-ttu-id="59aa3-107">Следующие связанные с глобальным кэшем сборок API помечены как устаревшие:</span><span class="sxs-lookup"><span data-stu-id="59aa3-107">The following GAC-related APIs are marked obsolete:</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  <span data-ttu-id="59aa3-108">Библиотеки и приложения не должны использовать API <xref:System.Reflection.Assembly.GlobalAssemblyCache> для определения поведения во время выполнения, так как в .NET Core и .NET 5 и более поздних версий он всегда возвращает `false`.</span><span class="sxs-lookup"><span data-stu-id="59aa3-108">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5+.</span></span>

## <a name="workarounds"></a><span data-ttu-id="59aa3-109">Методы обхода проблемы</span><span class="sxs-lookup"><span data-stu-id="59aa3-109">Workarounds</span></span>

<span data-ttu-id="59aa3-110">Если приложение запрашивает свойство <xref:System.Reflection.Assembly.GlobalAssemblyCache>, рассмотрите возможность удалить вызов.</span><span class="sxs-lookup"><span data-stu-id="59aa3-110">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="59aa3-111">Если вы используете значение <xref:System.Reflection.Assembly.GlobalAssemblyCache> для выбора между потоками сборки в глобальном кэше сборок и вне него во время выполнения, еще раз оцените, требуется ли такой поток по-прежнему в приложении .NET 5 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="59aa3-111">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET 5+ application.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="59aa3-112">См. также</span><span class="sxs-lookup"><span data-stu-id="59aa3-112">See also</span></span>

- [<span data-ttu-id="59aa3-113">Глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="59aa3-113">Global assembly cache</span></span>](../../../framework/app-domains/gac.md)
