---
description: 'Дополнительные сведения о: BC36593: выражение типа <type> не может быть доступно для запросов'
title: Выражение типа <type> не доступно для запроса
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: b2fc6c81ee34c1f8e251ac65ba582fde1c6a7b9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796357"
---
# <a name="bc36593-expression-of-type-type-is-not-queryable"></a><span data-ttu-id="fa8b6-103">BC36593: выражение типа \<type> не может быть доступно для запросов</span><span class="sxs-lookup"><span data-stu-id="fa8b6-103">BC36593: Expression of type \<type> is not queryable</span></span>

<span data-ttu-id="fa8b6-104">Выражение типа \<type> не может быть доступно для запросов.</span><span class="sxs-lookup"><span data-stu-id="fa8b6-104">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="fa8b6-105">Убедитесь, что отсутствует ссылка на сборку и (или) импорт пространства имен для поставщика LINQ.</span><span class="sxs-lookup"><span data-stu-id="fa8b6-105">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>

 <span data-ttu-id="fa8b6-106">Запрашиваемые типы определяются в <xref:System.Linq> <xref:System.Data.Linq> <xref:System.Xml.Linq> пространствах имен, и.</span><span class="sxs-lookup"><span data-stu-id="fa8b6-106">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="fa8b6-107">Для выполнения запросов LINQ необходимо импортировать одно или несколько из этих пространств имен.</span><span class="sxs-lookup"><span data-stu-id="fa8b6-107">You must import one or more of these namespaces to perform LINQ queries.</span></span>

 <span data-ttu-id="fa8b6-108"><xref:System.Linq>Пространство имен позволяет запрашивать объекты, такие как коллекции и массивы, с помощью LINQ.</span><span class="sxs-lookup"><span data-stu-id="fa8b6-108">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>

 <span data-ttu-id="fa8b6-109">Это <xref:System.Data.Linq> пространство имен позволяет запрашивать наборы данных ADO.NET и SQL Server с помощью LINQ.</span><span class="sxs-lookup"><span data-stu-id="fa8b6-109">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>

 <span data-ttu-id="fa8b6-110"><xref:System.Xml.Linq>Пространство имен позволяет запрашивать XML-код с помощью LINQ и использовать функции XML в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fa8b6-110">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>

 <span data-ttu-id="fa8b6-111">**Идентификатор ошибки:** BC36593</span><span class="sxs-lookup"><span data-stu-id="fa8b6-111">**Error ID:** BC36593</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fa8b6-112">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="fa8b6-112">To correct this error</span></span>

1. <span data-ttu-id="fa8b6-113">Добавьте `Import` оператор для <xref:System.Linq> <xref:System.Data.Linq> <xref:System.Xml.Linq> пространства имен, или в файл кода.</span><span class="sxs-lookup"><span data-stu-id="fa8b6-113">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="fa8b6-114">Также можно импортировать пространства имен для проекта с помощью страницы **ссылки** в конструкторе проектов (**Мой проект**).</span><span class="sxs-lookup"><span data-stu-id="fa8b6-114">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>

2. <span data-ttu-id="fa8b6-115">Убедитесь, что тип, определенный в качестве источника запроса, является запрашиваемым типом.</span><span class="sxs-lookup"><span data-stu-id="fa8b6-115">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="fa8b6-116">То есть тип, реализующий <xref:System.Collections.Generic.IEnumerable%601> или <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="fa8b6-116">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa8b6-117">См. также</span><span class="sxs-lookup"><span data-stu-id="fa8b6-117">See also</span></span>

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- <span data-ttu-id="fa8b6-118">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa8b6-118">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="fa8b6-119">LINQ</span><span class="sxs-lookup"><span data-stu-id="fa8b6-119">LINQ</span></span>](../../programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="fa8b6-120">XML</span><span class="sxs-lookup"><span data-stu-id="fa8b6-120">XML</span></span>](../../programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="fa8b6-121">Ссылки и оператор Imports</span><span class="sxs-lookup"><span data-stu-id="fa8b6-121">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="fa8b6-122">Оператор Imports (пространство имен .NET и тип)</span><span class="sxs-lookup"><span data-stu-id="fa8b6-122">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="fa8b6-123">Страница "Ссылки" в конструкторе проектов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa8b6-123">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
