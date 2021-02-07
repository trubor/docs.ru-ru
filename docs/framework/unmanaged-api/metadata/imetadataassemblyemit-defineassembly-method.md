---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyEmit::D Ефинеассембли'
title: Метод IMetaDataAssemblyEmit::DefineAssembly
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: cd53a4398f49ca96072fc5f5b6dcac35a94bdc59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706764"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="7f766-103">Метод IMetaDataAssemblyEmit::DefineAssembly</span><span class="sxs-lookup"><span data-stu-id="7f766-103">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>

<span data-ttu-id="7f766-104">Создает `Assembly` структуру, содержащую метаданные для указанной сборки, и возвращает связанный маркер метаданных.</span><span class="sxs-lookup"><span data-stu-id="7f766-104">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f766-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7f766-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f766-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7f766-106">Parameters</span></span>  

 `pbPublicKey`  
 <span data-ttu-id="7f766-107">окне Открытый ключ, определяющий издателя сборки, или значение NULL, если сборка не имеет строгого имени.</span><span class="sxs-lookup"><span data-stu-id="7f766-107">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="7f766-108">окне Размер в байтах для `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="7f766-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="7f766-109">окне Идентификатор алгоритма хэширования, используемого для шифрования файлов в сборке, или значение NULL для указания алгоритма SHA-1.</span><span class="sxs-lookup"><span data-stu-id="7f766-109">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="7f766-110">окне Понятное для человека текстовое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="7f766-110">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="7f766-111">Это значение не должно превышать 1024 символов.</span><span class="sxs-lookup"><span data-stu-id="7f766-111">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="7f766-112">окне Указатель на экземпляр ASSEMBLYMETADATA, содержащий сведения о версии, платформе и локали для сборки.</span><span class="sxs-lookup"><span data-stu-id="7f766-112">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="7f766-113">окне Сочетание значений [корассемблифлагс](corassemblyflags-enumeration.md) , описывающих функции сборки.</span><span class="sxs-lookup"><span data-stu-id="7f766-113">[in] A combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="7f766-114">заполняет Указатель на маркер метаданных.</span><span class="sxs-lookup"><span data-stu-id="7f766-114">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f766-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="7f766-115">Remarks</span></span>  

 <span data-ttu-id="7f766-116">`Assembly`В манифесте может быть определена только одна структура метаданных.</span><span class="sxs-lookup"><span data-stu-id="7f766-116">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f766-117">Требования</span><span class="sxs-lookup"><span data-stu-id="7f766-117">Requirements</span></span>  

 <span data-ttu-id="7f766-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f766-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f766-119">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="7f766-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f766-120">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f766-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f766-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f766-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f766-122">См. также</span><span class="sxs-lookup"><span data-stu-id="7f766-122">See also</span></span>

- [<span data-ttu-id="7f766-123">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="7f766-123">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
