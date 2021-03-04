---
description: 'Дополнительные сведения о: BC31019: не удается выполнить запись в выходной файл " <filename> ": <error>'
title: 'Не удается выполнить запись в файл результатов <filename>: <error>'
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 86ddd01764d51c3050186e99e047edb8aba158eb
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104811"
---
# <a name="bc31019-unable-to-write-to-output-file-filename-error"></a><span data-ttu-id="f51dc-103">BC31019: не удалось выполнить запись в выходной файл " \<filename> ": \<error></span><span class="sxs-lookup"><span data-stu-id="f51dc-103">BC31019: Unable to write to output file '\<filename>': \<error></span></span>

<span data-ttu-id="f51dc-104">Возникла проблема при создании файла.</span><span class="sxs-lookup"><span data-stu-id="f51dc-104">There was a problem creating the file.</span></span>

 <span data-ttu-id="f51dc-105">Не удается открыть выходной файл для записи.</span><span class="sxs-lookup"><span data-stu-id="f51dc-105">An output file cannot be opened for writing.</span></span> <span data-ttu-id="f51dc-106">Файл (или содержащая его папка) может быть открыт другим процессом для монопольного использования либо может иметь установленный атрибут "только для чтения".</span><span class="sxs-lookup"><span data-stu-id="f51dc-106">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>

 <span data-ttu-id="f51dc-107">Распространенные ситуации, в которых файл открыт для монопольного доступа.</span><span class="sxs-lookup"><span data-stu-id="f51dc-107">Common situations where a file is opened exclusively are:</span></span>

- <span data-ttu-id="f51dc-108">Приложение уже запущено и использует свои файлы.</span><span class="sxs-lookup"><span data-stu-id="f51dc-108">The application is already running and using its files.</span></span> <span data-ttu-id="f51dc-109">Чтобы решить эту проблему, убедитесь, что приложение не запущено.</span><span class="sxs-lookup"><span data-stu-id="f51dc-109">To solve this problem, make sure that the application is not running.</span></span>

- <span data-ttu-id="f51dc-110">Этот файл открыло другое приложение.</span><span class="sxs-lookup"><span data-stu-id="f51dc-110">Another application has opened the file.</span></span> <span data-ttu-id="f51dc-111">Чтобы решить эту проблему, убедитесь, что другое приложение не осуществляет доступ к файлу.</span><span class="sxs-lookup"><span data-stu-id="f51dc-111">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="f51dc-112">Не всегда очевидно, какое именно приложение осуществляет доступ к файлам, в этом случае самым простым способом завершения приложения может оказаться перезапуск компьютера.</span><span class="sxs-lookup"><span data-stu-id="f51dc-112">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>

 <span data-ttu-id="f51dc-113">Если хотя бы один из выходных файлов проекта доступен только для чтения, возникает это исключение.</span><span class="sxs-lookup"><span data-stu-id="f51dc-113">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>

 <span data-ttu-id="f51dc-114">**Идентификатор ошибки:** BC31019</span><span class="sxs-lookup"><span data-stu-id="f51dc-114">**Error ID:** BC31019</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="f51dc-115">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="f51dc-115">To correct this error</span></span>

1. <span data-ttu-id="f51dc-116">Скомпилируйте программу еще раз, чтобы узнать, повторится ли ошибка.</span><span class="sxs-lookup"><span data-stu-id="f51dc-116">Compile the program again to see if the error recurs.</span></span>

2. <span data-ttu-id="f51dc-117">Если ошибка не исчезает, сохраните работу и перезапустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f51dc-117">If the error continues, save your work and restart Visual Studio.</span></span>

3. <span data-ttu-id="f51dc-118">Если ошибка возникает снова, перезапустите компьютер.</span><span class="sxs-lookup"><span data-stu-id="f51dc-118">If the error continues, restart the computer.</span></span>

4. <span data-ttu-id="f51dc-119">Если ошибка повторяется, переустановите Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f51dc-119">If the error recurs, reinstall Visual Basic.</span></span>

5. <span data-ttu-id="f51dc-120">Если после переустановки ошибка не устранена, уведомите службу технической поддержки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="f51dc-120">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>

### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="f51dc-121">Проверка атрибутов файла в проводнике</span><span class="sxs-lookup"><span data-stu-id="f51dc-121">To check file attributes in File Explorer</span></span>

1. <span data-ttu-id="f51dc-122">Откройте нужную папку.</span><span class="sxs-lookup"><span data-stu-id="f51dc-122">Open the folder you are interested in.</span></span>

2. <span data-ttu-id="f51dc-123">Щелкните значок **представления** и выберите **подробные сведения**.</span><span class="sxs-lookup"><span data-stu-id="f51dc-123">Click the **Views** icon and choose **Details**.</span></span>

3. <span data-ttu-id="f51dc-124">Щелкните правой кнопкой мыши заголовок столбца и выберите в раскрывающемся списке пункт **атрибуты** .</span><span class="sxs-lookup"><span data-stu-id="f51dc-124">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>

### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="f51dc-125">Изменение атрибутов файла или папки</span><span class="sxs-lookup"><span data-stu-id="f51dc-125">To change the attributes of a file or folder</span></span>

1. <span data-ttu-id="f51dc-126">В **проводнике** щелкните правой кнопкой мыши файл или папку и выберите пункт **свойства**.</span><span class="sxs-lookup"><span data-stu-id="f51dc-126">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>

2. <span data-ttu-id="f51dc-127">В разделе **атрибуты** вкладки **Общие** снимите флажок **только для чтения** .</span><span class="sxs-lookup"><span data-stu-id="f51dc-127">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>

3. <span data-ttu-id="f51dc-128">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f51dc-128">Press **OK**.</span></span>

## <a name="see-also"></a><span data-ttu-id="f51dc-129">См. также</span><span class="sxs-lookup"><span data-stu-id="f51dc-129">See also</span></span>

- [<span data-ttu-id="f51dc-130">Параметры обратной связи Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f51dc-130">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
