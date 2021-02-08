---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyEmit:: SetFileProps'
title: Метод IMetaDataAssemblyEmit::SetFileProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 482aa11b85eaf05d126c4fcc0d5a1aced85002d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789311"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="fc8cc-103">Метод IMetaDataAssemblyEmit::SetFileProps</span><span class="sxs-lookup"><span data-stu-id="fc8cc-103">IMetaDataAssemblyEmit::SetFileProps Method</span></span>

<span data-ttu-id="fc8cc-104">Изменяет указанную структуру метаданных `File`.</span><span class="sxs-lookup"><span data-stu-id="fc8cc-104">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc8cc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fc8cc-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc8cc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fc8cc-106">Parameters</span></span>  

 `file`  
 <span data-ttu-id="fc8cc-107">окне Токен метаданных, указывающий `File` структуру метаданных, которую необходимо изменить.</span><span class="sxs-lookup"><span data-stu-id="fc8cc-107">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="fc8cc-108">окне Указатель на хэш-данные, связанные с файлом.</span><span class="sxs-lookup"><span data-stu-id="fc8cc-108">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="fc8cc-109">окне Размер в байтах для `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="fc8cc-109">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="fc8cc-110">окне Побитовое сочетание значений [корфилефлагс](corfileflags-enumeration.md) , задающих различные атрибуты файла.</span><span class="sxs-lookup"><span data-stu-id="fc8cc-110">[in] A bitwise combination of [CorFileFlags](corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc8cc-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="fc8cc-111">Remarks</span></span>  

 <span data-ttu-id="fc8cc-112">Чтобы создать `File` структуру метаданных, используйте метод [IMetaDataAssemblyEmit::D ефинефиле](imetadataassemblyemit-definefile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fc8cc-112">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc8cc-113">Требования</span><span class="sxs-lookup"><span data-stu-id="fc8cc-113">Requirements</span></span>  

 <span data-ttu-id="fc8cc-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc8cc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc8cc-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="fc8cc-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc8cc-116">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc8cc-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc8cc-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc8cc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc8cc-118">См. также</span><span class="sxs-lookup"><span data-stu-id="fc8cc-118">See also</span></span>

- [<span data-ttu-id="fc8cc-119">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="fc8cc-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
