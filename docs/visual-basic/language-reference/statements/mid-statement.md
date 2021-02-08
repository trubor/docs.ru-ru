---
description: 'Дополнительные сведения о инструкции: mid'
title: Оператор Mid
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: 29cf933cb38fc6ef831570d0940b481abf9cfecf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768887"
---
# <a name="mid-statement"></a><span data-ttu-id="effb9-103">Оператор Mid</span><span class="sxs-lookup"><span data-stu-id="effb9-103">Mid Statement</span></span>

<span data-ttu-id="effb9-104">Заменяет указанное число символов в `String` переменной символами из другой строки.</span><span class="sxs-lookup"><span data-stu-id="effb9-104">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="effb9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="effb9-105">Syntax</span></span>  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="effb9-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="effb9-106">Parts</span></span>  

 `Target`  
 <span data-ttu-id="effb9-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="effb9-107">Required.</span></span> <span data-ttu-id="effb9-108">Имя переменной, `String` которую необходимо изменить.</span><span class="sxs-lookup"><span data-stu-id="effb9-108">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="effb9-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="effb9-109">Required.</span></span> <span data-ttu-id="effb9-110">Выражение `Integer`.</span><span class="sxs-lookup"><span data-stu-id="effb9-110">`Integer` expression.</span></span> <span data-ttu-id="effb9-111">Место в символах `Target` , с которого начинается замена текста.</span><span class="sxs-lookup"><span data-stu-id="effb9-111">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="effb9-112">`Start` использует индекс, отсчитываемый от единицы.</span><span class="sxs-lookup"><span data-stu-id="effb9-112">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="effb9-113">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="effb9-113">Optional.</span></span> <span data-ttu-id="effb9-114">Выражение `Integer`.</span><span class="sxs-lookup"><span data-stu-id="effb9-114">`Integer` expression.</span></span> <span data-ttu-id="effb9-115">Число символов для замены.</span><span class="sxs-lookup"><span data-stu-id="effb9-115">Number of characters to replace.</span></span> <span data-ttu-id="effb9-116">Если этот параметр опущен, `String` используются все.</span><span class="sxs-lookup"><span data-stu-id="effb9-116">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="effb9-117">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="effb9-117">Required.</span></span> <span data-ttu-id="effb9-118">`String` выражение, которое заменяет часть `Target` .</span><span class="sxs-lookup"><span data-stu-id="effb9-118">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="effb9-119">Исключения</span><span class="sxs-lookup"><span data-stu-id="effb9-119">Exceptions</span></span>  
  
|<span data-ttu-id="effb9-120">Тип исключения</span><span class="sxs-lookup"><span data-stu-id="effb9-120">Exception type</span></span>|<span data-ttu-id="effb9-121">Условие</span><span class="sxs-lookup"><span data-stu-id="effb9-121">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="effb9-122">`Start` <= 0 или `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="effb9-122">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="effb9-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="effb9-123">Remarks</span></span>  

 <span data-ttu-id="effb9-124">Число заменяемых символов всегда меньше или равно числу символов в `Target` .</span><span class="sxs-lookup"><span data-stu-id="effb9-124">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="effb9-125">Visual Basic содержит <xref:Microsoft.VisualBasic.Strings.Mid%2A> функцию и `Mid` оператор.</span><span class="sxs-lookup"><span data-stu-id="effb9-125">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="effb9-126">Эти элементы работают с указанным числом символов в строке, но `Mid` функция возвращает символы, пока `Mid` оператор заменяет символы.</span><span class="sxs-lookup"><span data-stu-id="effb9-126">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="effb9-127">Для получения дополнительной информации см. <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="effb9-127">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="effb9-128">`MidB`Инструкция более ранних версий Visual Basic заменяет подстроку в байтах, а не на символы.</span><span class="sxs-lookup"><span data-stu-id="effb9-128">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="effb9-129">Он используется в основном для преобразования строк в приложениях с двухбайтовой кодировкой (DBCS).</span><span class="sxs-lookup"><span data-stu-id="effb9-129">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="effb9-130">Все строки Visual Basic в Юникоде и больше не `MidB` поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="effb9-130">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="effb9-131">Пример</span><span class="sxs-lookup"><span data-stu-id="effb9-131">Example</span></span>  

 <span data-ttu-id="effb9-132">В этом примере используется `Mid` оператор для замены указанного числа символов в строковой переменной символами из другой строки.</span><span class="sxs-lookup"><span data-stu-id="effb9-132">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="effb9-133">Требования</span><span class="sxs-lookup"><span data-stu-id="effb9-133">Requirements</span></span>  

 <span data-ttu-id="effb9-134">**Пространство имен:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="effb9-134">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="effb9-135">**Модуль:**`Strings`</span><span class="sxs-lookup"><span data-stu-id="effb9-135">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="effb9-136">**Сборка:** Библиотека времени выполнения Visual Basic (в Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="effb9-136">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="effb9-137">См. также</span><span class="sxs-lookup"><span data-stu-id="effb9-137">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="effb9-138">Строки</span><span class="sxs-lookup"><span data-stu-id="effb9-138">Strings</span></span>](../../programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="effb9-139">Знакомство со строками в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="effb9-139">Introduction to Strings in Visual Basic</span></span>](../../programming-guide/language-features/strings/introduction-to-strings.md)
