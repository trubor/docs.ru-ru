---
description: Дополнительные сведения о методе GetAssemblyRefHash
title: Метод GetAssemblyRefHash
ms.date: 03/30/2017
api_name:
- IALink.GetAssemblyRefHash
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetAssemblyRefHash
helpviewer_keywords:
- GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type:
- apiref
ms.openlocfilehash: d8222d2fdd2c05ca1a23f881989dc344ba294bc1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718477"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="1f775-103">Метод GetAssemblyRefHash</span><span class="sxs-lookup"><span data-stu-id="1f775-103">GetAssemblyRefHash Method</span></span>

<span data-ttu-id="1f775-104">Извлекает хэш-объект хэша для данной сборки.</span><span class="sxs-lookup"><span data-stu-id="1f775-104">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f775-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1f775-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f775-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1f775-106">Parameters</span></span>  

 `FileToken`  
 <span data-ttu-id="1f775-107">Идентификатор сборки, на которую будет ссылаться хэш.</span><span class="sxs-lookup"><span data-stu-id="1f775-107">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="1f775-108">Получает результирующий большой двоичный объект хэша.</span><span class="sxs-lookup"><span data-stu-id="1f775-108">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="1f775-109">Получает размер хэш-объекта хэша (в байтах).</span><span class="sxs-lookup"><span data-stu-id="1f775-109">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f775-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1f775-110">Return Value</span></span>  

 <span data-ttu-id="1f775-111">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="1f775-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f775-112">Требования</span><span class="sxs-lookup"><span data-stu-id="1f775-112">Requirements</span></span>  

 <span data-ttu-id="1f775-113">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="1f775-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f775-114">См. также</span><span class="sxs-lookup"><span data-stu-id="1f775-114">See also</span></span>

- [<span data-ttu-id="1f775-115">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="1f775-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="1f775-116">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="1f775-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="1f775-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="1f775-117">ALink API</span></span>](index.md)
