---
description: 'Дополнительные сведения о: BC36810: ошибка при компиляции XML-схем в проекте'
title: При компиляции XML-схем в проекте возникли ошибки
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 78e88208c0d3df12e7bad8ab46b1d91bce559923
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796487"
---
# <a name="bc36810-errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="391c9-103">BC36810: произошли ошибки при компиляции XML-схем в проекте</span><span class="sxs-lookup"><span data-stu-id="391c9-103">BC36810: Errors occurred while compiling the XML schemas in the project</span></span>

<span data-ttu-id="391c9-104">Произошли ошибки при компиляции XML-схем в проекте.</span><span class="sxs-lookup"><span data-stu-id="391c9-104">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="391c9-105">По этой причине XML IntelliSense недоступен.</span><span class="sxs-lookup"><span data-stu-id="391c9-105">Because of this, XML IntelliSense is not available.</span></span>

 <span data-ttu-id="391c9-106">Ошибка в схеме определения схемы XML (XSD), включенной в проект.</span><span class="sxs-lookup"><span data-stu-id="391c9-106">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="391c9-107">Эта ошибка возникает при добавлении файла XSD-схемы (XSD), который конфликтует с существующим набором схем XSD для проекта.</span><span class="sxs-lookup"><span data-stu-id="391c9-107">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>

 <span data-ttu-id="391c9-108">**Идентификатор ошибки:** BC36810</span><span class="sxs-lookup"><span data-stu-id="391c9-108">**Error ID:** BC36810</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="391c9-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="391c9-109">To correct this error</span></span>

- <span data-ttu-id="391c9-110">Дважды щелкните предупреждение в окне **Список ошибок** .</span><span class="sxs-lookup"><span data-stu-id="391c9-110">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="391c9-111">Visual Basic перейдет к расположению в XSD-файле, который является источником предупреждения.</span><span class="sxs-lookup"><span data-stu-id="391c9-111">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="391c9-112">Исправьте ошибку в схеме XSD.</span><span class="sxs-lookup"><span data-stu-id="391c9-112">Correct the error in the XSD schema.</span></span>

- <span data-ttu-id="391c9-113">Убедитесь, что в проект включены все необходимые файлы XSD-схемы (. xsd).</span><span class="sxs-lookup"><span data-stu-id="391c9-113">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="391c9-114">Чтобы просмотреть XSD-файлы в **Обозреватель решений**, может потребоваться выбрать пункт **Показать все файлы** в меню **проект** .</span><span class="sxs-lookup"><span data-stu-id="391c9-114">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="391c9-115">Щелкните правой кнопкой мыши XSD-файл и выберите **включить в проект** , чтобы включить файл в проект.</span><span class="sxs-lookup"><span data-stu-id="391c9-115">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>

- <span data-ttu-id="391c9-116">Если используется Мастер XML для схемы, эта ошибка может возникать, если вы выводите схемы несколько раз из одного источника.</span><span class="sxs-lookup"><span data-stu-id="391c9-116">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="391c9-117">В этом случае можно удалить существующие файлы XSD-схемы из проекта, добавить новый XML в шаблон элемента схемы, а затем предоставить мастеру XML для схемы все применимые источники XML для вашего проекта.</span><span class="sxs-lookup"><span data-stu-id="391c9-117">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>

- <span data-ttu-id="391c9-118">Если в схеме XSD не обнаружена ошибка, компилятор XML может не иметь достаточной информации для предоставления подробного сообщения об ошибке.</span><span class="sxs-lookup"><span data-stu-id="391c9-118">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="391c9-119">Если вы убедитесь, что пространства имен XML для XSD-файлов, включаемых в проект, соответствуют пространствам имен XML, определенным для набора XML-схем в Visual Studio, вы можете получить более подробные сведения об ошибках.</span><span class="sxs-lookup"><span data-stu-id="391c9-119">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="391c9-120">См. также</span><span class="sxs-lookup"><span data-stu-id="391c9-120">See also</span></span>

- [<span data-ttu-id="391c9-121">Окно список ошибок</span><span class="sxs-lookup"><span data-stu-id="391c9-121">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)
- [<span data-ttu-id="391c9-122">XML</span><span class="sxs-lookup"><span data-stu-id="391c9-122">XML</span></span>](../../programming-guide/language-features/xml/index.md)
