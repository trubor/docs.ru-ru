---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: OpenNamespace'
title: Метод ISymUnmanagedWriter::OpenNamespace
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
ms.openlocfilehash: ab848e44dfda1f5caaa92bfd3376bdcbd67d8a9b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762127"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="2b47e-103">Метод ISymUnmanagedWriter::OpenNamespace</span><span class="sxs-lookup"><span data-stu-id="2b47e-103">ISymUnmanagedWriter::OpenNamespace Method</span></span>

<span data-ttu-id="2b47e-104">Открывает новое пространство имен.</span><span class="sxs-lookup"><span data-stu-id="2b47e-104">Opens a new namespace.</span></span> <span data-ttu-id="2b47e-105">Вызовите этот метод перед определением методов или переменных, которые занимают пространство имен.</span><span class="sxs-lookup"><span data-stu-id="2b47e-105">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="2b47e-106">Пространства имен могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="2b47e-106">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b47e-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2b47e-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b47e-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="2b47e-108">Parameters</span></span>  

 `name`  
 <span data-ttu-id="2b47e-109">окне Указатель на имя нового пространства имен.</span><span class="sxs-lookup"><span data-stu-id="2b47e-109">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b47e-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2b47e-110">Return Value</span></span>  

 <span data-ttu-id="2b47e-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="2b47e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b47e-112">Требования</span><span class="sxs-lookup"><span data-stu-id="2b47e-112">Requirements</span></span>  

 <span data-ttu-id="2b47e-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="2b47e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b47e-114">См. также</span><span class="sxs-lookup"><span data-stu-id="2b47e-114">See also</span></span>

- [<span data-ttu-id="2b47e-115">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="2b47e-115">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="2b47e-116">Метод CloseNamespace</span><span class="sxs-lookup"><span data-stu-id="2b47e-116">CloseNamespace Method</span></span>](isymunmanagedwriter-closenamespace-method.md)
