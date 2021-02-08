---
description: 'Дополнительные сведения: для журнала событий указано недопустимое имя'
title: Указано недопустимое имя для журнала событий
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 4786483fe0b1ae32a16b67bfb4f406587719011b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787374"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="68578-103">Указано недопустимое имя для журнала событий</span><span class="sxs-lookup"><span data-stu-id="68578-103">An invalid name was specified for the event log</span></span>

<span data-ttu-id="68578-104">Для журнала событий было указано недопустимое имя.</span><span class="sxs-lookup"><span data-stu-id="68578-104">An invalid name was specified for the event log.</span></span> <span data-ttu-id="68578-105">Обычно это является результатом недопустимых символов в имени, пустого имени файла или слишком длинного имени файла.</span><span class="sxs-lookup"><span data-stu-id="68578-105">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="68578-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="68578-106">To correct this error</span></span>  
  
- <span data-ttu-id="68578-107">Если указанное имя содержит более восьми символов, убедитесь, что отсутствует конфликт с именами других журналов событий.</span><span class="sxs-lookup"><span data-stu-id="68578-107">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="68578-108">При определении уникальности имени оцениваются только первые восемь символов.</span><span class="sxs-lookup"><span data-stu-id="68578-108">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="68578-109">Если указывается путь, убедитесь, что он анализируется правильно.</span><span class="sxs-lookup"><span data-stu-id="68578-109">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="68578-110">Проверьте имя на наличие недопустимых символов.</span><span class="sxs-lookup"><span data-stu-id="68578-110">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="68578-111">Символы, которые нельзя использовать в имени файла: `<`, `>`, `:`, `"`, `/`, `\`и `|`.</span><span class="sxs-lookup"><span data-stu-id="68578-111">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68578-112">См. также</span><span class="sxs-lookup"><span data-stu-id="68578-112">See also</span></span>

- [<span data-ttu-id="68578-113">Практическое руководство. Анализ путей к файлам</span><span class="sxs-lookup"><span data-stu-id="68578-113">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="68578-114">Практическое руководство. Переименование файла</span><span class="sxs-lookup"><span data-stu-id="68578-114">How to: Rename a File</span></span>](../developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
