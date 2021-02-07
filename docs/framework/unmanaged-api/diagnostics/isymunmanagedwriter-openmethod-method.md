---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: Опенмесод'
title: Метод ISymUnmanagedWriter::OpenMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: 2cf7e6bf7c632449c25a2b49c7658fa7b1cc287e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762231"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="66128-103">Метод ISymUnmanagedWriter::OpenMethod</span><span class="sxs-lookup"><span data-stu-id="66128-103">ISymUnmanagedWriter::OpenMethod Method</span></span>

<span data-ttu-id="66128-104">Открывает метод, в который порождается символьная информация.</span><span class="sxs-lookup"><span data-stu-id="66128-104">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="66128-105">Данный метод преобразуется в текущий метод для вызовов для определения точек следования, параметров и лексических областей.</span><span class="sxs-lookup"><span data-stu-id="66128-105">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="66128-106">Существует неявная лексическая область вокруг всего метода.</span><span class="sxs-lookup"><span data-stu-id="66128-106">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="66128-107">Повторное открытие метода, который ранее был закрыт, стирает все ранее определенные символы для этого метода.</span><span class="sxs-lookup"><span data-stu-id="66128-107">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="66128-108">Одновременно может быть только один метод открытия.</span><span class="sxs-lookup"><span data-stu-id="66128-108">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66128-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="66128-109">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66128-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="66128-110">Parameters</span></span>  

 `method`  
 <span data-ttu-id="66128-111">окне Токен метаданных для открываемого метода.</span><span class="sxs-lookup"><span data-stu-id="66128-111">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66128-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="66128-112">Return Value</span></span>  

 <span data-ttu-id="66128-113">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="66128-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66128-114">Требования</span><span class="sxs-lookup"><span data-stu-id="66128-114">Requirements</span></span>  

 <span data-ttu-id="66128-115">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="66128-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66128-116">См. также</span><span class="sxs-lookup"><span data-stu-id="66128-116">See also</span></span>

- [<span data-ttu-id="66128-117">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="66128-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="66128-118">Метод CloseMethod</span><span class="sxs-lookup"><span data-stu-id="66128-118">CloseMethod Method</span></span>](isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="66128-119">Метод OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="66128-119">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)
