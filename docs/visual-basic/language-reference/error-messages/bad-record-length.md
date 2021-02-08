---
description: 'Дополнительные сведения о: неправильная длина записи'
title: Недопустимая длина записи
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 820597a3c4e157894aadb280ae141098cae7eed4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797059"
---
# <a name="bad-record-length"></a><span data-ttu-id="e6e39-103">Недопустимая длина записи</span><span class="sxs-lookup"><span data-stu-id="e6e39-103">Bad record length</span></span>

<span data-ttu-id="e6e39-104">Некоторые из возможных причин этой ошибки:</span><span class="sxs-lookup"><span data-stu-id="e6e39-104">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="e6e39-105">Длина переменной записи, указанной в `FileGet` `FileGetObject` `FilePut` операторе, или, `FilePutObject` отличается от длины, указанной в соответствующем `FileOpen` операторе.</span><span class="sxs-lookup"><span data-stu-id="e6e39-105">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
- <span data-ttu-id="e6e39-106">Переменная в `FilePut` `FilePutObject` операторе или включает строку переменной длины.</span><span class="sxs-lookup"><span data-stu-id="e6e39-106">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
- <span data-ttu-id="e6e39-107">Переменная в `FilePut` или `FilePutObject` включает `Variant` тип или.</span><span class="sxs-lookup"><span data-stu-id="e6e39-107">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e6e39-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="e6e39-108">To correct this error</span></span>  
  
1. <span data-ttu-id="e6e39-109">Убедитесь, что сумма размеров переменных фиксированной длины в определяемом пользователем типе, определяющем тип переменной записи, совпадает со значением, указанным в `FileOpen` `Len` предложении инструкции.</span><span class="sxs-lookup"><span data-stu-id="e6e39-109">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2. <span data-ttu-id="e6e39-110">Если переменная в `FilePut` `FilePutObject` операторе или содержит строку переменной длины, убедитесь, что длина строки переменной длины не меньше 2 символов, чем длина записи, заданная в `Len` предложении `FileOpen` инструкции.</span><span class="sxs-lookup"><span data-stu-id="e6e39-110">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3. <span data-ttu-id="e6e39-111">Если переменная в `FilePut` или имеет значение `FilePutObject` или включает, `Variant` Убедитесь, что длина строки переменной длины не меньше 4 байт, чем длина записи, указанная в `Len` предложении `FileOpen` инструкции.</span><span class="sxs-lookup"><span data-stu-id="e6e39-111">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e39-112">См. также</span><span class="sxs-lookup"><span data-stu-id="e6e39-112">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
