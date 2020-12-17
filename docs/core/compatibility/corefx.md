---
title: Критические изменения в библиотеке .NET
description: Список критических изменений в основных библиотеках .NET для .NET Core версий 1.0–3.0.
ms.date: 07/27/2020
ms.openlocfilehash: 092ff36a5e07c9e226fe2a67d5e7cfd391e9d16b
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366886"
---
# <a name="core-net-libraries-breaking-changes-in-net-core-10-30"></a><span data-ttu-id="9ab31-103">Критические изменения в основных библиотеках .NET Core версий 1.0–3.0.</span><span class="sxs-lookup"><span data-stu-id="9ab31-103">Core .NET libraries breaking changes in .NET Core 1.0-3.0</span></span>

<span data-ttu-id="9ab31-104">Основные библиотеки .NET предоставляет примитивы и другие общие типы, используемые в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ab31-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="9ab31-105">На этой странице описаны следующие критические изменения:</span><span class="sxs-lookup"><span data-stu-id="9ab31-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="9ab31-106">Критическое изменение</span><span class="sxs-lookup"><span data-stu-id="9ab31-106">Breaking change</span></span> | <span data-ttu-id="9ab31-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="9ab31-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="9ab31-108">Передача GroupCollection в методы расширения, принимающие IEnumerable\<T>, требует устранения неоднозначности</span><span class="sxs-lookup"><span data-stu-id="9ab31-108">Passing GroupCollection to extension methods taking IEnumerable\<T> requires disambiguation</span></span>](#passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation) | <span data-ttu-id="9ab31-109">3.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-109">3.0</span></span> |
| [<span data-ttu-id="9ab31-110">Интерфейсы API, сообщающие версию, теперь сообщают версию продукта, а не файла</span><span class="sxs-lookup"><span data-stu-id="9ab31-110">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="9ab31-111">3.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-111">3.0</span></span> |
| [<span data-ttu-id="9ab31-112">Пользовательские экземпляры EncoderFallbackBuffer не поддерживают рекурсивный откат</span><span class="sxs-lookup"><span data-stu-id="9ab31-112">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="9ab31-113">3.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-113">3.0</span></span> |
| [<span data-ttu-id="9ab31-114">Изменено поведение форматирования и анализа при наличии плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="9ab31-114">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="9ab31-115">3.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-115">3.0</span></span> |
| [<span data-ttu-id="9ab31-116">Операции синтаксического анализа с плавающей запятой больше не завершаются ошибкой и не вызывают исключение OverflowException</span><span class="sxs-lookup"><span data-stu-id="9ab31-116">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="9ab31-117">3.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-117">3.0</span></span> |
| [<span data-ttu-id="9ab31-118">Исключение InvalidAsynchronousStateException перенесено в другую сборку</span><span class="sxs-lookup"><span data-stu-id="9ab31-118">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="9ab31-119">3.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-119">3.0</span></span> |
| [<span data-ttu-id="9ab31-120">Замена неправильно сформированных последовательностей байтов в кодировке UTF-8 в соответствии с правилами Юникода</span><span class="sxs-lookup"><span data-stu-id="9ab31-120">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="9ab31-121">3.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-121">3.0</span></span> |
| [<span data-ttu-id="9ab31-122">Класс TypeDescriptionProviderAttribute перенесен в другую сборку</span><span class="sxs-lookup"><span data-stu-id="9ab31-122">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="9ab31-123">3.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-123">3.0</span></span> |
| [<span data-ttu-id="9ab31-124">ZipArchiveEntry больше не обрабатывает архивы с несогласованными размерами записей</span><span class="sxs-lookup"><span data-stu-id="9ab31-124">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="9ab31-125">3.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-125">3.0</span></span> |
| [<span data-ttu-id="9ab31-126">FieldInfo.SetValue вызывает исключение для статических полей и полей только для инициализации</span><span class="sxs-lookup"><span data-stu-id="9ab31-126">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="9ab31-127">3.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-127">3.0</span></span> |
| [<span data-ttu-id="9ab31-128">Во встроенные типы структур добавлены частные поля</span><span class="sxs-lookup"><span data-stu-id="9ab31-128">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="9ab31-129">2.1</span><span class="sxs-lookup"><span data-stu-id="9ab31-129">2.1</span></span> |
| [<span data-ttu-id="9ab31-130">Изменено значение по умолчанию для UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="9ab31-130">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="9ab31-131">2.1</span><span class="sxs-lookup"><span data-stu-id="9ab31-131">2.1</span></span> |
| [<span data-ttu-id="9ab31-132">Версии OpenSSL в macOS</span><span class="sxs-lookup"><span data-stu-id="9ab31-132">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="9ab31-133">2.1</span><span class="sxs-lookup"><span data-stu-id="9ab31-133">2.1</span></span> |
| [<span data-ttu-id="9ab31-134">Исключение UnauthorizedAccessException, вызванное FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="9ab31-134">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="9ab31-135">1.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-135">1.0</span></span> |
| [<span data-ttu-id="9ab31-136">Обработка исключений с поврежденным состоянием процесса не поддерживается</span><span class="sxs-lookup"><span data-stu-id="9ab31-136">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="9ab31-137">1.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-137">1.0</span></span> |
| [<span data-ttu-id="9ab31-138">Для свойств UriBuilder больше не добавляются начальные символы</span><span class="sxs-lookup"><span data-stu-id="9ab31-138">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="9ab31-139">1.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-139">1.0</span></span> |
| [<span data-ttu-id="9ab31-140">Process.StartInfo выдает исключение InvalidOperationException для процессов, которые не были запущены</span><span class="sxs-lookup"><span data-stu-id="9ab31-140">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="9ab31-141">1.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-141">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="9ab31-142">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-142">.NET Core 3.0</span></span>

[!INCLUDE [disambiguate-generic-type-for-groupcollection](../../../includes/core-changes/corefx/3.0/disambiguate-generic-type-for-groupcollection.md)]

***

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

<span data-ttu-id="9ab31-143">\*\*_</span><span class="sxs-lookup"><span data-stu-id="9ab31-143">\*\*_</span></span>

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

_*_

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

_*_

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

_*_

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

_*_

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

_*_

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

_*_

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

_*_

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

_*_

## <a name="net-core-21"></a><span data-ttu-id="9ab31-144">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9ab31-144">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a><span data-ttu-id="9ab31-145">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9ab31-145">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

<span data-ttu-id="9ab31-146">_\*\*</span><span class="sxs-lookup"><span data-stu-id="9ab31-146">_\*\*</span></span>
