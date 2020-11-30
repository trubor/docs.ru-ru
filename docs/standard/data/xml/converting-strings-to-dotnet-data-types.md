---
title: Преобразование строк в типы данных .NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
ms.openlocfilehash: 0cee7481f9c002f860bff7f12b8be0bb763dadb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701475"
---
# <a name="convert-strings-to-net-data-types"></a><span data-ttu-id="387eb-102">Преобразование строк в типы данных .NET</span><span class="sxs-lookup"><span data-stu-id="387eb-102">Convert strings to .NET data types</span></span>

<span data-ttu-id="387eb-103">Если нужно преобразовать строку в тип данных .NET, используйте метод **XmlConvert**, соответствующий требованиям приложения.</span><span class="sxs-lookup"><span data-stu-id="387eb-103">If you want to convert a string to a .NET data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="387eb-104">Список всех методов преобразования, доступных в классе **XmlConvert**, можно найти в <xref:System.Xml.XmlConvert>.</span><span class="sxs-lookup"><span data-stu-id="387eb-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="387eb-105">Строка, возвращаемая методом **ToString**, представляет строковую версию переданных ему данных.</span><span class="sxs-lookup"><span data-stu-id="387eb-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="387eb-106">Кроме того, существует несколько типов .NET, которые преобразуются с помощью класса **XmlConvert**, но не используют методы класса **System.Convert**.</span><span class="sxs-lookup"><span data-stu-id="387eb-106">Additionally, there are several .NET types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="387eb-107">Класс **XmlConvert** следует спецификации типа данных XSD и содержит тип данных, для которого может выполняться сопоставление **XmlConvert**.</span><span class="sxs-lookup"><span data-stu-id="387eb-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="387eb-108">В приведенной ниже таблице перечислены типы данных .NET и строковые типы, возвращаемые с помощью сопоставления типа данных XSD.</span><span class="sxs-lookup"><span data-stu-id="387eb-108">The following table lists .NET data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="387eb-109">**System.Convert** не поддерживает обработку этих типов .NET.</span><span class="sxs-lookup"><span data-stu-id="387eb-109">These .NET types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="387eb-110">Тип .NET</span><span class="sxs-lookup"><span data-stu-id="387eb-110">.NET type</span></span>|<span data-ttu-id="387eb-111">Возвращаемая строка</span><span class="sxs-lookup"><span data-stu-id="387eb-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="387eb-112">логический</span><span class="sxs-lookup"><span data-stu-id="387eb-112">Boolean</span></span>|<span data-ttu-id="387eb-113">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="387eb-113">"true", "false"</span></span>|  
|<span data-ttu-id="387eb-114">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="387eb-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="387eb-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="387eb-115">"INF"</span></span>|  
|<span data-ttu-id="387eb-116">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="387eb-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="387eb-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="387eb-117">"-INF"</span></span>|  
|<span data-ttu-id="387eb-118">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="387eb-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="387eb-119">"INF"</span><span class="sxs-lookup"><span data-stu-id="387eb-119">"INF"</span></span>|  
|<span data-ttu-id="387eb-120">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="387eb-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="387eb-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="387eb-121">"-INF"</span></span>|  
|<span data-ttu-id="387eb-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="387eb-122">DateTime</span></span>|<span data-ttu-id="387eb-123">Используется формат «гггг-ММ-ддТЧЧ:мм:ссzzzzzz» и его сокращенные версии.</span><span class="sxs-lookup"><span data-stu-id="387eb-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="387eb-124">Временной диапазон</span><span class="sxs-lookup"><span data-stu-id="387eb-124">Timespan</span></span>|<span data-ttu-id="387eb-125">Используется формат PnYnMnTnHnMnS, то есть значение `P2Y10M15DT10H30M20S` соответствует длительности в 2 года, 10 месяцев, 15 дней, 10 часов, 30 минут и 20 секунд.</span><span class="sxs-lookup"><span data-stu-id="387eb-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="387eb-126">Если любой из типов .NET, представленных в таблице, преобразуется в строку с использованием метода **ToString**, возвращаемая строка имеет не базовый тип, а тип строки XSD.</span><span class="sxs-lookup"><span data-stu-id="387eb-126">If converting any of the .NET types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="387eb-127">Типы значений **DateTime** и **Timespan** отличаются тем, что **DateTime** представляет момент времени, а **TimeSpan** — интервал времени.</span><span class="sxs-lookup"><span data-stu-id="387eb-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="387eb-128">Форматы **DateTime** и **Timespan** приведены в спецификации типов данных схемы XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="387eb-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="387eb-129">Пример:</span><span class="sxs-lookup"><span data-stu-id="387eb-129">For example:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 <span data-ttu-id="387eb-130">**Выходные данные**</span><span class="sxs-lookup"><span data-stu-id="387eb-130">**Output**</span></span>  
  
 <span data-ttu-id="387eb-131">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="387eb-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="387eb-132">В следующем примере кода целочисленное значение преобразуется в строку.</span><span class="sxs-lookup"><span data-stu-id="387eb-132">The following code converts an integer to a string:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 <span data-ttu-id="387eb-133">**Выходные данные**</span><span class="sxs-lookup"><span data-stu-id="387eb-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="387eb-134">Однако если строка преобразуется в тип **Boolean**, **Single** или **Double**, возвращаемый тип .NET не совпадает с типом, который возвращается при использовании класса **System.Convert**.</span><span class="sxs-lookup"><span data-stu-id="387eb-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET type that's returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="387eb-135">Преобразование строки в тип Boolean</span><span class="sxs-lookup"><span data-stu-id="387eb-135">String to Boolean</span></span>  

 <span data-ttu-id="387eb-136">В следующей таблице показано, какие типы создаются для заданных входных строк при преобразовании строки в значение **Boolean** с помощью метода **ToBoolean**.</span><span class="sxs-lookup"><span data-stu-id="387eb-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="387eb-137">Допустимый строковый входной параметр</span><span class="sxs-lookup"><span data-stu-id="387eb-137">Valid string input parameter</span></span>|<span data-ttu-id="387eb-138">Тип выходных данных .NET</span><span class="sxs-lookup"><span data-stu-id="387eb-138">.NET output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="387eb-139">True</span><span class="sxs-lookup"><span data-stu-id="387eb-139">"true"</span></span>|<span data-ttu-id="387eb-140">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="387eb-140">Boolean.True</span></span>|  
