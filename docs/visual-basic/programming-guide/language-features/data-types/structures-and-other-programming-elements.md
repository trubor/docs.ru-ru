---
description: Дополнительные сведения о структурах и других элементах программирования (Visual Basic)
title: Структуры и другие элементы программирования
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 62052389b617849566a3cd0c475a2eb5da9e61ca
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430590"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="c0b52-103">Структуры и другие элементы программирования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0b52-103">Structures and Other Programming Elements (Visual Basic)</span></span>

<span data-ttu-id="c0b52-104">Структуры можно использовать совместно с массивами, объектами и процедурами, а также друг с другом.</span><span class="sxs-lookup"><span data-stu-id="c0b52-104">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="c0b52-105">При взаимодействии используется тот же синтаксис, что и при использовании этих элементов по отдельности.</span><span class="sxs-lookup"><span data-stu-id="c0b52-105">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0b52-106">Нельзя инициализировать какие либо элементы структуры в объявлении структуры.</span><span class="sxs-lookup"><span data-stu-id="c0b52-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="c0b52-107">Значения можно назначать только элементам переменной, объявленным как тип структуры.</span><span class="sxs-lookup"><span data-stu-id="c0b52-107">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="c0b52-108">Структуры и массивы</span><span class="sxs-lookup"><span data-stu-id="c0b52-108">Structures and Arrays</span></span>  

 <span data-ttu-id="c0b52-109">Структура может содержать массив в качестве одного или нескольких элементов.</span><span class="sxs-lookup"><span data-stu-id="c0b52-109">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="c0b52-110">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c0b52-110">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 <span data-ttu-id="c0b52-111">Доступ к значениям массива в структуре осуществляется так же, как и к свойству объекта.</span><span class="sxs-lookup"><span data-stu-id="c0b52-111">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="c0b52-112">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c0b52-112">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="c0b52-113">Можно также объявить массив структур.</span><span class="sxs-lookup"><span data-stu-id="c0b52-113">You can also declare an array of structures.</span></span> <span data-ttu-id="c0b52-114">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c0b52-114">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="c0b52-115">Для доступа к компонентам этой архитектуры данных следуйте тем же правилам.</span><span class="sxs-lookup"><span data-stu-id="c0b52-115">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="c0b52-116">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c0b52-116">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="c0b52-117">Структуры и объекты</span><span class="sxs-lookup"><span data-stu-id="c0b52-117">Structures and Objects</span></span>  

 <span data-ttu-id="c0b52-118">Структура может содержать объект в качестве одного или нескольких его элементов.</span><span class="sxs-lookup"><span data-stu-id="c0b52-118">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="c0b52-119">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c0b52-119">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="c0b52-120">В таком объявлении следует использовать конкретный класс объекта, а не `Object` .</span><span class="sxs-lookup"><span data-stu-id="c0b52-120">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="c0b52-121">Структуры и процедуры</span><span class="sxs-lookup"><span data-stu-id="c0b52-121">Structures and Procedures</span></span>  

 <span data-ttu-id="c0b52-122">Структуру можно передать в качестве аргумента процедуры.</span><span class="sxs-lookup"><span data-stu-id="c0b52-122">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="c0b52-123">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c0b52-123">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="c0b52-124">В предыдущем примере структура передается *по ссылке*, что позволяет процедуре изменять ее элементы, чтобы изменения вступили в силу в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="c0b52-124">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="c0b52-125">Если необходимо защитить структуру от таких изменений, передайте ее по значению.</span><span class="sxs-lookup"><span data-stu-id="c0b52-125">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="c0b52-126">Можно также вернуть структуру из `Function` процедуры.</span><span class="sxs-lookup"><span data-stu-id="c0b52-126">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="c0b52-127">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c0b52-127">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a><span data-ttu-id="c0b52-128">Структуры внутри структур</span><span class="sxs-lookup"><span data-stu-id="c0b52-128">Structures Within Structures</span></span>  

 <span data-ttu-id="c0b52-129">Структуры могут содержать другие структуры.</span><span class="sxs-lookup"><span data-stu-id="c0b52-129">Structures can contain other structures.</span></span> <span data-ttu-id="c0b52-130">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c0b52-130">The following example illustrates this.</span></span>  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 <span data-ttu-id="c0b52-131">Эту методику также можно использовать для инкапсуляции структуры, определенной в одном модуле, в структуре, определенной в другом модуле.</span><span class="sxs-lookup"><span data-stu-id="c0b52-131">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="c0b52-132">Структуры могут содержать другие структуры для произвольной глубины.</span><span class="sxs-lookup"><span data-stu-id="c0b52-132">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b52-133">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c0b52-133">See also</span></span>

- [<span data-ttu-id="c0b52-134">Типы данных</span><span class="sxs-lookup"><span data-stu-id="c0b52-134">Data Types</span></span>](index.md)
- [<span data-ttu-id="c0b52-135">Простые типы данных</span><span class="sxs-lookup"><span data-stu-id="c0b52-135">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="c0b52-136">Составные типы данных</span><span class="sxs-lookup"><span data-stu-id="c0b52-136">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="c0b52-137">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="c0b52-137">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="c0b52-138">Структуры</span><span class="sxs-lookup"><span data-stu-id="c0b52-138">Structures</span></span>](structures.md)
- [<span data-ttu-id="c0b52-139">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="c0b52-139">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="c0b52-140">Практическое руководство. Объявление структуры</span><span class="sxs-lookup"><span data-stu-id="c0b52-140">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="c0b52-141">Переменные структуры</span><span class="sxs-lookup"><span data-stu-id="c0b52-141">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="c0b52-142">Структуры и классы</span><span class="sxs-lookup"><span data-stu-id="c0b52-142">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="c0b52-143">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="c0b52-143">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
