---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedBinder2'
title: Интерфейс ISymUnmanagedBinder2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
ms.openlocfilehash: 73847cdc9366ec18974fac261cbbad4d7dc6ccc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689889"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="75b4f-103">Интерфейс ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="75b4f-103">ISymUnmanagedBinder2 Interface</span></span>

<span data-ttu-id="75b4f-104">Представляет связыватель символов для неуправляемого кода и расширяет интерфейс [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="75b4f-104">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="75b4f-105">При открытии файла базы данных программы (PDB) из ненадежного источника возникает угроза безопасности.</span><span class="sxs-lookup"><span data-stu-id="75b4f-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75b4f-106">Методы</span><span class="sxs-lookup"><span data-stu-id="75b4f-106">Methods</span></span>  
  
|<span data-ttu-id="75b4f-107">Метод</span><span class="sxs-lookup"><span data-stu-id="75b4f-107">Method</span></span>|<span data-ttu-id="75b4f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="75b4f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75b4f-109">Метод GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="75b4f-109">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="75b4f-110">При наличии интерфейса метаданных и имени файла возвращает правильный интерфейс [ISymUnmanagedReader](isymunmanagedreader-interface.md) , который будет считывать символы отладки, связанные с модулем.</span><span class="sxs-lookup"><span data-stu-id="75b4f-110">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="75b4f-111">Предоставляет более широкие возможности поиска, чем метод [ISymUnmanagedBinder:: getreaderforfile:](isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="75b4f-111">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75b4f-112">Требования</span><span class="sxs-lookup"><span data-stu-id="75b4f-112">Requirements</span></span>  

 <span data-ttu-id="75b4f-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="75b4f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b4f-114">См. также</span><span class="sxs-lookup"><span data-stu-id="75b4f-114">See also</span></span>

- [<span data-ttu-id="75b4f-115">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="75b4f-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="75b4f-116">Интерфейс ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="75b4f-116">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="75b4f-117">Интерфейс ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="75b4f-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
