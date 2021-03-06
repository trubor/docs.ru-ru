---
title: Сравнение ASP.NET Identity и ASP.NET Core удостоверений
description: В этом разделе рассматриваются различия между ASP.NET Identity и ASP.NET Core удостоверениями, которые особенно важны при планировании миграции с платформа .NET Framework на .NET Core.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 184c0e7c872b7676530b917727f380d6735ba10a
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401762"
---
# <a name="compare-aspnet-identity-and-aspnet-core-identity"></a><span data-ttu-id="58521-103">Сравнение ASP.NET Identity и ASP.NET Core удостоверений</span><span class="sxs-lookup"><span data-stu-id="58521-103">Compare ASP.NET Identity and ASP.NET Core Identity</span></span>

<span data-ttu-id="58521-104">В ASP.NET MVC функции идентификации обычно настраиваются в *IdentityConfig.CS* в папке *App_Start* .</span><span class="sxs-lookup"><span data-stu-id="58521-104">In ASP.NET MVC, identity features are typically configured in *IdentityConfig.cs* in the *App_Start* folder.</span></span> <span data-ttu-id="58521-105">Ознакомьтесь с тем, как это настроить в существующем приложении, и сравните его с [конфигурацией, необходимой для ASP.NET Core удостоверения](/aspnet/core/security/authentication/identity-configuration) в *Startup.CS*.</span><span class="sxs-lookup"><span data-stu-id="58521-105">Review how this is configured in the existing app, and compare it to the [configuration required for ASP.NET Core Identity](/aspnet/core/security/authentication/identity-configuration) in *Startup.cs*.</span></span>

<span data-ttu-id="58521-106">ASP.NET Identity — это API, который поддерживает функции входа в интерфейс пользователя и управляет пользователями, паролями, данными профилирования, ролями, утверждениями, маркерами, подтверждениями по электронной почте и т. д.</span><span class="sxs-lookup"><span data-stu-id="58521-106">ASP.NET Identity is an API that supports user interface login functionality and manages users, passwords, profile data, roles, claims, tokens, email confirmations, and more.</span></span> <span data-ttu-id="58521-107">Он поддерживает внешние поставщики входа в систему, такие как Facebook, Google, Microsoft и Twitter.</span><span class="sxs-lookup"><span data-stu-id="58521-107">It supports external login providers like Facebook, Google, Microsoft, and Twitter.</span></span>

