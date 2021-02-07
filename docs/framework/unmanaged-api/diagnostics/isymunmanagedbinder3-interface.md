---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedBinder3'
title: Интерфейс ISymUnmanagedBinder3
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
ms.openlocfilehash: 6d2172fb119076cea6d0f912fb3f403d36856599
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689837"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="92092-103">Интерфейс ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="92092-103">ISymUnmanagedBinder3 Interface</span></span>

<span data-ttu-id="92092-104">Расширяет интерфейс связывателя символов.</span><span class="sxs-lookup"><span data-stu-id="92092-104">Extends the symbol binder interface.</span></span> <span data-ttu-id="92092-105">Получите этот интерфейс, вызвав метод `QueryInterface` для объекта, который реализует `ISymUnmanagedBinder` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="92092-105">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="92092-106">При открытии файла базы данных программы (PDB) из ненадежного источника возникает угроза безопасности.</span><span class="sxs-lookup"><span data-stu-id="92092-106">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92092-107">Методы</span><span class="sxs-lookup"><span data-stu-id="92092-107">Methods</span></span>  
  
|<span data-ttu-id="92092-108">Метод</span><span class="sxs-lookup"><span data-stu-id="92092-108">Method</span></span>|<span data-ttu-id="92092-109">Описание</span><span class="sxs-lookup"><span data-stu-id="92092-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92092-110">Метод GetReaderFromCallback</span><span class="sxs-lookup"><span data-stu-id="92092-110">GetReaderFromCallback Method</span></span>](isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="92092-111">Позволяет пользователю реализовать или предоставить через обратный вызов либо `IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` для получения сведений о каталоге отладки из памяти.</span><span class="sxs-lookup"><span data-stu-id="92092-111">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92092-112">Требования</span><span class="sxs-lookup"><span data-stu-id="92092-112">Requirements</span></span>  

 <span data-ttu-id="92092-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="92092-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92092-114">См. также</span><span class="sxs-lookup"><span data-stu-id="92092-114">See also</span></span>

- [<span data-ttu-id="92092-115">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="92092-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="92092-116">Интерфейс ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="92092-116">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="92092-117">Интерфейс ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="92092-117">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
