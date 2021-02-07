---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedWriter5'
title: Интерфейс ISymUnmanagedWriter5
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 0902385576e1eed17cea672b04858c7e3ef7add8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761633"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="3eb8c-103">Интерфейс ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="3eb8c-103">ISymUnmanagedWriter5 Interface</span></span>

<span data-ttu-id="3eb8c-104">Интерфейс ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="3eb8c-104">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eb8c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3eb8c-105">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="3eb8c-106">Методы</span><span class="sxs-lookup"><span data-stu-id="3eb8c-106">Methods</span></span>  

 <span data-ttu-id="3eb8c-107">Этот интерфейс содержит следующие методы:</span><span class="sxs-lookup"><span data-stu-id="3eb8c-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="3eb8c-108">Метод</span><span class="sxs-lookup"><span data-stu-id="3eb8c-108">Method</span></span>|<span data-ttu-id="3eb8c-109">Описание</span><span class="sxs-lookup"><span data-stu-id="3eb8c-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3eb8c-110">Метод CloseMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="3eb8c-110">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="3eb8c-111">Закройте Специальный раздел настраиваемых данных, чтобы получить сведения о сопоставлении диапазона "токен-источник".</span><span class="sxs-lookup"><span data-stu-id="3eb8c-111">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="3eb8c-112">После закрытия не удается добавить дополнительные сведения о сопоставлении.</span><span class="sxs-lookup"><span data-stu-id="3eb8c-112">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="3eb8c-113">Метод MapTokenToSourceSpan</span><span class="sxs-lookup"><span data-stu-id="3eb8c-113">MapTokenToSourceSpan Method</span></span>](isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="3eb8c-114">Сопоставляет заданный токен метаданных с заданным диапазоном исходной строки в указанном исходном файле.</span><span class="sxs-lookup"><span data-stu-id="3eb8c-114">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="3eb8c-115">Должен вызываться между вызовами [метода OpenMapTokensToSourceSpans](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) и [метода CloseMapTokensToSourceSpans](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="3eb8c-115">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="3eb8c-116">Метод OpenMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="3eb8c-116">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="3eb8c-117">Откройте Специальный раздел настраиваемых данных, чтобы выдать сведения о сопоставлении диапазона от токена к источнику в.</span><span class="sxs-lookup"><span data-stu-id="3eb8c-117">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="3eb8c-118">Открытие этого раздела, если метод уже открыт или наоборот, является ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3eb8c-118">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3eb8c-119">Требования</span><span class="sxs-lookup"><span data-stu-id="3eb8c-119">Requirements</span></span>  

 <span data-ttu-id="3eb8c-120">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="3eb8c-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb8c-121">См. также</span><span class="sxs-lookup"><span data-stu-id="3eb8c-121">See also</span></span>

- [<span data-ttu-id="3eb8c-122">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="3eb8c-122">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="3eb8c-123">Интерфейс ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="3eb8c-123">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
