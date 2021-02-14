---
description: 'Дополнительные сведения: Устранение неполадок массивов (Visual Basic)'
title: Устранение неполадок, связанных с массивами
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 2aca3c1819ed6482e132ba432e5e70fbdf9a5b3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454499"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="a914c-103">Устранение неполадок, связанных с массивами (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a914c-103">Troubleshooting Arrays (Visual Basic)</span></span>

<span data-ttu-id="a914c-104">На этой странице перечислены некоторые распространенные проблемы, которые могут возникнуть при работе с массивами.</span><span class="sxs-lookup"><span data-stu-id="a914c-104">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="a914c-105">Ошибки компиляции при объявлении и инициализации массива</span><span class="sxs-lookup"><span data-stu-id="a914c-105">Compilation Errors Declaring and Initializing an Array</span></span>  

 <span data-ttu-id="a914c-106">Ошибки компиляции могут возникать из нечеткого понимания правил объявления, создания и инициализации массивов.</span><span class="sxs-lookup"><span data-stu-id="a914c-106">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="a914c-107">Ниже перечислены наиболее распространенные причины возникновения ошибок.</span><span class="sxs-lookup"><span data-stu-id="a914c-107">The most common causes of errors are the following:</span></span>  
  
- <span data-ttu-id="a914c-108">Перед указанием длины измерения в объявлении переменной массива следует указать [новое предложение оператора](../../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="a914c-108">Supplying a [New Operator](../../../language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="a914c-109">В следующих строках кода показаны недопустимые объявления этого типа.</span><span class="sxs-lookup"><span data-stu-id="a914c-109">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- <span data-ttu-id="a914c-110">Задание длины измерений для большего массива массивов массивов.</span><span class="sxs-lookup"><span data-stu-id="a914c-110">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="a914c-111">В следующей строке кода показано недопустимое объявление этого типа.</span><span class="sxs-lookup"><span data-stu-id="a914c-111">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- <span data-ttu-id="a914c-112">Пропуск `New` ключевого слова при указании значений элементов.</span><span class="sxs-lookup"><span data-stu-id="a914c-112">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="a914c-113">В следующей строке кода показано недопустимое объявление этого типа.</span><span class="sxs-lookup"><span data-stu-id="a914c-113">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- <span data-ttu-id="a914c-114">Указание `New` предложения без фигурных скобок ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="a914c-114">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="a914c-115">В следующих строках кода показаны недопустимые объявления этого типа.</span><span class="sxs-lookup"><span data-stu-id="a914c-115">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="a914c-116">Доступ к массиву вне границ</span><span class="sxs-lookup"><span data-stu-id="a914c-116">Accessing an Array Out of Bounds</span></span>  

 <span data-ttu-id="a914c-117">Процесс инициализации массива назначает верхнюю границу и нижнюю границу для каждого измерения.</span><span class="sxs-lookup"><span data-stu-id="a914c-117">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="a914c-118">Каждый доступ к элементу массива должен указывать допустимый индекс (или подстрочный) для каждого измерения.</span><span class="sxs-lookup"><span data-stu-id="a914c-118">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="a914c-119">Если какой-либо индекс находится ниже нижней границы или выше его верхней границы, возникает <xref:System.IndexOutOfRangeException> исключение.</span><span class="sxs-lookup"><span data-stu-id="a914c-119">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="a914c-120">Компилятор не может обнаружить такую ошибку, поэтому во время выполнения возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="a914c-120">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="a914c-121">Определение границ</span><span class="sxs-lookup"><span data-stu-id="a914c-121">Determining Bounds</span></span>  

 <span data-ttu-id="a914c-122">Если другой компонент передает массив в код, например в качестве аргумента процедуры, размер этого массива или длины его измерений неизвестн.</span><span class="sxs-lookup"><span data-stu-id="a914c-122">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="a914c-123">Прежде чем пытаться получить доступ к любому элементу, необходимо всегда определять верхнюю границу для каждого измерения массива.</span><span class="sxs-lookup"><span data-stu-id="a914c-123">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="a914c-124">Если массив был создан некоторыми средствами, отличными от `New` предложения Visual Basic, то нижняя граница может быть отличной от 0, а также наиболее надежно определить нижнюю границу.</span><span class="sxs-lookup"><span data-stu-id="a914c-124">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="a914c-125">Указание измерения</span><span class="sxs-lookup"><span data-stu-id="a914c-125">Specifying the Dimension</span></span>  

 <span data-ttu-id="a914c-126">При определении границ многомерного массива следует соблюдать осторожность при указании измерения.</span><span class="sxs-lookup"><span data-stu-id="a914c-126">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="a914c-127">`dimension`Параметры <xref:System.Array.GetLowerBound%2A> методов и основаны <xref:System.Array.GetUpperBound%2A> на 0, а `Rank` Параметры Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> и <xref:Microsoft.VisualBasic.Information.UBound%2A> функций основаны на 1.</span><span class="sxs-lookup"><span data-stu-id="a914c-127">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a914c-128">См. также</span><span class="sxs-lookup"><span data-stu-id="a914c-128">See also</span></span>

- [<span data-ttu-id="a914c-129">Массивы</span><span class="sxs-lookup"><span data-stu-id="a914c-129">Arrays</span></span>](index.md)
- <span data-ttu-id="a914c-130">[How to: Initialize an Array Variable in Visual Basic](how-to-initialize-an-array-variable.md) (Практическое руководство. Инициализация переменной массива в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a914c-130">[How to: Initialize an Array Variable in Visual Basic](how-to-initialize-an-array-variable.md)</span></span>
