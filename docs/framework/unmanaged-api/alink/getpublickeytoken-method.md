---
description: Дополнительные сведения о методе Жетпубликкэйтокен
title: Метод GetPublicKeyToken
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
ms.openlocfilehash: b864c1dc61c7498ccca6aa04ef29b57a30e1a9ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718425"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="49dcf-103">Метод GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="49dcf-103">GetPublicKeyToken Method</span></span>

<span data-ttu-id="49dcf-104">Извлекает токен открытого ключа для данного ключа или контейнера ключей.</span><span class="sxs-lookup"><span data-stu-id="49dcf-104">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49dcf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="49dcf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="49dcf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="49dcf-106">Parameters</span></span>  

 `pszKeyFile`  
 <span data-ttu-id="49dcf-107">Имя файла ключа.</span><span class="sxs-lookup"><span data-stu-id="49dcf-107">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="49dcf-108">Имя контейнера ключей.</span><span class="sxs-lookup"><span data-stu-id="49dcf-108">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="49dcf-109">Адрес, по которому должен храниться токен ключа.</span><span class="sxs-lookup"><span data-stu-id="49dcf-109">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="49dcf-110">Задает размер буфера (в байтах), указанного в параметре `pvPublicKeyToken` .</span><span class="sxs-lookup"><span data-stu-id="49dcf-110">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="49dcf-111">После возврата содержит фактическое число используемых байтов.</span><span class="sxs-lookup"><span data-stu-id="49dcf-111">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49dcf-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="49dcf-112">Return Value</span></span>  

 <span data-ttu-id="49dcf-113">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="49dcf-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49dcf-114">Требования</span><span class="sxs-lookup"><span data-stu-id="49dcf-114">Requirements</span></span>  

 <span data-ttu-id="49dcf-115">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="49dcf-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49dcf-116">См. также</span><span class="sxs-lookup"><span data-stu-id="49dcf-116">See also</span></span>

- [<span data-ttu-id="49dcf-117">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="49dcf-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="49dcf-118">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="49dcf-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="49dcf-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="49dcf-119">ALink API</span></span>](index.md)
