---
title: Анализ других строк в .NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
ms.openlocfilehash: 352bd426c889996daa5f420ccc384947896dc118
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683749"
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="8a2c7-102">Анализ других строк в .NET</span><span class="sxs-lookup"><span data-stu-id="8a2c7-102">Parsing Other Strings in .NET</span></span>

<span data-ttu-id="8a2c7-103">Кроме числовых строк и строк <xref:System.DateTime> вы можете преобразовать строки, представляющих типы <xref:System.Char>, <xref:System.Boolean> или <xref:System.Enum>, в соответствующие типы данных.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="8a2c7-104">CHAR</span><span class="sxs-lookup"><span data-stu-id="8a2c7-104">Char</span></span>  

 <span data-ttu-id="8a2c7-105">Метод статического анализа, связанный с типом данных **Char**, полезен для преобразования строки, содержащей один символ, в его значение в кодировке Юникод.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="8a2c7-106">В следующем примере кода выполняется разбор строки в символ Юникода.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="8a2c7-107">Логическое</span><span class="sxs-lookup"><span data-stu-id="8a2c7-107">Boolean</span></span>  

 <span data-ttu-id="8a2c7-108">Тип данных **Boolean** содержит метод **Parse**, который можно использовать для преобразования строки, представляющей логическое значение в реальный тип **Boolean**.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="8a2c7-109">Этот метод не учитывает регистр и может успешно анализировать строку, содержащую значения "True" или "False".</span><span class="sxs-lookup"><span data-stu-id="8a2c7-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="8a2c7-110">Метод **Parse**, связанный с типом **Boolean**, может также анализировать строки, окруженные пробелами.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="8a2c7-111">Если передать ему любую другую строку, создается исключение <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="8a2c7-112">Следующий пример кода применяет метод **Parse** для преобразования строки в логическое значение.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="8a2c7-113">Перечисление</span><span class="sxs-lookup"><span data-stu-id="8a2c7-113">Enumeration</span></span>  

 <span data-ttu-id="8a2c7-114">Статический метод **Parse** можно использовать, чтобы инициализировать значение строки типом перечисления.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="8a2c7-115">Этот метод принимает тип перечисления, для которого нужно выполнить синтаксический анализ, анализируемую строку и необязательное логическое значение, обозначающее учет регистра при анализе.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="8a2c7-116">Анализируемая строка может содержать несколько значений, разделенных запятыми; перед этими значениями или после них могут быть один или несколько пробелов.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="8a2c7-117">Если строка содержит несколько значений, то возвращаемый объект будет содержать сочетание заданных значений, полученное с использованием побитовой операции OR.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="8a2c7-118">Следующий пример использует метод **Parse** для преобразования строкового представления в значение перечисления.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="8a2c7-119">Перечислению <xref:System.DayOfWeek> присваивается значение **Thursday**, найденное в строке.</span><span class="sxs-lookup"><span data-stu-id="8a2c7-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8a2c7-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8a2c7-120">See also</span></span>

- [<span data-ttu-id="8a2c7-121">Анализ строк в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8a2c7-121">Parsing Strings</span></span>](parsing-strings.md)
- [<span data-ttu-id="8a2c7-122">Типы форматирования</span><span class="sxs-lookup"><span data-stu-id="8a2c7-122">Formatting Types</span></span>](formatting-types.md)
- [<span data-ttu-id="8a2c7-123">Преобразование типов в .NET</span><span class="sxs-lookup"><span data-stu-id="8a2c7-123">Type Conversion in the .NET</span></span>](type-conversion.md)
