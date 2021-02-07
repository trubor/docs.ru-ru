---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyEmit::D Ефинеассемблиреф'
title: Метод IMetaDataAssemblyEmit::DefineAssemblyRef
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
ms.openlocfilehash: e3c3acce77e6b0cb2943d66f3477898c90ea6251
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706712"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="c6f62-103">Метод IMetaDataAssemblyEmit::DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="c6f62-103">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>

<span data-ttu-id="c6f62-104">Создает структуру `AssemblyRef`, содержащую метаданные для сборки, на которую ссылается данная сборка, и возвращает связанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="c6f62-104">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6f62-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c6f62-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6f62-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c6f62-106">Parameters</span></span>  

 `pbPublicKeyOrToken`  
 <span data-ttu-id="c6f62-107">окне Открытый ключ издателя сборки, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="c6f62-107">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="c6f62-108">Вспомогательную функцию [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) можно использовать, чтобы получить хэш открытого ключа для передачи в качестве этого параметра.</span><span class="sxs-lookup"><span data-stu-id="c6f62-108">The helper function [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="c6f62-109">окне Размер в байтах для `pbPublicKeyOrToken` .</span><span class="sxs-lookup"><span data-stu-id="c6f62-109">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="c6f62-110">окне Понятное для человека текстовое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="c6f62-110">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="c6f62-111">Это значение не должно превышать 1024 символов.</span><span class="sxs-lookup"><span data-stu-id="c6f62-111">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="c6f62-112">окне Экземпляр ASSEMBLYMETADATA, содержащий сведения о версии, платформе и языковой стандарте сборки, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="c6f62-112">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c6f62-113">окне Хэш-данные, связанные с упоминаемой сборкой.</span><span class="sxs-lookup"><span data-stu-id="c6f62-113">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="c6f62-114">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="c6f62-114">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c6f62-115">окне Размер в байтах для `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="c6f62-115">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="c6f62-116">окне Побитовое сочетание значений [корассемблифлагс](corassemblyflags-enumeration.md) , влияющих на поведение подсистемы выполнения.</span><span class="sxs-lookup"><span data-stu-id="c6f62-116">[in] A bitwise combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="c6f62-117">заполняет Указатель на возвращаемый `AssemblyRef` маркер метаданных.</span><span class="sxs-lookup"><span data-stu-id="c6f62-117">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6f62-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="c6f62-118">Remarks</span></span>  

 <span data-ttu-id="c6f62-119">`AssemblyRef`Для каждой сборки, на которую ссылается эта сборка, должна быть определена одна структура метаданных.</span><span class="sxs-lookup"><span data-stu-id="c6f62-119">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="c6f62-120">Во время выполнения сведения о сборке, на которую указывает ссылка, передаются распознавателю сборок с указанием, что они представляют "как встроенные" сведения.</span><span class="sxs-lookup"><span data-stu-id="c6f62-120">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="c6f62-121">Затем сопоставитель сборок применяет политику.</span><span class="sxs-lookup"><span data-stu-id="c6f62-121">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6f62-122">Требования</span><span class="sxs-lookup"><span data-stu-id="c6f62-122">Requirements</span></span>  

 <span data-ttu-id="c6f62-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6f62-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6f62-124">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c6f62-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6f62-125">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6f62-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6f62-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6f62-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6f62-127">См. также</span><span class="sxs-lookup"><span data-stu-id="c6f62-127">See also</span></span>

- [<span data-ttu-id="c6f62-128">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="c6f62-128">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
