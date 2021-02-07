---
description: Дополнительные сведения о методе ImportFileEx2
title: Метод ImportFileEx2
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
ms.openlocfilehash: 0968318ab7e416e56b71f2f30f2745d538d0ff8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718009"
---
# <a name="importfileex2-method"></a><span data-ttu-id="23ef5-103">Метод ImportFileEx2</span><span class="sxs-lookup"><span data-stu-id="23ef5-103">ImportFileEx2 Method</span></span>

<span data-ttu-id="23ef5-104">Импортирует сборки и непривязанные модули.</span><span class="sxs-lookup"><span data-stu-id="23ef5-104">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="23ef5-105">Этот метод похож на [Метод ImportFile](importfile-method.md), но работает даже в том случае, если импортируемый файл не существует на диске.</span><span class="sxs-lookup"><span data-stu-id="23ef5-105">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ef5-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="23ef5-106">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="23ef5-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="23ef5-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="23ef5-108">Имя импортируемого файла.</span><span class="sxs-lookup"><span data-stu-id="23ef5-108">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="23ef5-109">Необязательное имя целевого файла.</span><span class="sxs-lookup"><span data-stu-id="23ef5-109">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="23ef5-110">Необязательный интерфейс интерфейса [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) для области импорта.</span><span class="sxs-lookup"><span data-stu-id="23ef5-110">Optional import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="23ef5-111">Если значение равно TRUE, используется ImportTypes, в противном случае импорт должен выполняться вручную.</span><span class="sxs-lookup"><span data-stu-id="23ef5-111">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="23ef5-112">Флаги, передаваемые в [метод OpenScope](../metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="23ef5-112">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="23ef5-113">Получает уникальный идентификатор сборки или файла.</span><span class="sxs-lookup"><span data-stu-id="23ef5-113">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="23ef5-114">Получает интерфейс [интерфейса IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) для области импорта сборки.</span><span class="sxs-lookup"><span data-stu-id="23ef5-114">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="23ef5-115">Может иметь значение NULL, если файл не является сборкой.</span><span class="sxs-lookup"><span data-stu-id="23ef5-115">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="23ef5-116">Получает число импортированных файлов и (или) областей.</span><span class="sxs-lookup"><span data-stu-id="23ef5-116">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23ef5-117">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="23ef5-117">Return Value</span></span>  

 <span data-ttu-id="23ef5-118">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="23ef5-118">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23ef5-119">Требования</span><span class="sxs-lookup"><span data-stu-id="23ef5-119">Requirements</span></span>  

 <span data-ttu-id="23ef5-120">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="23ef5-120">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ef5-121">См. также</span><span class="sxs-lookup"><span data-stu-id="23ef5-121">See also</span></span>

- [<span data-ttu-id="23ef5-122">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="23ef5-122">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="23ef5-123">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="23ef5-123">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="23ef5-124">API ALink</span><span class="sxs-lookup"><span data-stu-id="23ef5-124">ALink API</span></span>](index.md)
