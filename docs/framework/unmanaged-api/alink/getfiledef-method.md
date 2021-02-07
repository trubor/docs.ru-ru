---
description: Дополнительные сведения о методе Жетфиледеф
title: Метод GetFileDef
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
ms.openlocfilehash: 5d44336e686ca565f468fb95ce5290ee41d5e16e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718451"
---
# <a name="getfiledef-method"></a><span data-ttu-id="fbf69-103">Метод GetFileDef</span><span class="sxs-lookup"><span data-stu-id="fbf69-103">GetFileDef Method</span></span>

<span data-ttu-id="fbf69-104">Извлекает фактический токен Филедеф, используемый в метаданных (в отличие от маркера, назначенного ALink).</span><span class="sxs-lookup"><span data-stu-id="fbf69-104">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf69-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fbf69-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbf69-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fbf69-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="fbf69-107">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="fbf69-107">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="fbf69-108">Токен добавленного файла, полученный из метода AddFile или метода AddImport.</span><span class="sxs-lookup"><span data-stu-id="fbf69-108">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="fbf69-109">Получает токен Филедеф.</span><span class="sxs-lookup"><span data-stu-id="fbf69-109">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbf69-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fbf69-110">Return Value</span></span>  

 <span data-ttu-id="fbf69-111">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="fbf69-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbf69-112">Требования</span><span class="sxs-lookup"><span data-stu-id="fbf69-112">Requirements</span></span>  

 <span data-ttu-id="fbf69-113">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="fbf69-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf69-114">См. также</span><span class="sxs-lookup"><span data-stu-id="fbf69-114">See also</span></span>

- [<span data-ttu-id="fbf69-115">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="fbf69-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="fbf69-116">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="fbf69-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="fbf69-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="fbf69-117">ALink API</span></span>](index.md)
