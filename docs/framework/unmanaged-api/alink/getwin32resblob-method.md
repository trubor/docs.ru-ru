---
description: Дополнительные сведения о методе GetWin32ResBlob
title: Метод GetWin32ResBlob
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
ms.openlocfilehash: e1140b14bfba56dfac03c443a537d6d2188575b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718269"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="281ab-103">Метод GetWin32ResBlob</span><span class="sxs-lookup"><span data-stu-id="281ab-103">GetWin32ResBlob Method</span></span>

<span data-ttu-id="281ab-104">Извлекает BLOB-объект ресурса Win32.</span><span class="sxs-lookup"><span data-stu-id="281ab-104">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="281ab-105">Вызовите этот метод после установки параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="281ab-105">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="281ab-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="281ab-106">Syntax</span></span>  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="281ab-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="281ab-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="281ab-108">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="281ab-108">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="281ab-109">Токен файла, используемый для получения имени файла, используемого при создании ресурса версии Win32</span><span class="sxs-lookup"><span data-stu-id="281ab-109">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="281ab-110">Значение TRUE, если файл является библиотекой DLL, и false для EXE-файла.</span><span class="sxs-lookup"><span data-stu-id="281ab-110">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="281ab-111">Необязательный значок для вставки в большой двоичный объект ресурса.</span><span class="sxs-lookup"><span data-stu-id="281ab-111">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="281ab-112">Получает большой двоичный объект ресурса.</span><span class="sxs-lookup"><span data-stu-id="281ab-112">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="281ab-113">Получает размер большого двоичного объекта.</span><span class="sxs-lookup"><span data-stu-id="281ab-113">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="281ab-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="281ab-114">Return Value</span></span>  

 <span data-ttu-id="281ab-115">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="281ab-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="281ab-116">Требования</span><span class="sxs-lookup"><span data-stu-id="281ab-116">Requirements</span></span>  

 <span data-ttu-id="281ab-117">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="281ab-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="281ab-118">См. также</span><span class="sxs-lookup"><span data-stu-id="281ab-118">See also</span></span>

- [<span data-ttu-id="281ab-119">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="281ab-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="281ab-120">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="281ab-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="281ab-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="281ab-121">ALink API</span></span>](index.md)
