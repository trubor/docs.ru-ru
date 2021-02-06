---
description: Дополнительные сведения о методе Емитманифест
title: Метод EmitManifest
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
ms.openlocfilehash: 770631864c030c067feb0b02d2f00c36076aa44c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638279"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="07ac4-103">Метод EmitManifest</span><span class="sxs-lookup"><span data-stu-id="07ac4-103">EmitManifest Method</span></span>

<span data-ttu-id="07ac4-104">Выдает окончательный манифест.</span><span class="sxs-lookup"><span data-stu-id="07ac4-104">Emits the final manifest.</span></span> <span data-ttu-id="07ac4-105">Вызовите этот метод после импорта всех остальных файлов и настройки всех параметров.</span><span class="sxs-lookup"><span data-stu-id="07ac4-105">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="07ac4-106">Не вызывайте этот метод для непривязанных модулей.</span><span class="sxs-lookup"><span data-stu-id="07ac4-106">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07ac4-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="07ac4-107">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="07ac4-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="07ac4-108">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="07ac4-109">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="07ac4-109">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="07ac4-110">Получает размер для резервирования в файле сборки, полученный из [функции StrongNameSignatureSize](../strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="07ac4-110">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="07ac4-111">При необходимости получает маркер манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="07ac4-111">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07ac4-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="07ac4-112">Return Value</span></span>  

 <span data-ttu-id="07ac4-113">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="07ac4-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07ac4-114">Требования</span><span class="sxs-lookup"><span data-stu-id="07ac4-114">Requirements</span></span>  

 <span data-ttu-id="07ac4-115">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="07ac4-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07ac4-116">См. также</span><span class="sxs-lookup"><span data-stu-id="07ac4-116">See also</span></span>

- [<span data-ttu-id="07ac4-117">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="07ac4-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="07ac4-118">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="07ac4-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="07ac4-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="07ac4-119">ALink API</span></span>](index.md)
