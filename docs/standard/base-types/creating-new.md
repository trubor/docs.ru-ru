---
title: Создание новых строк в .NET
description: Сведения о создании строк с помощью присваивания, конструкторов классов или методов System.String, объединяющих несколько строк, массивов строк или объектов в .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
ms.openlocfilehash: a8fec6c08d44212d1b7cdd5a34c9a27b0fc19746
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683879"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="ac711-103">Создание новых строк в .NET</span><span class="sxs-lookup"><span data-stu-id="ac711-103">Creating New Strings in .NET</span></span>

<span data-ttu-id="ac711-104">. NET позволяет создавать строки с помощью простой операции присваивания, а также перегружать конструктор класса для создания строк с помощью нескольких различных параметров.</span><span class="sxs-lookup"><span data-stu-id="ac711-104">.NET allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="ac711-105">Кроме того, .NET предоставляет в классе <xref:System.String?displayProperty=nameWithType> несколько методов для создания строковых объектов путем объединения строк, массивов строк или объектов.</span><span class="sxs-lookup"><span data-stu-id="ac711-105">.NET also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="ac711-106">Создание строк с помощью присваивания</span><span class="sxs-lookup"><span data-stu-id="ac711-106">Creating Strings Using Assignment</span></span>  

 <span data-ttu-id="ac711-107">Самый простой способ создать объект <xref:System.String> — присвоить строковый литерал объекту <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ac711-107">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="ac711-108">Создание строк с помощью конструктора класса</span><span class="sxs-lookup"><span data-stu-id="ac711-108">Creating Strings Using a Class Constructor</span></span>  

 <span data-ttu-id="ac711-109">С помощью перегруженного конструктора класса <xref:System.String> можно создавать строки из массивов символов.</span><span class="sxs-lookup"><span data-stu-id="ac711-109">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="ac711-110">Кроме того, строки можно создавать путем копирования того или иного знака указанное количество раз.</span><span class="sxs-lookup"><span data-stu-id="ac711-110">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="ac711-111">Методы, возвращающие строки</span><span class="sxs-lookup"><span data-stu-id="ac711-111">Methods that Return Strings</span></span>  

 <span data-ttu-id="ac711-112">В следующей таблице перечислено несколько полезных методов, которые возвращают строковые объекты.</span><span class="sxs-lookup"><span data-stu-id="ac711-112">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="ac711-113">Имя метода</span><span class="sxs-lookup"><span data-stu-id="ac711-113">Method name</span></span>|<span data-ttu-id="ac711-114">Использовать</span><span class="sxs-lookup"><span data-stu-id="ac711-114">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="ac711-115">Создание форматированной строки из набора объектов ввода.</span><span class="sxs-lookup"><span data-stu-id="ac711-115">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="ac711-116">Создание строк из двух или более строк.</span><span class="sxs-lookup"><span data-stu-id="ac711-116">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="ac711-117">Создание новой строки с помощью объединения массива строк.</span><span class="sxs-lookup"><span data-stu-id="ac711-117">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="ac711-118">Создание новой строки с помощью вставки строки в указанную позицию существующей строки.</span><span class="sxs-lookup"><span data-stu-id="ac711-118">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="ac711-119">Копирование указанных знаков в строке в указанную позицию в массиве символов.</span><span class="sxs-lookup"><span data-stu-id="ac711-119">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="ac711-120">Формат</span><span class="sxs-lookup"><span data-stu-id="ac711-120">Format</span></span>  

 <span data-ttu-id="ac711-121">Метод **String.Format** позволяет создавать форматированные строки и сцеплять строки, представляющие несколько объектов.</span><span class="sxs-lookup"><span data-stu-id="ac711-121">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="ac711-122">Этот метод автоматически преобразует в строку любой переданный объект.</span><span class="sxs-lookup"><span data-stu-id="ac711-122">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="ac711-123">Например, если приложение должно предоставить пользователю значение **Int32** и значение **DateTime**, с помощью метода **Format** вы можете соединить их в одну строку для отображения.</span><span class="sxs-lookup"><span data-stu-id="ac711-123">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="ac711-124">Сведения о правилах форматирования, используемых в этом методе, см. в разделе [Составное форматирование](composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="ac711-124">For information about formatting conventions used with this method, see the section on [composite formatting](composite-formatting.md).</span></span>  
  
 <span data-ttu-id="ac711-125">В следующем примере метод **Format** используется для создания строки, содержащей целочисленную переменную.</span><span class="sxs-lookup"><span data-stu-id="ac711-125">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="ac711-126">В этом примере <xref:System.DateTime.Now%2A?displayProperty=nameWithType> выводит текущую дату и время с учетом языка и региональных параметров, связанных с текущим потоком.</span><span class="sxs-lookup"><span data-stu-id="ac711-126">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="ac711-127">Concat</span><span class="sxs-lookup"><span data-stu-id="ac711-127">Concat</span></span>  

 <span data-ttu-id="ac711-128">Метод **String.Concat** позволяет легко создать новый строковый объект из двух или более существующих объектов.</span><span class="sxs-lookup"><span data-stu-id="ac711-128">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="ac711-129">Он позволяет использовать независимый от языка способ сцепления строк.</span><span class="sxs-lookup"><span data-stu-id="ac711-129">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="ac711-130">Этот метод принимает любой класс, производный от **System.Object**.</span><span class="sxs-lookup"><span data-stu-id="ac711-130">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="ac711-131">В следующем примере создается строка из двух существующих объектов строки и символа разделителя.</span><span class="sxs-lookup"><span data-stu-id="ac711-131">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="ac711-132">Join</span><span class="sxs-lookup"><span data-stu-id="ac711-132">Join</span></span>  

 <span data-ttu-id="ac711-133">Метод **String.Join** создает строку из массива строк и разделительной строки.</span><span class="sxs-lookup"><span data-stu-id="ac711-133">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="ac711-134">Этот метод полезен в случае необходимости сцепления нескольких строк и создания списка, отделенного, например, запятой.</span><span class="sxs-lookup"><span data-stu-id="ac711-134">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="ac711-135">В следующем примере используется пробел для привязки массива строк.</span><span class="sxs-lookup"><span data-stu-id="ac711-135">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="ac711-136">Insert</span><span class="sxs-lookup"><span data-stu-id="ac711-136">Insert</span></span>  

 <span data-ttu-id="ac711-137">Метод **String.Insert** создает новую строку, вставляя предоставленную строку в указанную позицию в другой строке.</span><span class="sxs-lookup"><span data-stu-id="ac711-137">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="ac711-138">Этот метод использует отсчитываемый от нуля индекс.</span><span class="sxs-lookup"><span data-stu-id="ac711-138">This method uses a zero-based index.</span></span> <span data-ttu-id="ac711-139">В следующем примере строка вставляется в пятую позицию индекса `MyString`, и создается новая строка с этим значением.</span><span class="sxs-lookup"><span data-stu-id="ac711-139">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="ac711-140">CopyTo</span><span class="sxs-lookup"><span data-stu-id="ac711-140">CopyTo</span></span>  

 <span data-ttu-id="ac711-141">Метод **String.CopyTo** копирует элементы строки в массив символов.</span><span class="sxs-lookup"><span data-stu-id="ac711-141">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="ac711-142">Можно указать начальный индекс строки и число копируемых символов.</span><span class="sxs-lookup"><span data-stu-id="ac711-142">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="ac711-143">Для копирования этому методу необходимы исходный индекс, массив знаков, индекс назначения и число символов.</span><span class="sxs-lookup"><span data-stu-id="ac711-143">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="ac711-144">Все индексы отсчитываются от нуля.</span><span class="sxs-lookup"><span data-stu-id="ac711-144">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="ac711-145">В следующем примере мы используем метод **CopyTo**, чтобы скопировать символы слова Hello из строкового объекта в позицию первого индекса в массиве символов.</span><span class="sxs-lookup"><span data-stu-id="ac711-145">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ac711-146">См. также</span><span class="sxs-lookup"><span data-stu-id="ac711-146">See also</span></span>

- [<span data-ttu-id="ac711-147">Базовые операции со строками в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ac711-147">Basic String Operations</span></span>](basic-string-operations.md)
- [<span data-ttu-id="ac711-148">Составное форматирование</span><span class="sxs-lookup"><span data-stu-id="ac711-148">Composite Formatting</span></span>](composite-formatting.md)
