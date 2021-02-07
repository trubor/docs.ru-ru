---
description: Дополнительные сведения о методе Жетресолутионскопе
title: Метод GetResolutionScope
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
ms.openlocfilehash: add8ccb1ef6eb0f4b688dcf80563e9280099120d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718399"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="5a783-103">Метод GetResolutionScope</span><span class="sxs-lookup"><span data-stu-id="5a783-103">GetResolutionScope Method</span></span>

<span data-ttu-id="5a783-104">Извлекает область заданного типа.</span><span class="sxs-lookup"><span data-stu-id="5a783-104">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a783-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5a783-105">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a783-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5a783-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="5a783-107">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="5a783-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="5a783-108">Файл, который необходим для ссылки.</span><span class="sxs-lookup"><span data-stu-id="5a783-108">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="5a783-109">Маркер файла, определяемый типом в, который обычно извлекается с помощью [метода ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="5a783-109">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="5a783-110">Получает ссылку на сборку или модуль.</span><span class="sxs-lookup"><span data-stu-id="5a783-110">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a783-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5a783-111">Return Value</span></span>  

 <span data-ttu-id="5a783-112">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="5a783-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a783-113">Требования</span><span class="sxs-lookup"><span data-stu-id="5a783-113">Requirements</span></span>  

 <span data-ttu-id="5a783-114">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="5a783-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a783-115">См. также</span><span class="sxs-lookup"><span data-stu-id="5a783-115">See also</span></span>

- [<span data-ttu-id="5a783-116">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="5a783-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5a783-117">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="5a783-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5a783-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="5a783-118">ALink API</span></span>](index.md)
