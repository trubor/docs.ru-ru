---
description: Дополнительные сведения о методе FreeWin32ResBlob
title: Метод FreeWin32ResBlob
ms.date: 03/30/2017
api_name:
- IALink.FreeWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- FreeWin32ResBlob
helpviewer_keywords:
- FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type:
- apiref
ms.openlocfilehash: 56c83632b623eec76e8e2d24030c79a8262f506f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637947"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="b46b5-103">Метод FreeWin32ResBlob</span><span class="sxs-lookup"><span data-stu-id="b46b5-103">FreeWin32ResBlob Method</span></span>

<span data-ttu-id="b46b5-104">Освобождает большой двоичный объект ресурсов Win32 и связанные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="b46b5-104">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b46b5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b46b5-105">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b46b5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b46b5-106">Parameters</span></span>  

 `ppResBlob`  
 <span data-ttu-id="b46b5-107">Большой двоичный объект ресурса, который необходимо освободить.</span><span class="sxs-lookup"><span data-stu-id="b46b5-107">The resource blob to be released.</span></span> <span data-ttu-id="b46b5-108">Этот метод присваивает указатель большого двоичного объекта значению NULL.</span><span class="sxs-lookup"><span data-stu-id="b46b5-108">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b46b5-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b46b5-109">Return Value</span></span>  

 <span data-ttu-id="b46b5-110">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="b46b5-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b46b5-111">Требования</span><span class="sxs-lookup"><span data-stu-id="b46b5-111">Requirements</span></span>  

 <span data-ttu-id="b46b5-112">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="b46b5-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b46b5-113">См. также</span><span class="sxs-lookup"><span data-stu-id="b46b5-113">See also</span></span>

- [<span data-ttu-id="b46b5-114">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="b46b5-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b46b5-115">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="b46b5-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b46b5-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="b46b5-116">ALink API</span></span>](index.md)
