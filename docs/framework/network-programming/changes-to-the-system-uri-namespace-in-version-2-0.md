---
description: 'Узнайте подробнее о: Изменения пространства имен System.Uri в версии 2.0'
title: Изменения пространства имен System.Uri в версии 2.0
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
ms.openlocfilehash: 8b5e2f2b3b59fba96e20e40a4df18273a2f6034f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791625"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="03f30-103">Изменения пространства имен System.Uri в версии 2.0</span><span class="sxs-lookup"><span data-stu-id="03f30-103">Changes to the System.Uri namespace in version 2.0</span></span>

<span data-ttu-id="03f30-104">В класс <xref:System.Uri?displayProperty=nameWithType> были внесены некоторые изменения.</span><span class="sxs-lookup"><span data-stu-id="03f30-104">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="03f30-105">Эти изменения были направлены на исправление некорректного поведения, повышение удобства использования и улучшение безопасности.</span><span class="sxs-lookup"><span data-stu-id="03f30-105">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>

## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="03f30-106">Устаревшие и нерекомендуемые члены</span><span class="sxs-lookup"><span data-stu-id="03f30-106">Obsolete and deprecated Members</span></span>

 <span data-ttu-id="03f30-107">Конструкторы:</span><span class="sxs-lookup"><span data-stu-id="03f30-107">Constructors:</span></span>

- <span data-ttu-id="03f30-108">все конструкторы с параметром `dontEscape`.</span><span class="sxs-lookup"><span data-stu-id="03f30-108">All constructors that have a `dontEscape` parameter.</span></span>

 <span data-ttu-id="03f30-109">Методы:</span><span class="sxs-lookup"><span data-stu-id="03f30-109">Methods:</span></span>

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a><span data-ttu-id="03f30-110">Изменения</span><span class="sxs-lookup"><span data-stu-id="03f30-110">Changes</span></span>

- <span data-ttu-id="03f30-111">Для схем URI, которые заведомо не содержат части запроса (file, ftp и другие), символ "?" всегда экранируется и не обрабатывается как начало части <xref:System.Uri.Query%2A>.</span><span class="sxs-lookup"><span data-stu-id="03f30-111">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>

- <span data-ttu-id="03f30-112">Для неявных файловых URI (имеют форму `c:\directory\file@name.txt`) символ фрагмента ("#") всегда экранируется, за исключением случаев, когда запрашивается полная отмена экранирования или <xref:System.Uri.LocalPath%2A> имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="03f30-112">For implicit file URIs (of the form `c:\directory\file@name.txt`), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>

- <span data-ttu-id="03f30-113">Прекращена поддержка имен узлов UNC. Принята спецификация IDN, определяющая представление международных имен узлов.</span><span class="sxs-lookup"><span data-stu-id="03f30-113">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>

- <span data-ttu-id="03f30-114"><xref:System.Uri.LocalPath%2A> всегда возвращает строку с полной отменой экранирования.</span><span class="sxs-lookup"><span data-stu-id="03f30-114"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>

- <span data-ttu-id="03f30-115"><xref:System.Uri.ToString%2A> не отменяет экранирование экранированного символа "%", "?" или "#".</span><span class="sxs-lookup"><span data-stu-id="03f30-115"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>

- <span data-ttu-id="03f30-116"><xref:System.Uri.Equals%2A> теперь включает часть <xref:System.Uri.Query%2A> в проверку равенства.</span><span class="sxs-lookup"><span data-stu-id="03f30-116"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>

- <span data-ttu-id="03f30-117">Операторы "==" и "!=" переопределены и связаны с методом <xref:System.Uri.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="03f30-117">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>

- <span data-ttu-id="03f30-118"><xref:System.Uri.IsLoopback%2A> теперь дает согласованные результаты.</span><span class="sxs-lookup"><span data-stu-id="03f30-118"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>

- <span data-ttu-id="03f30-119">URI "`file:///path`" больше не преобразуется в `file://path`.</span><span class="sxs-lookup"><span data-stu-id="03f30-119">The URI "`file:///path`" is no longer translated into `file://path`.</span></span>

- <span data-ttu-id="03f30-120">"#" теперь распознается как признак конца имени узла.</span><span class="sxs-lookup"><span data-stu-id="03f30-120">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="03f30-121">То есть `http://contoso.com#fragment` теперь преобразуется в `http://contoso.com/#fragment`.</span><span class="sxs-lookup"><span data-stu-id="03f30-121">That is, `http://contoso.com#fragment` is now converted to `http://contoso.com/#fragment`.</span></span>

- <span data-ttu-id="03f30-122">Исправлена ошибка, возникающая при объединении базового URI с фрагментом.</span><span class="sxs-lookup"><span data-stu-id="03f30-122">A bug when combining a base URI with a fragment has been fixed.</span></span>

- <span data-ttu-id="03f30-123">Исправлена ошибка в <xref:System.Uri.HostNameType%2A>.</span><span class="sxs-lookup"><span data-stu-id="03f30-123">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>

- <span data-ttu-id="03f30-124">Исправлена ошибка при синтаксическом анализе NNTP.</span><span class="sxs-lookup"><span data-stu-id="03f30-124">A bug in NNTP parsing is fixed.</span></span>

- <span data-ttu-id="03f30-125">URI формата HTTP:contoso.com теперь приводят к возникновению исключения синтаксического анализа.</span><span class="sxs-lookup"><span data-stu-id="03f30-125">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>

- <span data-ttu-id="03f30-126">Платформа правильно обрабатывает сведения о пользователях в URI.</span><span class="sxs-lookup"><span data-stu-id="03f30-126">The Framework correctly handles userinfo in a URI.</span></span>

- <span data-ttu-id="03f30-127">Сжатие пути URI фиксировано таким образом, чтобы неработающий URI не мог выполнять обход файловой системы на уровне выше корневого.</span><span class="sxs-lookup"><span data-stu-id="03f30-127">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>

## <a name="see-also"></a><span data-ttu-id="03f30-128">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="03f30-128">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
