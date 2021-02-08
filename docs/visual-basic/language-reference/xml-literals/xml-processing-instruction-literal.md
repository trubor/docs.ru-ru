---
description: 'Дополнительные сведения: литерал инструкции обработки XML (Visual Basic)'
title: XML-литерал инструкции обработки
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 5037aab343cbe50ebc48614991e96da8198a481f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787530"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="1e5b5-103">Литерал инструкции обработки XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e5b5-103">XML Processing Instruction Literal (Visual Basic)</span></span>

<span data-ttu-id="1e5b5-104">Литерал, представляющий <xref:System.Xml.Linq.XProcessingInstruction> объект.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-104">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e5b5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1e5b5-105">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="1e5b5-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="1e5b5-106">Parts</span></span>  

 `<?`  
 <span data-ttu-id="1e5b5-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-107">Required.</span></span> <span data-ttu-id="1e5b5-108">Обозначает начало литерала инструкции обработки XML.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-108">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="1e5b5-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-109">Required.</span></span> <span data-ttu-id="1e5b5-110">Имя, указывающее, какое приложение предназначено для инструкции по обработке.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-110">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="1e5b5-111">Не может начинаться с "XML" или "XML".</span><span class="sxs-lookup"><span data-stu-id="1e5b5-111">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="1e5b5-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-112">Optional.</span></span> <span data-ttu-id="1e5b5-113">Строка, указывающая, как целевое приложение `piName` должно обрабатывать XML-документ.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-113">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="1e5b5-114">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-114">Required.</span></span> <span data-ttu-id="1e5b5-115">Обозначает конец инструкции по обработке.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-115">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e5b5-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1e5b5-116">Return Value</span></span>  

 <span data-ttu-id="1e5b5-117">Объект <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-117">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e5b5-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="1e5b5-118">Remarks</span></span>  

 <span data-ttu-id="1e5b5-119">Литералы инструкций обработки XML указывают, как приложения должны обрабатывать XML-документ.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-119">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="1e5b5-120">Когда приложение загружает XML-документ, приложение может проверить инструкции по обработке XML, чтобы определить способ обработки документа.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-120">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="1e5b5-121">Приложение интерпретирует значение `piName` и `piData` .</span><span class="sxs-lookup"><span data-stu-id="1e5b5-121">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="1e5b5-122">В литерале XML-документа используется синтаксис, схожий с инструкцией по обработке XML.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-122">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="1e5b5-123">Дополнительные сведения см. в разделе [XML-литерал документа](xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="1e5b5-123">For more information, see [XML Document Literal](xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e5b5-124">`piName`Элемент не может начинаться со строк "XML" или "XML", поскольку спецификация xml 1,0 резервирует эти идентификаторы.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-124">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="1e5b5-125">Литерал инструкции обработки XML можно назначить переменной или включить в литерал XML-документа.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-125">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e5b5-126">XML-литерал может охватывать несколько строк без символов продолжения строки.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-126">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="1e5b5-127">Это позволяет копировать содержимое из XML-документа и вставлять его непосредственно в Visual Basic программу.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-127">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="1e5b5-128">Компилятор Visual Basic преобразует литерал инструкции обработки XML в вызов <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> конструктора.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-128">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e5b5-129">Пример</span><span class="sxs-lookup"><span data-stu-id="1e5b5-129">Example</span></span>  

 <span data-ttu-id="1e5b5-130">В следующем примере создается инструкция по обработке, определяющая таблицу стилей для XML-документа.</span><span class="sxs-lookup"><span data-stu-id="1e5b5-130">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="1e5b5-131">См. также</span><span class="sxs-lookup"><span data-stu-id="1e5b5-131">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="1e5b5-132">XML-литерал документа</span><span class="sxs-lookup"><span data-stu-id="1e5b5-132">XML Document Literal</span></span>](xml-document-literal.md)
- [<span data-ttu-id="1e5b5-133">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="1e5b5-133">XML Literals</span></span>](index.md)
- [<span data-ttu-id="1e5b5-134">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e5b5-134">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
