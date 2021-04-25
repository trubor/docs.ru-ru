---
title: Критические изменения в библиотеке .NET
description: Список критических изменений в основных библиотеках .NET для .NET Core версий 1.0–3.0.
ms.date: 07/27/2020
ms.openlocfilehash: 99c72b5ff36d0c0cb821d50b1ec04fdef56189da
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494367"
---
# <a name="core-net-libraries-breaking-changes-in-net-core-10-30"></a><span data-ttu-id="173c9-103">Критические изменения в основных библиотеках .NET Core версий 1.0–3.0.</span><span class="sxs-lookup"><span data-stu-id="173c9-103">Core .NET libraries breaking changes in .NET Core 1.0-3.0</span></span>

<span data-ttu-id="173c9-104">Основные библиотеки .NET предоставляет примитивы и другие общие типы, используемые в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="173c9-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="173c9-105">На этой странице описаны следующие критические изменения:</span><span class="sxs-lookup"><span data-stu-id="173c9-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="173c9-106">Критическое изменение</span><span class="sxs-lookup"><span data-stu-id="173c9-106">Breaking change</span></span> | <span data-ttu-id="173c9-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="173c9-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="173c9-108">Передача GroupCollection в методы расширения, принимающие IEnumerable\<T>, требует устранения неоднозначности</span><span class="sxs-lookup"><span data-stu-id="173c9-108">Passing GroupCollection to extension methods taking IEnumerable\<T> requires disambiguation</span></span>](#passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation) | <span data-ttu-id="173c9-109">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="173c9-109">.NET Core 3.0</span></span> |
| [<span data-ttu-id="173c9-110">Интерфейсы API, сообщающие версию, теперь сообщают версию продукта, а не файла</span><span class="sxs-lookup"><span data-stu-id="173c9-110">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="173c9-111">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="173c9-111">.NET Core 3.0</span></span> |
| [<span data-ttu-id="173c9-112">Пользовательские экземпляры EncoderFallbackBuffer не поддерживают рекурсивный откат</span><span class="sxs-lookup"><span data-stu-id="173c9-112">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="173c9-113">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="173c9-113">.NET Core 3.0</span></span> |
| [<span data-ttu-id="173c9-114">Изменено поведение форматирования и анализа при наличии плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="173c9-114">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="173c9-115">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="173c9-115">.NET Core 3.0</span></span> |
| [<span data-ttu-id="173c9-116">Операции синтаксического анализа с плавающей запятой больше не завершаются ошибкой и не вызывают исключение OverflowException</span><span class="sxs-lookup"><span data-stu-id="173c9-116">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="173c9-117">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="173c9-117">.NET Core 3.0</span></span> |
| [<span data-ttu-id="173c9-118">Исключение InvalidAsynchronousStateException перенесено в другую сборку</span><span class="sxs-lookup"><span data-stu-id="173c9-118">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="173c9-119">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="173c9-119">.NET Core 3.0</span></span> |
| [<span data-ttu-id="173c9-120">Замена неправильно сформированных последовательностей байтов в кодировке UTF-8 в соответствии с правилами Юникода</span><span class="sxs-lookup"><span data-stu-id="173c9-120">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="173c9-121">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="173c9-121">.NET Core 3.0</span></span> |
| [<span data-ttu-id="173c9-122">Класс TypeDescriptionProviderAttribute перенесен в другую сборку</span><span class="sxs-lookup"><span data-stu-id="173c9-122">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="173c9-123">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="173c9-123">.NET Core 3.0</span></span> |
| [<span data-ttu-id="173c9-124">ZipArchiveEntry больше не обрабатывает архивы с несогласованными размерами записей</span><span class="sxs-lookup"><span data-stu-id="173c9-124">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="173c9-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="173c9-125">.NET Core 3.0</span></span> |
| [<span data-ttu-id="173c9-126">FieldInfo.SetValue вызывает исключение для статических полей и полей только для инициализации</span><span class="sxs-lookup"><span data-stu-id="173c9-126">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="173c9-127">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="173c9-127">.NET Core 3.0</span></span> |
| [<span data-ttu-id="173c9-128">API-интерфейсы пути не выдают исключение для недопустимых символов</span><span class="sxs-lookup"><span data-stu-id="173c9-128">Path APIs don't throw an exception for invalid characters</span></span>](#path-apis-dont-throw-an-exception-for-invalid-characters) | <span data-ttu-id="173c9-129">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="173c9-129">.NET Core 2.1</span></span> |
| [<span data-ttu-id="173c9-130">Во встроенные типы структур добавлены частные поля</span><span class="sxs-lookup"><span data-stu-id="173c9-130">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="173c9-131">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="173c9-131">.NET Core 2.1</span></span> |
| [<span data-ttu-id="173c9-132">Изменено значение по умолчанию для UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="173c9-132">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="173c9-133">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="173c9-133">.NET Core 2.1</span></span> |
| [<span data-ttu-id="173c9-134">Версии OpenSSL в macOS</span><span class="sxs-lookup"><span data-stu-id="173c9-134">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="173c9-135">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="173c9-135">.NET Core 2.1</span></span> |
| [<span data-ttu-id="173c9-136">Исключение UnauthorizedAccessException, вызванное FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="173c9-136">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="173c9-137">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="173c9-137">.NET Core 1.0</span></span> |
| [<span data-ttu-id="173c9-138">Обработка исключений с поврежденным состоянием процесса не поддерживается</span><span class="sxs-lookup"><span data-stu-id="173c9-138">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="173c9-139">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="173c9-139">.NET Core 1.0</span></span> |
| [<span data-ttu-id="173c9-140">Для свойств UriBuilder больше не добавляются начальные символы</span><span class="sxs-lookup"><span data-stu-id="173c9-140">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="173c9-141">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="173c9-141">.NET Core 1.0</span></span> |
| [<span data-ttu-id="173c9-142">Process.StartInfo выдает исключение InvalidOperationException для процессов, которые не были запущены</span><span class="sxs-lookup"><span data-stu-id="173c9-142">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="173c9-143">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="173c9-143">.NET Core 1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="173c9-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="173c9-144">.NET Core 3.0</span></span>

[!INCLUDE [disambiguate-generic-type-for-groupcollection](../../../includes/core-changes/corefx/3.0/disambiguate-generic-type-for-groupcollection.md)]

***

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="173c9-145">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="173c9-145">.NET Core 2.1</span></span>

[!INCLUDE [path-apis-dont-throw-exception-for-invalid-paths](../../../includes/core-changes/corefx/2.1/path-apis-dont-throw-exception-for-invalid-paths.md)]

***

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="173c9-146">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="173c9-146">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
