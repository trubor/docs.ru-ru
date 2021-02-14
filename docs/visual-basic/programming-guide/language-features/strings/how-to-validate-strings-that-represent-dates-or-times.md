---
description: Дополнительные сведения см. в статье как проверить строки, представляющие дату или время (Visual Basic).
title: Практическое руководство. Проверка строк, представляющих дату или время
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 4e9255717d1711d8e9839c218a78b359549d9eef
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424259"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="2938d-103">Практическое руководство. Проверка строк, представляющих дату или время (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2938d-103">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>

<span data-ttu-id="2938d-104">В следующем примере кода задается `Boolean` значение, указывающее, представляет ли строка допустимую дату или время.</span><span class="sxs-lookup"><span data-stu-id="2938d-104">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2938d-105">Пример</span><span class="sxs-lookup"><span data-stu-id="2938d-105">Example</span></span>  

 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="2938d-106">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="2938d-106">Compile the code</span></span>  

 <span data-ttu-id="2938d-107">Замените `("01/01/03")` и `"9:30 PM"` датой и временем, которые необходимо проверить.</span><span class="sxs-lookup"><span data-stu-id="2938d-107">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="2938d-108">Строку можно заменить другой жестко запрограммированной строкой, `String` переменной или методом, возвращающим строку, например `InputBox` .</span><span class="sxs-lookup"><span data-stu-id="2938d-108">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2938d-109">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="2938d-109">Robust Programming</span></span>  

 <span data-ttu-id="2938d-110">Используйте этот метод для проверки строки перед попыткой преобразования в `String` `DateTime` переменную.</span><span class="sxs-lookup"><span data-stu-id="2938d-110">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="2938d-111">При проверке даты или времени сначала можно избежать создания исключения во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="2938d-111">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2938d-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2938d-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="2938d-113">Проверка строк в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2938d-113">Validating Strings in Visual Basic</span></span>](validating-strings.md)