<span data-ttu-id="58521-108">Если приложение ASP.NET MVC использует членство в ASP.NET, вы найдете инструкции по [переносу из ASP.NET членства с проверкой подлинности в удостоверение ASP.NET Core 2,0](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span><span class="sxs-lookup"><span data-stu-id="58521-108">If your ASP.NET MVC app is using ASP.NET Membership, you'll find a guide to [migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="58521-109">Это, в первую очередь, упражнение по переносу данных, при котором вы сможете использовать удостоверение ASP.NET Core с перенесенными записями пользователей.</span><span class="sxs-lookup"><span data-stu-id="58521-109">This is mainly a data migration exercise, at the completion of which you should be able to use ASP.NET Core Identity with your migrated user records.</span></span>

<span data-ttu-id="58521-110">Если вы переносите ASP.NET Identity пользователей на ASP.NET Core Identity, может потребоваться обновить хэши паролей или определить, какие пароли хэшированы с помощью нового подхода ASP.NET Core идентификации или более старого ASP.NET Identity.</span><span class="sxs-lookup"><span data-stu-id="58521-110">If you migrate your ASP.NET Identity users to ASP.NET Core Identity, you may need to update their password hashes, or track which passwords are hashed with the new ASP.NET Core Identity approach or the older ASP.NET Identity approach.</span></span> <span data-ttu-id="58521-111">[Этот подход, описанный в Stack overflow](https://stackoverflow.com/a/57074910/13729) , предоставляет несколько вариантов для переноса хэшей паролей пользователей с течением времени, а не всего за один раз.</span><span class="sxs-lookup"><span data-stu-id="58521-111">[This approach described on Stack Overflow](https://stackoverflow.com/a/57074910/13729) provides some options for migrating user password hashes over time, rather than all at once.</span></span>

<span data-ttu-id="58521-112">Одно из крупнейших различий в том, что ASP.NET Core удостоверение по сравнению с ASP.NET Identity, — это немало кода, который нужно включить в проект.</span><span class="sxs-lookup"><span data-stu-id="58521-112">One of the biggest differences when it comes to ASP.NET Core Identity compared to ASP.NET Identity is how little code you need to include in your project.</span></span> <span data-ttu-id="58521-113">ASP.NET Core удостоверение теперь поставляется как библиотека классов Razor, то есть все его интерфейсы и логика доступны из пакета NuGet.</span><span class="sxs-lookup"><span data-stu-id="58521-113">ASP.NET Core Identity now ships as a Razor Class Library, meaning its UI and logic are all available from a NuGet package.</span></span> <span data-ttu-id="58521-114">Существующий пользовательский интерфейс и логику можно переопределить путем [формирования шаблонов ASP.NET Core файлов удостоверений](/aspnet/core/security/authentication/scaffold-identity) , но даже в этом случае необходимо только сформировать страницы, которые нужно изменить, а не все существующие.</span><span class="sxs-lookup"><span data-stu-id="58521-114">You can override the existing UI and logic by [scaffolding the ASP.NET Core Identity files](/aspnet/core/security/authentication/scaffold-identity) but even in this case you need only scaffold the pages you want to modify, not every one that exists.</span></span>

## <a name="migrate-from-owin--katana"></a><span data-ttu-id="58521-115">Миграция из OWIN или Katana</span><span class="sxs-lookup"><span data-stu-id="58521-115">Migrate from OWIN / Katana</span></span>

<span data-ttu-id="58521-116">В следующих ресурсах представлены некоторые рекомендации по миграции из OWIN/Katana.</span><span class="sxs-lookup"><span data-stu-id="58521-116">The following resources offer some guidance for migrating from OWIN / Katana:</span></span>

- [<span data-ttu-id="58521-117">Миграция</span><span class="sxs-lookup"><span data-stu-id="58521-117">Migration</span></span>](/aspnet/core/migration/proper-to-2x/#globalasax-file-replacement)
- [<span data-ttu-id="58521-118">Katana в ASPNET 5</span><span class="sxs-lookup"><span data-stu-id="58521-118">Katana to ASPNET 5</span></span>](https://devblogs.microsoft.com/aspnet/katana-asp-net-5-and-bridging-the-gap/)

## <a name="references"></a><span data-ttu-id="58521-119">Ссылки</span><span class="sxs-lookup"><span data-stu-id="58521-119">References</span></span>

- [<span data-ttu-id="58521-120">Перенесите проверку подлинности и удостоверение в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="58521-120">Migrate Authentication and Identity to ASP.NET Core</span></span>](/aspnet/core/migration/identity)
- [<span data-ttu-id="58521-121">Введение в удостоверение на ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="58521-121">Introduction to Identity on ASP.NET Core</span></span>](/aspnet/core/security/authorization/introduction)
- [<span data-ttu-id="58521-122">Настройка удостоверения ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="58521-122">Configure ASP.NET Core Identity</span></span>](/aspnet/core/security/authentication/identity-configuration)
- [<span data-ttu-id="58521-123">Удостоверение шаблона в ASP.NET Core проектах</span><span class="sxs-lookup"><span data-stu-id="58521-123">Scaffold Identity in ASP.NET Core projects</span></span>](/aspnet/core/security/authentication/scaffold-identity)

>[!div class="step-by-step"]
><span data-ttu-id="58521-124">[Назад](authentication-differences.md)
>[Вперед](controller-differences.md)</span><span class="sxs-lookup"><span data-stu-id="58521-124">[Previous](authentication-differences.md)
[Next](controller-differences.md)</span></span>
