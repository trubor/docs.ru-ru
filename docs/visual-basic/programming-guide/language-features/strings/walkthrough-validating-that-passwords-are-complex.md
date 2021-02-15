---
description: Дополнительные сведения см. в разделе Пошаговое руководство. Проверка сложности паролей (Visual Basic)
title: Сложность проверки паролей
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 608d9c7708058ca99196f2a06fd4ddd018aa0363
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471015"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="9ca7b-103">Пошаговое руководство. Проверка паролей на сложность (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ca7b-103">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>

<span data-ttu-id="9ca7b-104">Этот метод проверяет некоторые характеристики строгого пароля и обновляет строковый параметр, используя сведения о том, какие проверки пароля завершился ошибкой.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-104">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="9ca7b-105">Пароли можно использовать в защищенной системе для авторизации пользователя.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-105">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="9ca7b-106">Тем не менее пароли должны быть сложными для взлома неавторизованными пользователями.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-106">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="9ca7b-107">Злоумышленники могут использовать *словарную* программу для атаки, которая перебирает все слова в словаре (или несколько словарей на разных языках) и проверяет, работает ли какое-либо из слов в качестве пароля пользователя.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-107">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="9ca7b-108">Ненадежные пароли, например "Янкиз" или "Мустанг", можно быстро угадать.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-108">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="9ca7b-109">Более надежные пароли, например "? Вы " L1N3vaFiNdMeyeP@sSWerd !", вероятно, догадаться гораздо меньше.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-109">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="9ca7b-110">Система, защищенная паролем, должна гарантировать, что пользователи будут выбирать надежные пароли.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-110">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="9ca7b-111">Надежный пароль является сложным (он содержит сочетание прописных и строчных букв, цифр и специальных символов) и не является словом.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-111">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="9ca7b-112">В этом примере показано, как проверить сложность.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-112">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ca7b-113">Пример</span><span class="sxs-lookup"><span data-stu-id="9ca7b-113">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="9ca7b-114">Код</span><span class="sxs-lookup"><span data-stu-id="9ca7b-114">Code</span></span>  

 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="9ca7b-115">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="9ca7b-115">Compile the code</span></span>  

 <span data-ttu-id="9ca7b-116">Вызовите этот метод, передав строку, содержащую этот пароль.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-116">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="9ca7b-117">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="9ca7b-117">This example requires:</span></span>  
  
- <span data-ttu-id="9ca7b-118">Доступ к членам пространства имен <xref:System.Text.RegularExpressions>.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-118">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="9ca7b-119">Добавьте оператор `Imports`, если в коде не используются полные имена членов.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-119">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="9ca7b-120">Дополнительные сведения см. в статье [Оператор Imports (пространство имен .NET и тип)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="9ca7b-120">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="9ca7b-121">Безопасность</span><span class="sxs-lookup"><span data-stu-id="9ca7b-121">Security</span></span>  

 <span data-ttu-id="9ca7b-122">При перемещении пароля по сети необходимо использовать безопасный метод передачи данных.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-122">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="9ca7b-123">Дополнительные сведения см. в разделе [ASP.NET Web Application Security](/previous-versions/aspnet/330a99hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9ca7b-123">For more information, see [ASP.NET Web Application Security](/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="9ca7b-124">Точность функции можно улучшить `ValidatePassword` , добавив дополнительные проверки сложности:</span><span class="sxs-lookup"><span data-stu-id="9ca7b-124">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
- <span data-ttu-id="9ca7b-125">Сравните пароль и его подстроки с именем пользователя, идентификатором пользователя и словарем, определяемым приложением.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-125">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="9ca7b-126">Кроме того, при выполнении сравнений следует рассматривать визуально схожие символы как эквивалентные.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-126">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="9ca7b-127">Например, буквы "l" и "e" считаются эквивалентными цифрам "1" и "3".</span><span class="sxs-lookup"><span data-stu-id="9ca7b-127">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
- <span data-ttu-id="9ca7b-128">Если имеется только один символ в верхнем регистре, убедитесь, что он не является первым символом пароля.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-128">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
- <span data-ttu-id="9ca7b-129">Убедитесь, что последние два символа пароля являются буквенными символами.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-129">Make sure that the last two characters of the password are letter characters.</span></span>  
  
- <span data-ttu-id="9ca7b-130">Не разрешайте пароли, в которых все символы введены из верхней строки клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="9ca7b-130">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca7b-131">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9ca7b-131">See also</span></span>

- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="9ca7b-132">[Безопасность веб-приложений ASP.NET](/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9ca7b-132">[ASP.NET Web Application Security](/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
