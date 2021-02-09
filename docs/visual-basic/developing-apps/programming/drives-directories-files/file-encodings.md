---
description: 'Узнайте подробнее о: Кодировки файлов (Visual Basic)'
title: Кодировки файлов
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: f573b5d8f83c27cbf4ddacb9fd40474d7d1be1ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675368"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="4caca-103">Кодировки файлов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4caca-103">File Encodings (Visual Basic)</span></span>

<span data-ttu-id="4caca-104">Кодировки файлов (или кодировки символов) определяют отображение символов при обработке текстов.</span><span class="sxs-lookup"><span data-stu-id="4caca-104">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="4caca-105">Одна кодировка может быть предпочтительнее другой с точки зрения возможности или невозможности оперирования языковыми символами, хотя обычно предпочитается Юникод.</span><span class="sxs-lookup"><span data-stu-id="4caca-105">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>

<span data-ttu-id="4caca-106">При чтении или записи в файлы несоответствие кодировок файлов может привести к исключениям или неверным результатам.</span><span class="sxs-lookup"><span data-stu-id="4caca-106">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>

## <a name="types-of-encodings"></a><span data-ttu-id="4caca-107">Типы кодировок</span><span class="sxs-lookup"><span data-stu-id="4caca-107">Types of Encodings</span></span>

<span data-ttu-id="4caca-108">Юникод является предпочтительной кодировкой при работе с файлами.</span><span class="sxs-lookup"><span data-stu-id="4caca-108">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="4caca-109">Юникод — мировой стандарт кодировки символов, в котором используются 16-разрядные кодовые значения для представления всех символов, используемых в современных вычислениях, включая технические символы и специальные символы, используемые в издательском деле.</span><span class="sxs-lookup"><span data-stu-id="4caca-109">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>

<span data-ttu-id="4caca-110">Предыдущие стандарты кодировок состояли из традиционных наборов знаков, таких как набор знаков ANSI Windows, использующий 8-разрядные кодовые значения, или комбинаций из 8-разрядных кодовых значений для представления символов, используемых в конкретном языке или географическом регионе.</span><span class="sxs-lookup"><span data-stu-id="4caca-110">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>

## <a name="encoding-class"></a><span data-ttu-id="4caca-111">Класс Encoding</span><span class="sxs-lookup"><span data-stu-id="4caca-111">Encoding Class</span></span>

<span data-ttu-id="4caca-112">Класс <xref:System.Text.Encoding> представляет кодировку символов.</span><span class="sxs-lookup"><span data-stu-id="4caca-112">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="4caca-113">В этой таблице перечислены типы доступных кодировок и дано их описание.</span><span class="sxs-lookup"><span data-stu-id="4caca-113">This table lists the type of encodings available and describes each.</span></span>

|<span data-ttu-id="4caca-114">Имя</span><span class="sxs-lookup"><span data-stu-id="4caca-114">Name</span></span>|<span data-ttu-id="4caca-115">Описание</span><span class="sxs-lookup"><span data-stu-id="4caca-115">Description</span></span>|
|---|---|
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="4caca-116">Представляет кодировку ASCII символов Юникода.</span><span class="sxs-lookup"><span data-stu-id="4caca-116">Represents an ASCII character encoding of Unicode characters.</span></span>|
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="4caca-117">Представляет кодировку символов Юникода в формате UTF-16.</span><span class="sxs-lookup"><span data-stu-id="4caca-117">Represents a UTF-16 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="4caca-118">Представляет кодировку символов Юникода в формате UTF-32.</span><span class="sxs-lookup"><span data-stu-id="4caca-118">Represents a UTF-32 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="4caca-119">Представляет кодировку UTF-7 символов Юникода.</span><span class="sxs-lookup"><span data-stu-id="4caca-119">Represents a UTF-7 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="4caca-120">Представляет кодировку символов Юникода в формате UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4caca-120">Represents a UTF-8 encoding of Unicode characters.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4caca-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4caca-121">See also</span></span>

- [<span data-ttu-id="4caca-122">Чтение из файлов</span><span class="sxs-lookup"><span data-stu-id="4caca-122">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="4caca-123">Запись в файлы</span><span class="sxs-lookup"><span data-stu-id="4caca-123">Writing to Files</span></span>](writing-to-files.md)
