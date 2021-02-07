---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter4:: GetDebugInfoWithPadding'
title: Метод ISymUnmanagedWriter4::GetDebugInfoWithPadding
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: f5a2026a4ddf12b741b670097e31260e68f33c7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761711"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="04bd9-103">Метод ISymUnmanagedWriter4::GetDebugInfoWithPadding</span><span class="sxs-lookup"><span data-stu-id="04bd9-103">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>

<span data-ttu-id="04bd9-104">Функция аналогична [методу GetDebugInfo](isymunmanagedwriter-getdebuginfo-method.md) , за исключением того, что строка пути дополнена нулями после завершающего нуль-символа, чтобы сделать строку фиксированным размером `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="04bd9-104">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="04bd9-105">Заполнение задается только в том случае, если длина строки пути меньше `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="04bd9-105">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="04bd9-106">Это упрощает написание средств, которые отличаются от PE файлов.</span><span class="sxs-lookup"><span data-stu-id="04bd9-106">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04bd9-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="04bd9-107">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04bd9-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="04bd9-108">Parameters</span></span>  
  
|<span data-ttu-id="04bd9-109">Параметр</span><span class="sxs-lookup"><span data-stu-id="04bd9-109">Parameter</span></span>|<span data-ttu-id="04bd9-110">Описание</span><span class="sxs-lookup"><span data-stu-id="04bd9-110">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="04bd9-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="04bd9-111">Return Value</span></span>  

 <span data-ttu-id="04bd9-112">Возвращает `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="04bd9-112">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04bd9-113">Требования</span><span class="sxs-lookup"><span data-stu-id="04bd9-113">Requirements</span></span>  

 <span data-ttu-id="04bd9-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="04bd9-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04bd9-115">См. также</span><span class="sxs-lookup"><span data-stu-id="04bd9-115">See also</span></span>

- [<span data-ttu-id="04bd9-116">Интерфейс ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="04bd9-116">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
