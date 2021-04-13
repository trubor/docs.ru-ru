---
title: 'Критическое изменение. Blazor: Обновленная логика проверки для статических веб-ресурсов'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Blazor. Обновленная логика проверки для статических веб-ресурсов
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b6fb8e9a10157a97119fa07a95fb3dbb8b207214
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498156"
---
# <a name="blazor-updated-validation-logic-for-static-web-assets"></a><span data-ttu-id="c8f23-103">Blazor: Обновленная логика проверки для статических веб-ресурсов</span><span class="sxs-lookup"><span data-stu-id="c8f23-103">Blazor: Updated validation logic for static web assets</span></span>

<span data-ttu-id="c8f23-104">При проверке конфликтов для статических веб-ресурсов в ASP.NET Core 3.1 и Blazor WebAssembly 3.2 возникала ошибка.</span><span class="sxs-lookup"><span data-stu-id="c8f23-104">There was an issue in conflict validation for static web assets in ASP.NET Core 3.1 and Blazor WebAssembly 3.2.</span></span> <span data-ttu-id="c8f23-105">Эта ошибка:</span><span class="sxs-lookup"><span data-stu-id="c8f23-105">The issue:</span></span>

* <span data-ttu-id="c8f23-106">Не позволяла правильно обнаружить конфликты между ресурсами узла и ресурсами из библиотеки классов Razor (RCL) и приложениями Blazor WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="c8f23-106">Prevented proper conflict detection between the host assets and assets from Razor Class Libraries (RCLs) and Blazor WebAssembly apps.</span></span>
* <span data-ttu-id="c8f23-107">В основном влияет на приложения Blazor WebAssembly, поскольку статические веб-ресурсы в RCL обрабатываются по префиксу `_content/$(PackageId)`.</span><span class="sxs-lookup"><span data-stu-id="c8f23-107">Mostly affects Blazor WebAssembly apps, since by default, static web assets in RCLs are served under the `_content/$(PackageId)` prefix.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c8f23-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="c8f23-108">Version introduced</span></span>

<span data-ttu-id="c8f23-109">5.0</span><span class="sxs-lookup"><span data-stu-id="c8f23-109">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="c8f23-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="c8f23-110">Old behavior</span></span>

<span data-ttu-id="c8f23-111">Во время разработки статические веб-ресурсы RCL могут быть автоматически переопределены с помощью ресурсов основного проекта по одному и тому же пути к узлу.</span><span class="sxs-lookup"><span data-stu-id="c8f23-111">During development, an RCL's static web assets could be silently overridden with host project assets on the same host path.</span></span> <span data-ttu-id="c8f23-112">Рассмотрим RCL, который определил статический веб-ресурс для обслуживания по адресу */folder/file.txt*.</span><span class="sxs-lookup"><span data-stu-id="c8f23-112">Consider an RCL that has defined a static web asset to be served at */folder/file.txt*.</span></span> <span data-ttu-id="c8f23-113">Если узел поместил файл в папку *wwwroot/Folder/File. txt*, то файл на сервере автоматически был переопределен в RCL или приложении Blazor WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="c8f23-113">If the host placed a file at *wwwroot/folder/file.txt*, the file on the server silently overrode the file on the RCL or Blazor WebAssembly app.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="c8f23-114">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="c8f23-114">New behavior</span></span>

<span data-ttu-id="c8f23-115">ASP.NET Core правильно определяет, когда возникает эта проблема.</span><span class="sxs-lookup"><span data-stu-id="c8f23-115">ASP.NET Core correctly detects when this issue happens.</span></span> <span data-ttu-id="c8f23-116">Он информирует пользователя о конфликте, чтобы вы могли предпринять соответствующие действия.</span><span class="sxs-lookup"><span data-stu-id="c8f23-116">It informs you, the user, of the conflict so that you can take the appropriate action.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="c8f23-117">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="c8f23-117">Reason for change</span></span>

