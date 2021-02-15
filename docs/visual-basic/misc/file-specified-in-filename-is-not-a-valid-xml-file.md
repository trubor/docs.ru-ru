---
description: 'Дополнительные сведения: файл, указанный в FileName, не является допустимым XML-файлом'
title: Файл, указанный в FileName, не является допустимым XML-файлом
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: c7d521986f3489345117a3947ed1e9b459af897e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472986"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="b3971-103">Файл, указанный в FileName, не является допустимым XML-файлом</span><span class="sxs-lookup"><span data-stu-id="b3971-103">File specified in FileName is not a valid XML file</span></span>

<span data-ttu-id="b3971-104">Указанное имя файла не представляет допустимый XML-файл.</span><span class="sxs-lookup"><span data-stu-id="b3971-104">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="b3971-105">Чтобы задать допустимую структуру и содержимое XML-документа, можно использовать схему DTD, Microsoft XML-Data Reduced (XDR) или языка определения схемы XML.</span><span class="sxs-lookup"><span data-stu-id="b3971-105">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="b3971-106">Схемы XSD — предпочтительный способ указания грамматики XML в платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b3971-106">XSD schemas are the preferred way to specify XML grammars in the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="b3971-107">В некоторых более ранних версиях Visual Studio **конструктор XML** — это конструктор для типизированных наборов данных и схемы XML.</span><span class="sxs-lookup"><span data-stu-id="b3971-107">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="b3971-108">**Конструктор XML** по-прежнему можно использовать для создания и редактирования файлов схемы XML.</span><span class="sxs-lookup"><span data-stu-id="b3971-108">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="b3971-109">Однако в Visual Studio 2012 конструктор для создания и редактирования типизированных наборов данных — это **Конструктор наборов данных**.</span><span class="sxs-lookup"><span data-stu-id="b3971-109">However, in Visual Studio 2012, the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="b3971-110">Дополнительные сведения см. в разделе [Создание и изменение типизированных наборов данных](/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="b3971-110">For more information, see [Creating and Editing Typed Datasets](/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b3971-111">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="b3971-111">To correct this error</span></span>

- <span data-ttu-id="b3971-112">Убедитесь, что вы указали правильное имя файла.</span><span class="sxs-lookup"><span data-stu-id="b3971-112">Check that you are supplying the correct file name.</span></span>

- <span data-ttu-id="b3971-113">Убедитесь, что указанный файл содержит допустимый XML, загрузив XML-файл, который требуется проверить, в **конструктор XML**.</span><span class="sxs-lookup"><span data-stu-id="b3971-113">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="b3971-114">В меню **XML** выберите **Проверить XML**.</span><span class="sxs-lookup"><span data-stu-id="b3971-114">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="b3971-115">Ошибки отображаются в **списке задач**.</span><span class="sxs-lookup"><span data-stu-id="b3971-115">Errors are displayed in the **Task List**.</span></span>

- <span data-ttu-id="b3971-116">Если XML-файл имеет связанную схему XML, удостоверьтесь, что элементы существуют в определенной структуре и что содержимое отдельных элементов соответствует объявленным типам данных, указанным в схеме.</span><span class="sxs-lookup"><span data-stu-id="b3971-116">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3971-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b3971-117">See also</span></span>

- <xref:System.Xml>
- [<span data-ttu-id="b3971-118">Практическое руководство. Анализ путей к файлам</span><span class="sxs-lookup"><span data-stu-id="b3971-118">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
