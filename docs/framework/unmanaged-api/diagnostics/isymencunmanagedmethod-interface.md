---
description: 'Дополнительные сведения о: интерфейс ISymENCUnmanagedMethod'
title: Интерфейс ISymENCUnmanagedMethod
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
ms.openlocfilehash: 59dd56c20279b2507fc4432182d0abb5b3e9c289
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790325"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="fb75a-103">Интерфейс ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="fb75a-103">ISymENCUnmanagedMethod Interface</span></span>

<span data-ttu-id="fb75a-104">Предоставляет сведения для функции "изменить и продолжить".</span><span class="sxs-lookup"><span data-stu-id="fb75a-104">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb75a-105">Методы</span><span class="sxs-lookup"><span data-stu-id="fb75a-105">Methods</span></span>  
  
|<span data-ttu-id="fb75a-106">Метод</span><span class="sxs-lookup"><span data-stu-id="fb75a-106">Method</span></span>|<span data-ttu-id="fb75a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="fb75a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb75a-108">Метод GetDocumentsForMethod</span><span class="sxs-lookup"><span data-stu-id="fb75a-108">GetDocumentsForMethod Method</span></span>](isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="fb75a-109">Возвращает документы, в которых у этого метода есть строки.</span><span class="sxs-lookup"><span data-stu-id="fb75a-109">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="fb75a-110">Метод GetDocumentsForMethodCount</span><span class="sxs-lookup"><span data-stu-id="fb75a-110">GetDocumentsForMethodCount Method</span></span>](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="fb75a-111">Возвращает число документов, в которых у этого метода есть строки.</span><span class="sxs-lookup"><span data-stu-id="fb75a-111">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="fb75a-112">Метод GetFileNameFromOffset</span><span class="sxs-lookup"><span data-stu-id="fb75a-112">GetFileNameFromOffset Method</span></span>](isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="fb75a-113">Возвращает имя файла для строки, связанной со смещением.</span><span class="sxs-lookup"><span data-stu-id="fb75a-113">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="fb75a-114">Метод GetLineFromOffset</span><span class="sxs-lookup"><span data-stu-id="fb75a-114">GetLineFromOffset Method</span></span>](isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="fb75a-115">Возвращает сведения о строке, связанные со смещением.</span><span class="sxs-lookup"><span data-stu-id="fb75a-115">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="fb75a-116">Метод GetSourceExtentInDocument</span><span class="sxs-lookup"><span data-stu-id="fb75a-116">GetSourceExtentInDocument Method</span></span>](isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="fb75a-117">Возвращает наименьшую начальную строку и самую новую конечную строку для метода в определенном документе.</span><span class="sxs-lookup"><span data-stu-id="fb75a-117">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb75a-118">Требования</span><span class="sxs-lookup"><span data-stu-id="fb75a-118">Requirements</span></span>  

 <span data-ttu-id="fb75a-119">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="fb75a-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb75a-120">См. также</span><span class="sxs-lookup"><span data-stu-id="fb75a-120">See also</span></span>

- [<span data-ttu-id="fb75a-121">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="fb75a-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