<span data-ttu-id="c8f23-118">Статические веб-ресурсы не предназначены для переопределения файлами на узле *wwwroot* проекта.</span><span class="sxs-lookup"><span data-stu-id="c8f23-118">Static web assets weren't intended to be overridable by files on the *wwwroot* host of the project.</span></span> <span data-ttu-id="c8f23-119">Если разрешить переопределение этих файлов, могут возникать ошибки, которые трудно диагностировать.</span><span class="sxs-lookup"><span data-stu-id="c8f23-119">Allowing for the overriding of those files could lead to errors that are difficult to diagnose.</span></span> <span data-ttu-id="c8f23-120">В результате могут возникнуть неопределенные изменения поведения в опубликованных приложениях.</span><span class="sxs-lookup"><span data-stu-id="c8f23-120">The result could be undefined behavior changes in published apps.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c8f23-121">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="c8f23-121">Recommended action</span></span>

<span data-ttu-id="c8f23-122">По умолчанию причины для возникновения конфликтов файла RCL с файлом на узле отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="c8f23-122">By default, there's no reason for an RCL file to conflict with a file on the host.</span></span> <span data-ttu-id="c8f23-123">Файлы RCL имеют префикс `_content/${PackageId}`.</span><span class="sxs-lookup"><span data-stu-id="c8f23-123">RCL files are prefixed with `_content/${PackageId}`.</span></span> <span data-ttu-id="c8f23-124">Файлы Blazor WebAssembly размещаются в корне пространства URL-адресов узла, что исключает конфликты.</span><span class="sxs-lookup"><span data-stu-id="c8f23-124">Blazor WebAssembly files are placed at the root of the host URL space, which makes conflicts easier.</span></span> <span data-ttu-id="c8f23-125">Например, приложения Blazor WebAssembly содержат файл *favicon.ico*, который узел может также включить в папку *wwwroot*.</span><span class="sxs-lookup"><span data-stu-id="c8f23-125">For example, Blazor WebAssembly apps contain a *favicon.ico* file that the host might also include in its *wwwroot* folder.</span></span>

<span data-ttu-id="c8f23-126">Если источником конфликта является файл RCL, это часто означает, что код копирует ресурсы из библиотеки в папку *wwwroot* проекта.</span><span class="sxs-lookup"><span data-stu-id="c8f23-126">If the conflict's source is an RCL file, it often means code is copying assets from the library into the project's *wwwroot* folder.</span></span> <span data-ttu-id="c8f23-127">Написание кода для копирования файлов позволяет достичь основной цели статических веб-ресурсов.</span><span class="sxs-lookup"><span data-stu-id="c8f23-127">Writing code to copy files defeats a primary goal of static web assets.</span></span> <span data-ttu-id="c8f23-128">Эта цель заключается в получении обновлений в браузере при обновлении содержимого без активации новой компиляции.</span><span class="sxs-lookup"><span data-stu-id="c8f23-128">This goal is fundamental to get updates on the browser when the contents are updated without having to trigger a new compilation.</span></span>

<span data-ttu-id="c8f23-129">Вы можете сохранить это поведение и хранить файл на узле.</span><span class="sxs-lookup"><span data-stu-id="c8f23-129">You may choose to preserve this behavior and maintain the file on the host.</span></span> <span data-ttu-id="c8f23-130">Для этого удалите файл из списка статических веб-ресурсов с настраиваемым целевым объектом MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c8f23-130">To do so, remove the file from the list of static web assets with a custom MSBuild target.</span></span>

<span data-ttu-id="c8f23-131">Чтобы использовать файл RCL или файл Blazor WebAssembly вместо файла основного проекта, удалите файл из основного проекта.</span><span class="sxs-lookup"><span data-stu-id="c8f23-131">To use the RCL's file or the Blazor WebAssembly app's file instead of the host project's file, remove the file from the host project.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c8f23-132">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="c8f23-132">Affected APIs</span></span>

<span data-ttu-id="c8f23-133">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="c8f23-133">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