|<span data-ttu-id="387eb-141">"1"</span><span class="sxs-lookup"><span data-stu-id="387eb-141">"1"</span></span>|<span data-ttu-id="387eb-142">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="387eb-142">Boolean.True</span></span>|  
|<span data-ttu-id="387eb-143">"false"</span><span class="sxs-lookup"><span data-stu-id="387eb-143">"false"</span></span>|<span data-ttu-id="387eb-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="387eb-144">Boolean.False</span></span>|  
|<span data-ttu-id="387eb-145">"0"</span><span class="sxs-lookup"><span data-stu-id="387eb-145">"0"</span></span>|<span data-ttu-id="387eb-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="387eb-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="387eb-147">Например, пусть задан следующий XML-код.</span><span class="sxs-lookup"><span data-stu-id="387eb-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="387eb-148">**Ввод**</span><span class="sxs-lookup"><span data-stu-id="387eb-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>
```  
  
 <span data-ttu-id="387eb-149">Обе записи обрабатываются следующим кодом, где **bvalue** имеет значение **System.Boolean.True**.</span><span class="sxs-lookup"><span data-stu-id="387eb-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="387eb-150">Преобразование строки в тип Single</span><span class="sxs-lookup"><span data-stu-id="387eb-150">String to Single</span></span>  

 <span data-ttu-id="387eb-151">В следующей таблице показано, какие типы создаются для заданных входных строк при преобразовании строки в значение **Single** с помощью метода **ToSingle**.</span><span class="sxs-lookup"><span data-stu-id="387eb-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="387eb-152">Допустимый строковый входной параметр</span><span class="sxs-lookup"><span data-stu-id="387eb-152">Valid string input parameter</span></span>|<span data-ttu-id="387eb-153">Тип выходных данных .NET</span><span class="sxs-lookup"><span data-stu-id="387eb-153">.NET output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="387eb-154">"INF"</span><span class="sxs-lookup"><span data-stu-id="387eb-154">"INF"</span></span>|<span data-ttu-id="387eb-155">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="387eb-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="387eb-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="387eb-156">"-INF"</span></span>|<span data-ttu-id="387eb-157">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="387eb-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="387eb-158">Преобразование строки в тип Double</span><span class="sxs-lookup"><span data-stu-id="387eb-158">String to Double</span></span>  

 <span data-ttu-id="387eb-159">В следующей таблице показано, какие типы создаются для заданных входных строк при преобразовании строки в значение **Double** с помощью метода **ToDouble**.</span><span class="sxs-lookup"><span data-stu-id="387eb-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="387eb-160">Допустимый строковый входной параметр</span><span class="sxs-lookup"><span data-stu-id="387eb-160">Valid string input parameter</span></span>|<span data-ttu-id="387eb-161">Тип выходных данных .NET</span><span class="sxs-lookup"><span data-stu-id="387eb-161">.NET output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="387eb-162">"INF"</span><span class="sxs-lookup"><span data-stu-id="387eb-162">"INF"</span></span>|<span data-ttu-id="387eb-163">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="387eb-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="387eb-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="387eb-164">"-INF"</span></span>|<span data-ttu-id="387eb-165">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="387eb-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="387eb-166">Следующий код записывает строку `<Infinity>INF</Infinity>`:</span><span class="sxs-lookup"><span data-stu-id="387eb-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="387eb-167">См. также</span><span class="sxs-lookup"><span data-stu-id="387eb-167">See also</span></span>

- [<span data-ttu-id="387eb-168">Преобразование типов XML-данных</span><span class="sxs-lookup"><span data-stu-id="387eb-168">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="387eb-169">Преобразование типов .NET в строки</span><span class="sxs-lookup"><span data-stu-id="387eb-169">Converting .NET Types to Strings</span></span>](converting-dotnet-types-to-strings.md)
