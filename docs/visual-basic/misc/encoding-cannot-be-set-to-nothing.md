---
description: 'Подробнее: кодировка не может принимать значение Nothing'
title: Параметру Encoding нельзя присвоить значение Nothing
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 4fa9cbd9488501b5295da8d8ace41ef06a706c12
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462999"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="7a8cc-103">Параметру Encoding нельзя присвоить значение Nothing</span><span class="sxs-lookup"><span data-stu-id="7a8cc-103">Encoding cannot be set to Nothing</span></span>

<span data-ttu-id="7a8cc-104">Не удалось выполнить чтение или запись в файл, так как параметр `encoding` установлен в значение `Nothing` , но требует допустимое значение.</span><span class="sxs-lookup"><span data-stu-id="7a8cc-104">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="7a8cc-105"><xref:System.Text.Encoding> используется для определения, какая кодировка должна использоваться при записи в файл.</span><span class="sxs-lookup"><span data-stu-id="7a8cc-105"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="7a8cc-106">Кодировка по умолчанию — UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7a8cc-106">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7a8cc-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="7a8cc-107">To correct this error</span></span>  
  
- <span data-ttu-id="7a8cc-108">Предоставьте допустимое значение для параметра `encoding` .</span><span class="sxs-lookup"><span data-stu-id="7a8cc-108">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a8cc-109">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7a8cc-109">See also</span></span>

- [<span data-ttu-id="7a8cc-110">Кодировки файлов</span><span class="sxs-lookup"><span data-stu-id="7a8cc-110">File Encodings</span></span>](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="7a8cc-111">Чтение из файлов</span><span class="sxs-lookup"><span data-stu-id="7a8cc-111">Reading from Files</span></span>](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="7a8cc-112">Запись в файлы</span><span class="sxs-lookup"><span data-stu-id="7a8cc-112">Writing to Files</span></span>](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="7a8cc-113">My. Computer. FileSystem. ReadAllText</span><span class="sxs-lookup"><span data-stu-id="7a8cc-113">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="7a8cc-114">My. Computer. FileSystem. WriteAllText</span><span class="sxs-lookup"><span data-stu-id="7a8cc-114">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
