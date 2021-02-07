---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyEmit::D Ефинефиле'
title: Метод IMetaDataAssemblyEmit::DefineFile
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: 825ef44c2b0a5f312b4c5f9c851d62e75709c7ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671056"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="e20a3-103">Метод IMetaDataAssemblyEmit::DefineFile</span><span class="sxs-lookup"><span data-stu-id="e20a3-103">IMetaDataAssemblyEmit::DefineFile Method</span></span>

<span data-ttu-id="e20a3-104">Создает структуру метаданных `File`, содержащую метаданные для сборки, на которую ссылается данная сборка, и возвращает связанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="e20a3-104">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e20a3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e20a3-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e20a3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e20a3-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="e20a3-107">окне Имя файла, который будет использоваться.</span><span class="sxs-lookup"><span data-stu-id="e20a3-107">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="e20a3-108">окне Указатель на хэш-данные, связанные со сборкой.</span><span class="sxs-lookup"><span data-stu-id="e20a3-108">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="e20a3-109">окне Размер в байтах для `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="e20a3-109">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="e20a3-110">окне Побитовое сочетание `FileFlags` значений, задающих настройки свойств.</span><span class="sxs-lookup"><span data-stu-id="e20a3-110">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="e20a3-111">заполняет Указатель на возвращаемый `File` токен.</span><span class="sxs-lookup"><span data-stu-id="e20a3-111">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e20a3-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="e20a3-112">Remarks</span></span>  

 <span data-ttu-id="e20a3-113">Одна `File` структура метаданных должна быть определена для каждого файла, который был частью этой сборки на момент построения этой сборки, за исключением файла, содержащего метаданные.</span><span class="sxs-lookup"><span data-stu-id="e20a3-113">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e20a3-114">Требования</span><span class="sxs-lookup"><span data-stu-id="e20a3-114">Requirements</span></span>  

 <span data-ttu-id="e20a3-115">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e20a3-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e20a3-116">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="e20a3-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e20a3-117">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e20a3-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e20a3-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e20a3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e20a3-119">См. также</span><span class="sxs-lookup"><span data-stu-id="e20a3-119">See also</span></span>

- [<span data-ttu-id="e20a3-120">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="e20a3-120">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
