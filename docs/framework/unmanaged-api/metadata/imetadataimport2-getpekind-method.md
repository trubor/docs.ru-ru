---
description: 'Дополнительные сведения о методе: IMetaDataImport2:: GetPEKind'
title: Метод IMetaDataImport2::GetPEKind
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
ms.openlocfilehash: 3cd003f4b1a56f59b9e8c89bf1c4f8f2f8c7fea1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688589"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="c9ba8-103">Метод IMetaDataImport2::GetPEKind</span><span class="sxs-lookup"><span data-stu-id="c9ba8-103">IMetaDataImport2::GetPEKind Method</span></span>

<span data-ttu-id="c9ba8-104">Возвращает значение, определяющее природу кода в переносимом исполняемом (PE) файле (обычно это DLL или EXE-файл), который определен в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="c9ba8-104">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9ba8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c9ba8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9ba8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c9ba8-106">Parameters</span></span>  

 `pdwPEKind`  
 <span data-ttu-id="c9ba8-107">заполняет Указатель на значение перечисления [CorPEKind](corpekind-enumeration.md) , ОПИСЫВАЮЩее PE-файл.</span><span class="sxs-lookup"><span data-stu-id="c9ba8-107">[out] A pointer to a value of the [CorPEKind](corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="c9ba8-108">заполняет Указатель на значение, идентифицирующее архитектуру компьютера.</span><span class="sxs-lookup"><span data-stu-id="c9ba8-108">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="c9ba8-109">Возможные значения см. в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="c9ba8-109">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9ba8-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="c9ba8-110">Remarks</span></span>  

 <span data-ttu-id="c9ba8-111">Значение, на которое ссылается `pdwMachine` параметр, может быть одним из следующих.</span><span class="sxs-lookup"><span data-stu-id="c9ba8-111">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="c9ba8-112">Значение</span><span class="sxs-lookup"><span data-stu-id="c9ba8-112">Value</span></span>|<span data-ttu-id="c9ba8-113">Архитектура компьютера</span><span class="sxs-lookup"><span data-stu-id="c9ba8-113">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="c9ba8-114">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="c9ba8-114">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="c9ba8-115">0x014C</span><span class="sxs-lookup"><span data-stu-id="c9ba8-115">0x014C</span></span>|<span data-ttu-id="c9ba8-116">x86</span><span class="sxs-lookup"><span data-stu-id="c9ba8-116">x86</span></span>|  
|<span data-ttu-id="c9ba8-117">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="c9ba8-117">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="c9ba8-118">0x0200</span><span class="sxs-lookup"><span data-stu-id="c9ba8-118">0x0200</span></span>|<span data-ttu-id="c9ba8-119">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="c9ba8-119">Intel IPF</span></span>|  
|<span data-ttu-id="c9ba8-120">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="c9ba8-120">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="c9ba8-121">0x8664</span><span class="sxs-lookup"><span data-stu-id="c9ba8-121">0x8664</span></span>|<span data-ttu-id="c9ba8-122">X64</span><span class="sxs-lookup"><span data-stu-id="c9ba8-122">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9ba8-123">Требования</span><span class="sxs-lookup"><span data-stu-id="c9ba8-123">Requirements</span></span>  

 <span data-ttu-id="c9ba8-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9ba8-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9ba8-125">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c9ba8-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9ba8-126">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9ba8-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9ba8-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9ba8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ba8-128">См. также</span><span class="sxs-lookup"><span data-stu-id="c9ba8-128">See also</span></span>

- [<span data-ttu-id="c9ba8-129">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c9ba8-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="c9ba8-130">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c9ba8-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c9ba8-131">Перечисление CorPEKind</span><span class="sxs-lookup"><span data-stu-id="c9ba8-131">CorPEKind Enumeration</span></span>](corpekind-enumeration.md)
