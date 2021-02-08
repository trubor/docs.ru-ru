---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyImport:: GetFileProps'
title: Метод IMetaDataAssemblyImport::GetFileProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: 6814fee7edf5478a1ce2cf2b81d8f16fa62cd3f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784110"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="1e2e9-103">Метод IMetaDataAssemblyImport::GetFileProps</span><span class="sxs-lookup"><span data-stu-id="1e2e9-103">IMetaDataAssemblyImport::GetFileProps Method</span></span>

<span data-ttu-id="1e2e9-104">Возвращает свойства файла с указанной сигнатурой метаданных.</span><span class="sxs-lookup"><span data-stu-id="1e2e9-104">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e2e9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1e2e9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e2e9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1e2e9-106">Parameters</span></span>  

 `mdf`  
 <span data-ttu-id="1e2e9-107">окне `mdFile` Токен метаданных, представляющий файл, для которого необходимо получить свойства.</span><span class="sxs-lookup"><span data-stu-id="1e2e9-107">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="1e2e9-108">заполняет Простое имя файла.</span><span class="sxs-lookup"><span data-stu-id="1e2e9-108">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1e2e9-109">окне Размер (в расширенных символах) для `szName` .</span><span class="sxs-lookup"><span data-stu-id="1e2e9-109">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="1e2e9-110">заполняет Число расширенных символов, фактически возвращаемых в `szName` .</span><span class="sxs-lookup"><span data-stu-id="1e2e9-110">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="1e2e9-111">заполняет Указатель на хэш-значение.</span><span class="sxs-lookup"><span data-stu-id="1e2e9-111">[out] A pointer to the hash value.</span></span> <span data-ttu-id="1e2e9-112">Это хэш-код с использованием алгоритма SHA-1 файла.</span><span class="sxs-lookup"><span data-stu-id="1e2e9-112">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="1e2e9-113">заполняет Число расширенных символов в возвращенном хэш-значении.</span><span class="sxs-lookup"><span data-stu-id="1e2e9-113">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="1e2e9-114">заполняет Указатель на флаги, описывающие метаданные, примененные к файлу.</span><span class="sxs-lookup"><span data-stu-id="1e2e9-114">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="1e2e9-115">Значение Flags является сочетанием одного или нескольких значений [корфилефлагс](corfileflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="1e2e9-115">The flags value is a combination of one or more [CorFileFlags](corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e2e9-116">Требования</span><span class="sxs-lookup"><span data-stu-id="1e2e9-116">Requirements</span></span>  

 <span data-ttu-id="1e2e9-117">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e2e9-117">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e2e9-118">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="1e2e9-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e2e9-119">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1e2e9-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e2e9-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e2e9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e2e9-121">См. также</span><span class="sxs-lookup"><span data-stu-id="1e2e9-121">See also</span></span>

- [<span data-ttu-id="1e2e9-122">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="1e2e9-122">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
