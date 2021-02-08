---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyImport:: GetAssemblyRefProps'
title: Метод IMetaDataAssemblyImport::GetAssemblyRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: f7011806920ba37ca84b1a48f12da3a5557fa464
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784136"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="8711e-103">Метод IMetaDataAssemblyImport::GetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="8711e-103">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>

<span data-ttu-id="8711e-104">Возвращает набор свойств для ссылки на сборку с указанной сигнатурой метаданных.</span><span class="sxs-lookup"><span data-stu-id="8711e-104">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8711e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8711e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,
    [out] const void          **ppbPublicKeyOrToken,
    [out] ULONG                *pcbPublicKeyOrToken,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] ASSEMBLYMETADATA     *pMetaData,
    [out] const void           **ppbHashValue,
    [out] ULONG                *pcbHashValue,
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8711e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8711e-106">Parameters</span></span>  

 `mdar`  
 <span data-ttu-id="8711e-107">окне `mdAssemblyRef` Токен метаданных, представляющий ссылку на сборку, для которой необходимо получить свойства.</span><span class="sxs-lookup"><span data-stu-id="8711e-107">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="8711e-108">заполняет Указатель на открытый ключ или маркер метаданных.</span><span class="sxs-lookup"><span data-stu-id="8711e-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="8711e-109">заполняет Число байтов в возвращенном открытом ключе или токене.</span><span class="sxs-lookup"><span data-stu-id="8711e-109">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="8711e-110">заполняет Простое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="8711e-110">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8711e-111">окне Размер (в расширенных символах) для `szName` .</span><span class="sxs-lookup"><span data-stu-id="8711e-111">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8711e-112">заполняет Указатель на число расширенных символов, фактически возвращаемых в `szName` .</span><span class="sxs-lookup"><span data-stu-id="8711e-112">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="8711e-113">заполняет Указатель на структуру ASSEMBLYMETADATA, содержащую метаданные сборки.</span><span class="sxs-lookup"><span data-stu-id="8711e-113">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="8711e-114">заполняет Указатель на хэш-значение.</span><span class="sxs-lookup"><span data-stu-id="8711e-114">[out] A pointer to the hash value.</span></span> <span data-ttu-id="8711e-115">Это хэш с использованием алгоритма SHA-1 `PublicKey` Свойства сборки, на которую указывает ссылка, если не задан флаг арффуллоригинатор перечисления [ассемблиреффлагс](assemblyrefflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="8711e-115">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="8711e-116">заполняет Число расширенных символов в возвращенном хэш-значении.</span><span class="sxs-lookup"><span data-stu-id="8711e-116">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="8711e-117">заполняет Указатель на флаги, описывающие метаданные, примененные к сборке.</span><span class="sxs-lookup"><span data-stu-id="8711e-117">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="8711e-118">Значение Flags является сочетанием одного или нескольких значений [корассемблифлагс](corassemblyflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="8711e-118">The flags value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8711e-119">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8711e-119">Return Value</span></span>  

 <span data-ttu-id="8711e-120">Этот метод возвращает S_OK, если он выполнен. в противном случае возвращается один из кодов ошибок, определенных в файле заголовка Winerror. h.</span><span class="sxs-lookup"><span data-stu-id="8711e-120">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8711e-121">Требования</span><span class="sxs-lookup"><span data-stu-id="8711e-121">Requirements</span></span>  

 <span data-ttu-id="8711e-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8711e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8711e-123">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="8711e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8711e-124">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8711e-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8711e-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8711e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8711e-126">См. также</span><span class="sxs-lookup"><span data-stu-id="8711e-126">See also</span></span>

- [<span data-ttu-id="8711e-127">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="8711e-127">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
