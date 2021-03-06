---
title: Сравнение использования Razor в ASP.NET MVC и ASP.NET Core
description: Чем Razor отличается между ASP.NET MVC и ASP.NET Core?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: a9f7fa2e6b8c0c6bf61c743cf8c956b1ad09713c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401720"
---
# <a name="compare-razor-usage-in-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="4dd22-103">Сравнение использования Razor в ASP.NET MVC и ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4dd22-103">Compare Razor usage in ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="4dd22-104">Базовый синтаксис Razor не существенно изменился между ASP.NET MVC и ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4dd22-104">The basic syntax of Razor hasn't changed substantially between ASP.NET MVC and ASP.NET Core.</span></span> <span data-ttu-id="4dd22-105">Однако существуют некоторые отличия, такие как ввод [вспомогательных функций тегов](/aspnet/core/mvc/views/tag-helpers/intro) и Razor Pages, которые следует учитывать при миграции.</span><span class="sxs-lookup"><span data-stu-id="4dd22-105">However, there are certain differences, such as the introduction of [Tag Helpers](/aspnet/core/mvc/views/tag-helpers/intro) and Razor Pages, that should be considered when migrating.</span></span> <span data-ttu-id="4dd22-106">Если приложение активно использует пользовательские функции Razor, обратитесь к [Справочнику по синтаксис Razor для ASP.NET Core](/aspnet/core/razor-pages) , чтобы узнать, какие изменения могут потребоваться при миграции на ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4dd22-106">If your app makes heavy use of custom Razor functionality, refer to the [Razor syntax reference for ASP.NET Core](/aspnet/core/razor-pages) to see what changes may be required when you migrate to ASP.NET Core.</span></span>

## <a name="tag-helpers"></a><span data-ttu-id="4dd22-107">Вспомогательные функции тегов</span><span class="sxs-lookup"><span data-stu-id="4dd22-107">Tag Helpers</span></span>

<span data-ttu-id="4dd22-108">Вспомогательные функции тегов позволяют серверному коду участвовать в создании и отрисовке HTML-элементов в файлах Razor.</span><span class="sxs-lookup"><span data-stu-id="4dd22-108">Tag Helpers enable server-side code to participate in creating and rendering HTML elements in Razor files.</span></span> <span data-ttu-id="4dd22-109">Они предлагают множество преимуществ по сравнению со вспомогательными классами HTML и должны использоваться вместо вспомогательных функций HTML везде, где это возможно.</span><span class="sxs-lookup"><span data-stu-id="4dd22-109">They offer many advantages over HTML Helpers and should be used in place of HTML Helpers wherever possible.</span></span> <span data-ttu-id="4dd22-110">Они предоставляют удобный для HTML процесс разработки, поскольку они выглядят как стандартные HTML и игнорируются большинством средств, предназначенных для редактирования HTML.</span><span class="sxs-lookup"><span data-stu-id="4dd22-110">They provide an HTML-friendly development experience, since they look like standard HTML and are ignored by most tooling designed to edit HTML.</span></span> <span data-ttu-id="4dd22-111">В _Visual Studio_ имеется широкая поддержка IntelliSense для создания разметки HTML и Razor с помощью вспомогательных функций тегов.</span><span class="sxs-lookup"><span data-stu-id="4dd22-111">Within _Visual Studio_, there's rich IntelliSense support for creating HTML and Razor markup with Tag Helpers.</span></span> <span data-ttu-id="4dd22-112">Вспомогательные функции тегов могут обеспечить простое или сложное поведение из декларативной разметки в файлах Razor.</span><span class="sxs-lookup"><span data-stu-id="4dd22-112">Tag Helpers can provide simple or complex behavior from declarative markup in Razor files.</span></span>

## <a name="razor-pages"></a><span data-ttu-id="4dd22-113">Razor Pages</span><span class="sxs-lookup"><span data-stu-id="4dd22-113">Razor Pages</span></span>

<span data-ttu-id="4dd22-114">Razor Pages предлагают альтернативы контроллерам, действиям и представлениям для приложений на основе страниц и форм.</span><span class="sxs-lookup"><span data-stu-id="4dd22-114">Razor Pages offer an alternative to controllers, actions, and views for page- and form-based apps.</span></span> <span data-ttu-id="4dd22-115">[В этой главе Razor Pages было сравнивалось с ASP.NET MVC ранее](./comparing-razor-pages-aspnet-mvc.md).</span><span class="sxs-lookup"><span data-stu-id="4dd22-115">[Razor Pages were compared to ASP.NET MVC earlier in this chapter](./comparing-razor-pages-aspnet-mvc.md).</span></span>

## <a name="references"></a><span data-ttu-id="4dd22-116">Ссылки</span><span class="sxs-lookup"><span data-stu-id="4dd22-116">References</span></span>

- [<span data-ttu-id="4dd22-117">Миграция с ASP.NET MVC на ASP.NET Core MVC: контроллеры и представления</span><span class="sxs-lookup"><span data-stu-id="4dd22-117">Migrate from ASP.NET MVC to ASP.NET Core MVC: Controllers and Views</span></span>](/aspnet/core/migration/mvc#migrate-controllers-and-views)
- [<span data-ttu-id="4dd22-118">Вспомогательные функции тегов в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4dd22-118">Tag Helpers in ASP.NET Core</span></span>](/aspnet/core/mvc/views/tag-helpers/intro)
- [<span data-ttu-id="4dd22-119">Введение в Razor Pages в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4dd22-119">Introduction to Razor Pages in ASP.NET Core</span></span>](/aspnet/core/razor-pages)
- [<span data-ttu-id="4dd22-120">Справочник по синтаксису Razor для ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4dd22-120">Razor syntax reference for ASP.NET Core</span></span>](/aspnet/core/razor-pages)

>[!div class="step-by-step"]
><span data-ttu-id="4dd22-121">[Назад](controller-differences.md)
>[Вперед](signalr-differences.md)</span><span class="sxs-lookup"><span data-stu-id="4dd22-121">[Previous](controller-differences.md)
[Next](signalr-differences.md)</span></span>
