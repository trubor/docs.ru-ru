---
description: 'Дополнительные сведения: не удается считать поля с разделителями, так как двойная кавычка не является допустимым разделителем, если параметр EscapeQuotes имеет значение true'
title: Не удается прочитать поля с разделителями, поскольку двойные кавычки не являются допустимым разделителем, если параметр EscapeQuotes имеет значение True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: 066b5110eaddad74b64f1d86683d7ca2a0a619f7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474399"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="1abb4-103">Не удается прочитать поля с разделителями, поскольку двойные кавычки не являются допустимым разделителем, если параметр EscapeQuotes имеет значение True</span><span class="sxs-lookup"><span data-stu-id="1abb4-103">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>

<span data-ttu-id="1abb4-104">`TextFieldParser` не может читать из файла, поскольку в качестве разделителя указан знак кавычек ("), а `EscapeQuotes` имеет значение `True`.</span><span class="sxs-lookup"><span data-stu-id="1abb4-104">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1abb4-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="1abb4-105">To correct this error</span></span>  
  
- <span data-ttu-id="1abb4-106">Задайте для параметра `EscapeQuotes` значение `False`.</span><span class="sxs-lookup"><span data-stu-id="1abb4-106">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1abb4-107">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1abb4-107">See also</span></span>

- [<span data-ttu-id="1abb4-108">Метод TextFieldParser.SetDelimiters</span><span class="sxs-lookup"><span data-stu-id="1abb4-108">TextFieldParser.SetDelimiters Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [<span data-ttu-id="1abb4-109">Свойство TextFieldParser.Delimiters</span><span class="sxs-lookup"><span data-stu-id="1abb4-109">TextFieldParser.Delimiters Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [<span data-ttu-id="1abb4-110">Практическое руководство. Чтение из текстовых файлов с разделителями-запятыми</span><span class="sxs-lookup"><span data-stu-id="1abb4-110">How to: Read From Comma-Delimited Text Files</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="1abb4-111">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="1abb4-111">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
