---
description: 'Дополнительные сведения: преобразования типов в Visual Basic'
title: Преобразования типов
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
ms.openlocfilehash: 1f40951856710eb6f2892a7f7a4e04173ee3ee44
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454486"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="d0e9a-103">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0e9a-103">Type Conversions in Visual Basic</span></span>

<span data-ttu-id="d0e9a-104">Процесс изменения значения из одного типа данных на другой тип называется *преобразованием*.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-104">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="d0e9a-105">Преобразования могут *расширяться* или *уменьшаться* в зависимости от объема данных используемых типов.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-105">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="d0e9a-106">Они также являются *неявно* или явными в зависимости от синтаксиса в исходном коде.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-106">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0e9a-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="d0e9a-107">In This Section</span></span>  

 [<span data-ttu-id="d0e9a-108">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="d0e9a-108">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)  
 <span data-ttu-id="d0e9a-109">Описывает преобразования, классифицированные, если целевой тип может содержать данные.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-109">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="d0e9a-110">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="d0e9a-110">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)  
 <span data-ttu-id="d0e9a-111">Описывает преобразования, которые классифицируются, независимо от того, выполняет ли Visual Basic их автоматически.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-111">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="d0e9a-112">Преобразования значений между строковыми и другими типами</span><span class="sxs-lookup"><span data-stu-id="d0e9a-112">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="d0e9a-113">Описывает преобразование между строками и числовыми `Boolean` значениями, значениями даты и времени.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-113">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="d0e9a-114">Практическое руководство. Преобразование объекта к другому типу в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0e9a-114">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="d0e9a-115">Показывает, как преобразовать `Object` переменную в любой другой тип данных.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-115">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="d0e9a-116">Преобразования массивов</span><span class="sxs-lookup"><span data-stu-id="d0e9a-116">Array Conversions</span></span>](array-conversions.md)  
 <span data-ttu-id="d0e9a-117">Пошаговый процесс преобразования между массивами различных типов данных.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-117">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d0e9a-118">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="d0e9a-118">Related Sections</span></span>  

 [<span data-ttu-id="d0e9a-119">Типы данных</span><span class="sxs-lookup"><span data-stu-id="d0e9a-119">Data Types</span></span>](index.md)  
 <span data-ttu-id="d0e9a-120">Вводит Visual Basic типы данных и описывает, как их использовать.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-120">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="d0e9a-121">Типы данных</span><span class="sxs-lookup"><span data-stu-id="d0e9a-121">Data Types</span></span>](../../../language-reference/data-types/index.md)  
 <span data-ttu-id="d0e9a-122">Содержит список простейших типов данных, предоставляемых Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-122">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="d0e9a-123">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="d0e9a-123">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)  
 <span data-ttu-id="d0e9a-124">Обсуждаются некоторые распространенные проблемы, которые могут возникнуть при работе с типами данных.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-124">Discusses some common problems that can arise when working with data types.</span></span>
