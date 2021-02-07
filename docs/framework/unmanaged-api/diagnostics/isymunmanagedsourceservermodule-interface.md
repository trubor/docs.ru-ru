---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedSourceServerModule'
title: Интерфейс ISymUnmanagedSourceServerModule
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule
helpviewer_keywords:
- ISymUnmanagedSourceServerModule interface [.NET Framework debugging]
ms.assetid: a19b23bd-2061-476e-b67d-252f57404f8b
topic_type:
- apiref
ms.openlocfilehash: c837af4cda443ec93bfbaa2d73feeb2b8f8a2803
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763128"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="8569e-103">Интерфейс ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="8569e-103">ISymUnmanagedSourceServerModule Interface</span></span>

<span data-ttu-id="8569e-104">Предоставляет данные сервера-источника для модуля.</span><span class="sxs-lookup"><span data-stu-id="8569e-104">Provides source server data for a module.</span></span> <span data-ttu-id="8569e-105">Получите этот интерфейс, вызвав `QueryInterface` для объекта, который реализует интерфейс [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8569e-105">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8569e-106">Методы</span><span class="sxs-lookup"><span data-stu-id="8569e-106">Methods</span></span>  
  
|<span data-ttu-id="8569e-107">Метод</span><span class="sxs-lookup"><span data-stu-id="8569e-107">Method</span></span>|<span data-ttu-id="8569e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8569e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8569e-109">Метод GetSourceServerData</span><span class="sxs-lookup"><span data-stu-id="8569e-109">GetSourceServerData Method</span></span>](isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="8569e-110">Возвращает данные исходного сервера для модуля.</span><span class="sxs-lookup"><span data-stu-id="8569e-110">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8569e-111">Требования</span><span class="sxs-lookup"><span data-stu-id="8569e-111">Requirements</span></span>  

 <span data-ttu-id="8569e-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="8569e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8569e-113">См. также</span><span class="sxs-lookup"><span data-stu-id="8569e-113">See also</span></span>

- [<span data-ttu-id="8569e-114">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="8569e-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
