---
description: 'Дополнительные сведения: неправильный режим файла'
title: Недопустимый режим файла
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: da792407fb37f5c206be7ff39da14d314ef1e2d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797085"
---
# <a name="bad-file-mode"></a><span data-ttu-id="cbe9d-103">Недопустимый режим файла</span><span class="sxs-lookup"><span data-stu-id="cbe9d-103">Bad file mode</span></span>

<span data-ttu-id="cbe9d-104">Инструкции, используемые для манипулирования содержимым файлов, должны соответствовать режиму, в котором был открыт файл.</span><span class="sxs-lookup"><span data-stu-id="cbe9d-104">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="cbe9d-105">Возможные причины:</span><span class="sxs-lookup"><span data-stu-id="cbe9d-105">Possible causes include:</span></span>  
  
- <span data-ttu-id="cbe9d-106">`FilePutObject`Оператор или `FileGetObject` указывает последовательный файл.</span><span class="sxs-lookup"><span data-stu-id="cbe9d-106">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="cbe9d-107">`Print`Оператор указывает файл, Открытый для режима доступа, отличного от `Output` или `Append` .</span><span class="sxs-lookup"><span data-stu-id="cbe9d-107">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="cbe9d-108">`Input`Оператор указывает файл, Открытый для режима доступа, отличного от`Input`</span><span class="sxs-lookup"><span data-stu-id="cbe9d-108">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="cbe9d-109">Попытка записи в файл, доступный только для чтения.</span><span class="sxs-lookup"><span data-stu-id="cbe9d-109">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cbe9d-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="cbe9d-110">To correct this error</span></span>  
  
- <span data-ttu-id="cbe9d-111">Убедитесь `FilePutObject` , что `FileGetObject` ссылки ссылаются только на файлы, открытые для `Random` или `Binary` Access.</span><span class="sxs-lookup"><span data-stu-id="cbe9d-111">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="cbe9d-112">Убедитесь `Print` , что файл открыт для `Output` `Append` режима доступа или.</span><span class="sxs-lookup"><span data-stu-id="cbe9d-112">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="cbe9d-113">В противном случае используйте другую инструкцию для размещения данных в файле или повторно откройте файл в соответствующем режиме.</span><span class="sxs-lookup"><span data-stu-id="cbe9d-113">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="cbe9d-114">Убедитесь `Input` , что файл открыт для `Input` .</span><span class="sxs-lookup"><span data-stu-id="cbe9d-114">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="cbe9d-115">В противном случае используйте другую инструкцию для размещения данных в файле или повторного открытия файла в соответствующем режиме.</span><span class="sxs-lookup"><span data-stu-id="cbe9d-115">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="cbe9d-116">При записи в файл, доступный только для чтения, измените состояние чтения/записи файла или не пытайтесь выполнить запись в него.</span><span class="sxs-lookup"><span data-stu-id="cbe9d-116">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="cbe9d-117">Используйте функциональность объекта `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="cbe9d-117">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe9d-118">См. также</span><span class="sxs-lookup"><span data-stu-id="cbe9d-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="cbe9d-119">Устранение неполадок: Чтение из текстовых файлов и запись в такие файлы</span><span class="sxs-lookup"><span data-stu-id="cbe9d-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
