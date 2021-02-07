---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedBinder'
title: Интерфейс ISymUnmanagedBinder
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
ms.openlocfilehash: 14ebccb028ab3388a8058dd05504c56a6df74c95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689928"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="65e22-103">Интерфейс ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="65e22-103">ISymUnmanagedBinder Interface</span></span>

<span data-ttu-id="65e22-104">Представляет модуль привязки символов для неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="65e22-104">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="65e22-105">При открытии файла базы данных программы (PDB) из ненадежного источника возникает угроза безопасности.</span><span class="sxs-lookup"><span data-stu-id="65e22-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65e22-106">Методы</span><span class="sxs-lookup"><span data-stu-id="65e22-106">Methods</span></span>  
  
|<span data-ttu-id="65e22-107">Метод</span><span class="sxs-lookup"><span data-stu-id="65e22-107">Method</span></span>|<span data-ttu-id="65e22-108">Описание</span><span class="sxs-lookup"><span data-stu-id="65e22-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65e22-109">Метод GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="65e22-109">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="65e22-110">При наличии интерфейса метаданных и имени файла возвращает правильную структуру [ISymUnmanagedReader](isymunmanagedreader-interface.md) , которая будет считывать отладочные символы, связанные с модулем.</span><span class="sxs-lookup"><span data-stu-id="65e22-110">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="65e22-111">Метод GetReaderFromStream</span><span class="sxs-lookup"><span data-stu-id="65e22-111">GetReaderFromStream Method</span></span>](isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="65e22-112">При наличии интерфейса метаданных и потока, содержащего хранилище символов, возвращает правильную структуру [ISymUnmanagedReader](isymunmanagedreader-interface.md) , которая будет считывать отладочные символы из заданного хранилища символов.</span><span class="sxs-lookup"><span data-stu-id="65e22-112">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65e22-113">Требования</span><span class="sxs-lookup"><span data-stu-id="65e22-113">Requirements</span></span>  

 <span data-ttu-id="65e22-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="65e22-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e22-115">См. также</span><span class="sxs-lookup"><span data-stu-id="65e22-115">See also</span></span>

- [<span data-ttu-id="65e22-116">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="65e22-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="65e22-117">Интерфейс ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="65e22-117">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="65e22-118">Интерфейс ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="65e22-118">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
