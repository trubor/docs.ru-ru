---
description: 'Дополнительные сведения о: ввод за концом файла'
title: Оператор Input обнаружил конец файла
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: b65a57bdc56367518a93880be28781e56c9b99cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796045"
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="4f23b-103">Оператор Input обнаружил конец файла</span><span class="sxs-lookup"><span data-stu-id="4f23b-103">Input past end of file</span></span>

<span data-ttu-id="4f23b-104">Либо `Input` инструкция считывает из файла, который является пустым, либо в котором используются все данные, либо вы использовали `EOF` функцию с файлом, открытым для двоичного доступа.</span><span class="sxs-lookup"><span data-stu-id="4f23b-104">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4f23b-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="4f23b-105">To correct this error</span></span>  
  
1. <span data-ttu-id="4f23b-106">Используйте `EOF` функцию непосредственно перед `Input` оператором, чтобы определить конец файла.</span><span class="sxs-lookup"><span data-stu-id="4f23b-106">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2. <span data-ttu-id="4f23b-107">Если файл открыт для двоичного доступа, используйте `Seek` и `Loc` .</span><span class="sxs-lookup"><span data-stu-id="4f23b-107">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f23b-108">См. также</span><span class="sxs-lookup"><span data-stu-id="4f23b-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
