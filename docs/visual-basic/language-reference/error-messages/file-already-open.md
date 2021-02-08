---
description: 'Дополнительные сведения о: файл уже открыт'
title: Файл уже открыт
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 2f3345c15f4a3095a8e733c2c8424edb25b4dee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796305"
---
# <a name="file-already-open"></a><span data-ttu-id="b44fd-103">Файл уже открыт</span><span class="sxs-lookup"><span data-stu-id="b44fd-103">File already open</span></span>

<span data-ttu-id="b44fd-104">Иногда файл должен быть закрыт, прежде чем `FileOpen` может произойти другая операция.</span><span class="sxs-lookup"><span data-stu-id="b44fd-104">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="b44fd-105">Некоторые из возможных причин этой ошибки:</span><span class="sxs-lookup"><span data-stu-id="b44fd-105">Among the possible causes of this error are:</span></span>

- <span data-ttu-id="b44fd-106">Операция последовательного режима вывода `FileOpen` была выполнена для уже открытого файла</span><span class="sxs-lookup"><span data-stu-id="b44fd-106">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>

- <span data-ttu-id="b44fd-107">Оператор ссылается на открытый файл.</span><span class="sxs-lookup"><span data-stu-id="b44fd-107">A statement refers to an open file.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b44fd-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="b44fd-108">To correct this error</span></span>

- <span data-ttu-id="b44fd-109">Закройте файл перед выполнением инструкции.</span><span class="sxs-lookup"><span data-stu-id="b44fd-109">Close the file before executing the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="b44fd-110">См. также</span><span class="sxs-lookup"><span data-stu-id="b44fd-110">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
