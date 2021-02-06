---
description: Дополнительные сведения о методе CloseEnum
title: Метод CloseEnum
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
ms.openlocfilehash: 700c54de5af2e5c0be6940d4045019092655d46f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638383"
---
# <a name="closeenum-method"></a><span data-ttu-id="0c885-103">Метод CloseEnum</span><span class="sxs-lookup"><span data-stu-id="0c885-103">CloseEnum Method</span></span>

<span data-ttu-id="0c885-104">Закрывает указанное перечисление и освобождает связанные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="0c885-104">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c885-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0c885-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c885-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0c885-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="0c885-107">Обрабатываемый обработчик перечисления.</span><span class="sxs-lookup"><span data-stu-id="0c885-107">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c885-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0c885-108">Return Value</span></span>  

 <span data-ttu-id="0c885-109">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="0c885-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c885-110">Требования</span><span class="sxs-lookup"><span data-stu-id="0c885-110">Requirements</span></span>  

 <span data-ttu-id="0c885-111">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="0c885-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c885-112">См. также</span><span class="sxs-lookup"><span data-stu-id="0c885-112">See also</span></span>

- [<span data-ttu-id="0c885-113">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="0c885-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0c885-114">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="0c885-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0c885-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="0c885-115">ALink API</span></span>](index.md)
