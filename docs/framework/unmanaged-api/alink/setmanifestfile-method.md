---
description: Дополнительные сведения о методе SetManifestFile
title: Метод SetManifestFile
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
ms.openlocfilehash: fe91c7f2b4e6f58a0a740de84e055ead49adb77d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662329"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="1c700-103">Метод SetManifestFile</span><span class="sxs-lookup"><span data-stu-id="1c700-103">SetManifestFile Method</span></span>

<span data-ttu-id="1c700-104">Позволяет указать или сбросить файл манифеста, используемый компоновщиком при создании сборки.</span><span class="sxs-lookup"><span data-stu-id="1c700-104">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c700-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1c700-105">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c700-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1c700-106">Parameters</span></span>  

 `pszFile`  
  
 <span data-ttu-id="1c700-107">Имя файла манифеста, содержимое которого помещается в большой двоичный объект Win32 Resources.</span><span class="sxs-lookup"><span data-stu-id="1c700-107">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c700-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1c700-108">Return Value</span></span>  

 <span data-ttu-id="1c700-109">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="1c700-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c700-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="1c700-110">Remarks</span></span>  

 <span data-ttu-id="1c700-111">Вызовите этот метод, прежде чем запрашивать Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="1c700-111">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="1c700-112">Значение `pszFile` параметра — это имя файла манифеста, содержимое которого считывается и помещается в ресурсы Win32 с идентификатором RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="1c700-112">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="1c700-113">При вызове с помощью параметра NULL все ранее прочитанные манифесты очищаются.</span><span class="sxs-lookup"><span data-stu-id="1c700-113">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="1c700-114">Это позволяет сбросить состояние компоновщика до значения времени инициализации.</span><span class="sxs-lookup"><span data-stu-id="1c700-114">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c700-115">Требования</span><span class="sxs-lookup"><span data-stu-id="1c700-115">Requirements</span></span>  

 <span data-ttu-id="1c700-116">Требуется aLink. h</span><span class="sxs-lookup"><span data-stu-id="1c700-116">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c700-117">См. также</span><span class="sxs-lookup"><span data-stu-id="1c700-117">See also</span></span>

- [<span data-ttu-id="1c700-118">Интерфейс IALink3</span><span class="sxs-lookup"><span data-stu-id="1c700-118">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="1c700-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="1c700-119">ALink API</span></span>](index.md)
- [<span data-ttu-id="1c700-120">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="1c700-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="1c700-121">Al.exe (компоновщик сборок)</span><span class="sxs-lookup"><span data-stu-id="1c700-121">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
