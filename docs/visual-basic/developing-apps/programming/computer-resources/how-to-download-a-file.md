---
description: 'Подробнее о следующем: Практическое руководство. Загрузка файла в Visual Basic'
title: Практическое руководство. Скачивание файла
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: dd296a5958431b74ccc8e0fb41a49073f4847ded
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797696"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="e801c-103">Практическое руководство. Загрузка файла в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e801c-103">How to: Download a File in Visual Basic</span></span>

<span data-ttu-id="e801c-104">Метод <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> можно использовать для скачивания удаленного файла и сохранения его в определенном месте.</span><span class="sxs-lookup"><span data-stu-id="e801c-104">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="e801c-105">Если для параметра `ShowUI` установлено значение `True`, отображается диалоговое окно, показывающее ход загрузки и позволяющее пользователю отменить операцию.</span><span class="sxs-lookup"><span data-stu-id="e801c-105">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="e801c-106">По умолчанию существующие файлы с тем же именем не перезаписываются. Если требуется перезаписывать существующие файлы, установите для параметра `overwrite` значение `True`.</span><span class="sxs-lookup"><span data-stu-id="e801c-106">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>

<span data-ttu-id="e801c-107">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="e801c-107">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="e801c-108">Недопустимое имя диска (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="e801c-108">Drive name is not valid (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="e801c-109">Не была предоставлена необходимая аутентификация (<xref:System.UnauthorizedAccessException> или <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="e801c-109">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="e801c-110">Сервер не отвечает в пределах указанного `connectionTimeout` (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="e801c-110">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>

- <span data-ttu-id="e801c-111">Запрос отклонен веб-сайтом (<xref:System.Net.WebException>).</span><span class="sxs-lookup"><span data-stu-id="e801c-111">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> <span data-ttu-id="e801c-112">По имени файла не всегда можно с уверенностью судить о его содержимом.</span><span class="sxs-lookup"><span data-stu-id="e801c-112">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="e801c-113">Например, файл с именем Form1.vb может вовсе не быть исходным файлом Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e801c-113">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="e801c-114">Следует проверять все входные данные перед использованием их в приложении.</span><span class="sxs-lookup"><span data-stu-id="e801c-114">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="e801c-115">Содержимое файла может отличаться от ожидаемого, поэтому может не удаться прочесть файл с помощью методов чтения.</span><span class="sxs-lookup"><span data-stu-id="e801c-115">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

### <a name="to-download-a-file"></a><span data-ttu-id="e801c-116">Загрузка файла</span><span class="sxs-lookup"><span data-stu-id="e801c-116">To download a file</span></span>

- <span data-ttu-id="e801c-117">Используйте метод `DownloadFile`, чтобы скачать файл, указав расположение конечного файла в виде строки или URI и задав расположение для сохранения файла.</span><span class="sxs-lookup"><span data-stu-id="e801c-117">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="e801c-118">В этом примере выполняется загрузка файла `WineList.txt` из `http://www.cohowinery.com/downloads` и его сохранение в `C:\Documents and Settings\All Users\Documents`:</span><span class="sxs-lookup"><span data-stu-id="e801c-118">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="e801c-119">Загрузка файла с указанием времени ожидания</span><span class="sxs-lookup"><span data-stu-id="e801c-119">To download a file, specifying a time-out interval</span></span>

- <span data-ttu-id="e801c-120">Используйте метод `DownloadFile`, чтобы скачать файл, указав расположение конечного файла в виде строки или URI, задав расположение для сохранения файла и интервал времени ожидания в миллисекундах (значение по умолчанию 1000).</span><span class="sxs-lookup"><span data-stu-id="e801c-120">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="e801c-121">В этом примере выполняется загрузка файла `WineList.txt` из `http://www.cohowinery.com/downloads` и его сохранение в `C:\Documents and Settings\All Users\Documents` с указанием интервала ожидания 500 миллисекунд:</span><span class="sxs-lookup"><span data-stu-id="e801c-121">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="e801c-122">Загрузка файла с указанием имени пользователя и пароля</span><span class="sxs-lookup"><span data-stu-id="e801c-122">To download a file, supplying a user name and password</span></span>

- <span data-ttu-id="e801c-123">Используйте метод `DownLoadFile`, чтобы скачать файл, указав расположение конечного файла в виде строки или URI и задав расположение для сохранения файла, имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="e801c-123">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="e801c-124">В этом примере выполняется загрузка файла `WineList.txt` из `http://www.cohowinery.com/downloads` и его сохранение в `C:\Documents and Settings\All Users\Documents` с именем пользователя `anonymous` и пустым паролем.</span><span class="sxs-lookup"><span data-stu-id="e801c-124">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > <span data-ttu-id="e801c-125">Протокол FTP, используемый методом `DownLoadFile`, отправляет данные, включая пароли, в формате обычного текста и не должен использоваться для передачи важных сведений.</span><span class="sxs-lookup"><span data-stu-id="e801c-125">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="e801c-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e801c-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="e801c-127">Практическое руководство. Отправка файла</span><span class="sxs-lookup"><span data-stu-id="e801c-127">How to: Upload a File</span></span>](how-to-upload-a-file.md)
- [<span data-ttu-id="e801c-128">Практическое руководство. Анализ путей к файлам</span><span class="sxs-lookup"><span data-stu-id="e801c-128">How to: Parse File Paths</span></span>](../drives-directories-files/how-to-parse-file-paths.md)
