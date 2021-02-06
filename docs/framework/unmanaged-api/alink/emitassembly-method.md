---
description: Дополнительные сведения о методе Емитассембли
title: Метод EmitAssembly
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
ms.openlocfilehash: aada17d8df6435c5edfe6beb5db5ee13f887f253
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638344"
---
# <a name="emitassembly-method"></a><span data-ttu-id="00802-103">Метод EmitAssembly</span><span class="sxs-lookup"><span data-stu-id="00802-103">EmitAssembly Method</span></span>

<span data-ttu-id="00802-104">Создает сборку.</span><span class="sxs-lookup"><span data-stu-id="00802-104">Creates the assembly.</span></span> <span data-ttu-id="00802-105">Вызывайте этот метод после закрытия всех остальных файлов, кроме файла сборки.</span><span class="sxs-lookup"><span data-stu-id="00802-105">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="00802-106">Не вызывайте этот метод при создании непривязанных модулей.</span><span class="sxs-lookup"><span data-stu-id="00802-106">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00802-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="00802-107">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="00802-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="00802-108">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="00802-109">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="00802-109">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00802-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="00802-110">Return Value</span></span>  

 <span data-ttu-id="00802-111">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="00802-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00802-112">Требования</span><span class="sxs-lookup"><span data-stu-id="00802-112">Requirements</span></span>  

 <span data-ttu-id="00802-113">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="00802-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00802-114">См. также</span><span class="sxs-lookup"><span data-stu-id="00802-114">See also</span></span>

- [<span data-ttu-id="00802-115">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="00802-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="00802-116">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="00802-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="00802-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="00802-117">ALink API</span></span>](index.md)
