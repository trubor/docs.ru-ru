---
description: Дополнительные сведения о методе Преклосеассембли
title: Метод PreCloseAssembly
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
ms.openlocfilehash: 088a5bba654b3442da64672991d76537e9b4722c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662524"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="68f07-103">Метод PreCloseAssembly</span><span class="sxs-lookup"><span data-stu-id="68f07-103">PreCloseAssembly Method</span></span>

<span data-ttu-id="68f07-104">Закрывает файл сборки.</span><span class="sxs-lookup"><span data-stu-id="68f07-104">Closes the assembly file.</span></span> <span data-ttu-id="68f07-105">Вызовите этот метод после закрытия всех остальных файлов, но перед закрытием файла сборки.</span><span class="sxs-lookup"><span data-stu-id="68f07-105">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="68f07-106">Не вызывайте этот метод для непривязанных модулей.</span><span class="sxs-lookup"><span data-stu-id="68f07-106">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68f07-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="68f07-107">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="68f07-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="68f07-108">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="68f07-109">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="68f07-109">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68f07-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="68f07-110">Return Value</span></span>  

 <span data-ttu-id="68f07-111">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="68f07-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68f07-112">Требования</span><span class="sxs-lookup"><span data-stu-id="68f07-112">Requirements</span></span>  

 <span data-ttu-id="68f07-113">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="68f07-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f07-114">См. также</span><span class="sxs-lookup"><span data-stu-id="68f07-114">See also</span></span>

- [<span data-ttu-id="68f07-115">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="68f07-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="68f07-116">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="68f07-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="68f07-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="68f07-117">ALink API</span></span>](index.md)
