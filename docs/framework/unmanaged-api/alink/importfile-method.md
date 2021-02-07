---
description: Дополнительные сведения о методе ImportFile
title: Метод ImportFile
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
ms.openlocfilehash: 82c9c7de7cd739ee205dc3695ea651643d01ea3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718165"
---
# <a name="importfile-method"></a><span data-ttu-id="66317-103">Метод ImportFile</span><span class="sxs-lookup"><span data-stu-id="66317-103">ImportFile Method</span></span>

<span data-ttu-id="66317-104">Импортирует сборки и непривязанные модули.</span><span class="sxs-lookup"><span data-stu-id="66317-104">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66317-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="66317-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="66317-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="66317-106">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="66317-107">Полное имя импортируемого файла.</span><span class="sxs-lookup"><span data-stu-id="66317-107">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="66317-108">Необязательное имя выходного файла, которое можно использовать для переименования файла, так как он связан с сборкой.</span><span class="sxs-lookup"><span data-stu-id="66317-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="66317-109">Если значение равно TRUE, используется ImportTypes, в противном случае импорт должен выполняться вручную.</span><span class="sxs-lookup"><span data-stu-id="66317-109">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="66317-110">Указатель на маркер, где будет храниться уникальный идентификатор файла.</span><span class="sxs-lookup"><span data-stu-id="66317-110">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="66317-111">Файл может быть сборкой или файлом.</span><span class="sxs-lookup"><span data-stu-id="66317-111">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="66317-112">Получает указатель на [интерфейс IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="66317-112">Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="66317-113">Может иметь значение NULL, если файл не является сборкой.</span><span class="sxs-lookup"><span data-stu-id="66317-113">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="66317-114">Указатель на число импортированных файлов и (или) областей.</span><span class="sxs-lookup"><span data-stu-id="66317-114">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66317-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="66317-115">Return Value</span></span>  

 <span data-ttu-id="66317-116">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="66317-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66317-117">Требования</span><span class="sxs-lookup"><span data-stu-id="66317-117">Requirements</span></span>  

 <span data-ttu-id="66317-118">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="66317-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66317-119">См. также</span><span class="sxs-lookup"><span data-stu-id="66317-119">See also</span></span>

- [<span data-ttu-id="66317-120">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="66317-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="66317-121">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="66317-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="66317-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="66317-122">ALink API</span></span>](index.md)
