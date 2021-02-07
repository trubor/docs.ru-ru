---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedReaderSymbolSearchInfo'
title: Интерфейс ISymUnmanagedReaderSymbolSearchInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedReaderSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: fde7e21d-1169-4bed-a34d-792e69652bf9
topic_type:
- apiref
ms.openlocfilehash: f5d13027709698df735af5fceac31f7b73741440
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763570"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a><span data-ttu-id="0348a-103">Интерфейс ISymUnmanagedReaderSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="0348a-103">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>

<span data-ttu-id="0348a-104">Предоставляет методы, которые получают сведения о поиске символов.</span><span class="sxs-lookup"><span data-stu-id="0348a-104">Provides methods that get symbol search information.</span></span> <span data-ttu-id="0348a-105">Получите этот интерфейс, вызвав `QueryInterface` для объекта, который реализует интерфейс [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0348a-105">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0348a-106">Методы</span><span class="sxs-lookup"><span data-stu-id="0348a-106">Methods</span></span>  
  
|<span data-ttu-id="0348a-107">Метод</span><span class="sxs-lookup"><span data-stu-id="0348a-107">Method</span></span>|<span data-ttu-id="0348a-108">Описание</span><span class="sxs-lookup"><span data-stu-id="0348a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0348a-109">Метод GetSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="0348a-109">GetSymbolSearchInfo Method</span></span>](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|<span data-ttu-id="0348a-110">Возвращает сведения о поиске символов.</span><span class="sxs-lookup"><span data-stu-id="0348a-110">Gets symbol search information.</span></span>|  
|[<span data-ttu-id="0348a-111">Метод GetSymbolSearchInfoCount</span><span class="sxs-lookup"><span data-stu-id="0348a-111">GetSymbolSearchInfoCount Method</span></span>](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|<span data-ttu-id="0348a-112">Возвращает число сведений о поиске символов.</span><span class="sxs-lookup"><span data-stu-id="0348a-112">Gets a count of symbol search information.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0348a-113">Требования</span><span class="sxs-lookup"><span data-stu-id="0348a-113">Requirements</span></span>  

 <span data-ttu-id="0348a-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="0348a-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0348a-115">См. также</span><span class="sxs-lookup"><span data-stu-id="0348a-115">See also</span></span>

- [<span data-ttu-id="0348a-116">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="0348a-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
