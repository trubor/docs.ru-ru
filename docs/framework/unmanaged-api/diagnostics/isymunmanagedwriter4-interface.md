---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedWriter4'
title: Интерфейс ISymUnmanagedWriter4
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: 3814d7e2728f28d224a4e9a6d99f699f220e8a4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761685"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="3ed40-103">Интерфейс ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="3ed40-103">ISymUnmanagedWriter4 Interface</span></span>

<span data-ttu-id="3ed40-104">Интерфейс ISymUnmanagedWriter4.</span><span class="sxs-lookup"><span data-stu-id="3ed40-104">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ed40-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3ed40-105">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="3ed40-106">Методы</span><span class="sxs-lookup"><span data-stu-id="3ed40-106">Methods</span></span>  

 <span data-ttu-id="3ed40-107">Этот интерфейс содержит следующие методы:</span><span class="sxs-lookup"><span data-stu-id="3ed40-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="3ed40-108">Метод</span><span class="sxs-lookup"><span data-stu-id="3ed40-108">Method</span></span>|<span data-ttu-id="3ed40-109">Описание</span><span class="sxs-lookup"><span data-stu-id="3ed40-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ed40-110">Метод GetDebugInfoWithPadding</span><span class="sxs-lookup"><span data-stu-id="3ed40-110">GetDebugInfoWithPadding Method</span></span>](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="3ed40-111">Функция аналогична [методу GetDebugInfo](isymunmanagedwriter-getdebuginfo-method.md) , за исключением того, что строка пути дополнена нулями после завершающего нуль-символа, чтобы сделать строку фиксированным размером `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="3ed40-111">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="3ed40-112">Заполнение задается только в том случае, если длина строки пути меньше `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="3ed40-112">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="3ed40-113">Это упрощает написание средств, которые отличаются от PE файлов.</span><span class="sxs-lookup"><span data-stu-id="3ed40-113">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ed40-114">Требования</span><span class="sxs-lookup"><span data-stu-id="3ed40-114">Requirements</span></span>  

 <span data-ttu-id="3ed40-115">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="3ed40-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed40-116">См. также</span><span class="sxs-lookup"><span data-stu-id="3ed40-116">See also</span></span>

- [<span data-ttu-id="3ed40-117">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="3ed40-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="3ed40-118">Интерфейс ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="3ed40-118">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
