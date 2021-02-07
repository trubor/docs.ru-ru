---
description: Дополнительные сведения о методе ImportFile2
title: Метод ImportFile2
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
ms.openlocfilehash: 98da8ecf4bfc19e52c5a92e6509f6af49afbdd5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718061"
---
# <a name="importfile2-method"></a><span data-ttu-id="0f9f5-103">Метод ImportFile2</span><span class="sxs-lookup"><span data-stu-id="0f9f5-103">ImportFile2 Method</span></span>

<span data-ttu-id="0f9f5-104">Импортирует сборки и непривязанные модули.</span><span class="sxs-lookup"><span data-stu-id="0f9f5-104">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="0f9f5-105">Этот метод похож на [Метод ImportFile](importfile-method.md), но работает даже в том случае, если импортируемый файл не существует на диске.</span><span class="sxs-lookup"><span data-stu-id="0f9f5-105">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f9f5-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0f9f5-106">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f9f5-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="0f9f5-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="0f9f5-108">Имя импортируемого файла.</span><span class="sxs-lookup"><span data-stu-id="0f9f5-108">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="0f9f5-109">Необязательное имя выходного файла, которое можно использовать для переименования файла, так как он связан с сборкой.</span><span class="sxs-lookup"><span data-stu-id="0f9f5-109">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="0f9f5-110">Необязательный интерфейс интерфейса [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) с областью действия.</span><span class="sxs-lookup"><span data-stu-id="0f9f5-110">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="0f9f5-111">Если значение равно TRUE, используется ImportTypes, в противном случае импорт должен выполняться вручную.</span><span class="sxs-lookup"><span data-stu-id="0f9f5-111">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="0f9f5-112">Получает идентификатор для файла или сборки.</span><span class="sxs-lookup"><span data-stu-id="0f9f5-112">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="0f9f5-113">Получает интерфейс [интерфейса IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0f9f5-113">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="0f9f5-114">Значение NULL, если файл не является сборкой.</span><span class="sxs-lookup"><span data-stu-id="0f9f5-114">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="0f9f5-115">Получает найденные файлы и/или импортированные области.</span><span class="sxs-lookup"><span data-stu-id="0f9f5-115">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f9f5-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0f9f5-116">Return Value</span></span>  

 <span data-ttu-id="0f9f5-117">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="0f9f5-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f9f5-118">Требования</span><span class="sxs-lookup"><span data-stu-id="0f9f5-118">Requirements</span></span>  

 <span data-ttu-id="0f9f5-119">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="0f9f5-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f9f5-120">См. также</span><span class="sxs-lookup"><span data-stu-id="0f9f5-120">See also</span></span>

- [<span data-ttu-id="0f9f5-121">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="0f9f5-121">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0f9f5-122">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="0f9f5-122">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0f9f5-123">API ALink</span><span class="sxs-lookup"><span data-stu-id="0f9f5-123">ALink API</span></span>](index.md)
