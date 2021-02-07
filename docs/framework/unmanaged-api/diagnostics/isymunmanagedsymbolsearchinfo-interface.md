---
description: 'Дополнительные сведения о: интерфейс Исимунманажедсимболсеарчинфо'
title: Интерфейс ISymUnmanagedSymbolSearchInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
ms.openlocfilehash: 2f2ab198d2c54a9fcc5fa2e24b9196a38c583f81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762985"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="b659f-103">Интерфейс ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="b659f-103">ISymUnmanagedSymbolSearchInfo Interface</span></span>

<span data-ttu-id="b659f-104">Предоставляет методы, получающие сведения о пути поиска.</span><span class="sxs-lookup"><span data-stu-id="b659f-104">Provides methods that get information about the search path.</span></span> <span data-ttu-id="b659f-105">Получите этот интерфейс, вызвав `QueryInterface` для объекта, который реализует интерфейс [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b659f-105">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b659f-106">Методы</span><span class="sxs-lookup"><span data-stu-id="b659f-106">Methods</span></span>  
  
|<span data-ttu-id="b659f-107">Метод</span><span class="sxs-lookup"><span data-stu-id="b659f-107">Method</span></span>|<span data-ttu-id="b659f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b659f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b659f-109">Метод GetHRESULT</span><span class="sxs-lookup"><span data-stu-id="b659f-109">GetHRESULT Method</span></span>](isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="b659f-110">Возвращает значение HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b659f-110">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="b659f-111">Метод GetSearchPath</span><span class="sxs-lookup"><span data-stu-id="b659f-111">GetSearchPath Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="b659f-112">Возвращает путь поиска.</span><span class="sxs-lookup"><span data-stu-id="b659f-112">Gets the search path.</span></span>|  
|[<span data-ttu-id="b659f-113">Метод GetSearchPathLength</span><span class="sxs-lookup"><span data-stu-id="b659f-113">GetSearchPathLength Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="b659f-114">Возвращает длину пути поиска.</span><span class="sxs-lookup"><span data-stu-id="b659f-114">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b659f-115">Требования</span><span class="sxs-lookup"><span data-stu-id="b659f-115">Requirements</span></span>  

 <span data-ttu-id="b659f-116">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="b659f-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b659f-117">См. также</span><span class="sxs-lookup"><span data-stu-id="b659f-117">See also</span></span>

- [<span data-ttu-id="b659f-118">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="b659f-118">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
