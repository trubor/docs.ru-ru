---
description: 'Дополнительные сведения: метод IMetaDataImport:: Жетпинвокемап'
title: Метод IMetaDataImport::GetPinvokeMap
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
ms.openlocfilehash: fcf45f4741709423aa48dcf895dfc4be276e19fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649446"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="338ee-103">Метод IMetaDataImport::GetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="338ee-103">IMetaDataImport::GetPinvokeMap Method</span></span>

<span data-ttu-id="338ee-104">Возвращает токен ModuleRef, представляющий целевую сборку вызова PInvoke.</span><span class="sxs-lookup"><span data-stu-id="338ee-104">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="338ee-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="338ee-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="338ee-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="338ee-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="338ee-107">окне Токен FieldDef или MethodDef для получения метаданных сопоставления PInvoke для.</span><span class="sxs-lookup"><span data-stu-id="338ee-107">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="338ee-108">заполняет Указатель на флаги, используемые для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="338ee-108">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="338ee-109">Это значение является битовой маской из перечисления [CorPinvokeMap](corpinvokemap-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="338ee-109">This value is a bitmask from the [CorPinvokeMap](corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="338ee-110">заполняет Имя неуправляемой целевой библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="338ee-110">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="338ee-111">окне Размер в расширенных символах `szImportName` .</span><span class="sxs-lookup"><span data-stu-id="338ee-111">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="338ee-112">заполняет Число расширенных символов, возвращаемых в `szImportName` .</span><span class="sxs-lookup"><span data-stu-id="338ee-112">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="338ee-113">заполняет Указатель на токен ModuleRef, представляющий неуправляемую библиотеку целевых объектов.</span><span class="sxs-lookup"><span data-stu-id="338ee-113">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="338ee-114">Требования</span><span class="sxs-lookup"><span data-stu-id="338ee-114">Requirements</span></span>  

 <span data-ttu-id="338ee-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="338ee-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="338ee-116">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="338ee-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="338ee-117">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="338ee-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="338ee-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="338ee-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="338ee-119">См. также</span><span class="sxs-lookup"><span data-stu-id="338ee-119">See also</span></span>

- [<span data-ttu-id="338ee-120">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="338ee-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="338ee-121">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="338ee-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
