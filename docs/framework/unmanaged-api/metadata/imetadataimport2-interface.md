---
description: 'Дополнительные сведения о: интерфейс IMetaDataImport2'
title: Интерфейс IMetaDataImport2
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: de1b190ae174c6028e4f116d7f6fc0b9af0aac6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688550"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="f10ca-103">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f10ca-103">IMetaDataImport2 Interface</span></span>

<span data-ttu-id="f10ca-104">Расширяет интерфейс [IMetaDataImport](imetadataimport-interface.md) для обеспечения возможности работы с универсальными типами.</span><span class="sxs-lookup"><span data-stu-id="f10ca-104">Extends the [IMetaDataImport](imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f10ca-105">Методы</span><span class="sxs-lookup"><span data-stu-id="f10ca-105">Methods</span></span>  
  
|<span data-ttu-id="f10ca-106">Метод</span><span class="sxs-lookup"><span data-stu-id="f10ca-106">Method</span></span>|<span data-ttu-id="f10ca-107">Описание</span><span class="sxs-lookup"><span data-stu-id="f10ca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f10ca-108">Метод EnumGenericParamConstraints</span><span class="sxs-lookup"><span data-stu-id="f10ca-108">EnumGenericParamConstraints Method</span></span>](imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="f10ca-109">Возвращает перечислитель для массива ограничений универсальных параметров, связанных с универсальным параметром, представленным указанным токеном.</span><span class="sxs-lookup"><span data-stu-id="f10ca-109">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="f10ca-110">Метод EnumGenericParams</span><span class="sxs-lookup"><span data-stu-id="f10ca-110">EnumGenericParams Method</span></span>](imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="f10ca-111">Возвращает перечислитель для массива маркеров универсальных параметров, связанных с указанным маркером TypeDef или MethodDef.</span><span class="sxs-lookup"><span data-stu-id="f10ca-111">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="f10ca-112">Метод EnumMethodSpecs</span><span class="sxs-lookup"><span data-stu-id="f10ca-112">EnumMethodSpecs Method</span></span>](imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="f10ca-113">Возвращает перечислитель для массива токенов MethodSpec, связанных с указанным токеном MethodDef или MemberRef.</span><span class="sxs-lookup"><span data-stu-id="f10ca-113">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="f10ca-114">Метод GetGenericParamConstraintProps</span><span class="sxs-lookup"><span data-stu-id="f10ca-114">GetGenericParamConstraintProps Method</span></span>](imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="f10ca-115">Возвращает метаданные, связанные с ограничением универсального параметра, представленного указанным маркером ограничения.</span><span class="sxs-lookup"><span data-stu-id="f10ca-115">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="f10ca-116">Метод GetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="f10ca-116">GetGenericParamProps Method</span></span>](imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="f10ca-117">Возвращает метаданные, связанные с универсальным параметром, представленным указанным токеном.</span><span class="sxs-lookup"><span data-stu-id="f10ca-117">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="f10ca-118">Метод GetMethodSpecProps</span><span class="sxs-lookup"><span data-stu-id="f10ca-118">GetMethodSpecProps Method</span></span>](imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="f10ca-119">Возвращает сигнатуру метаданных метода, на который ссылается указанный токен MethodSpec.</span><span class="sxs-lookup"><span data-stu-id="f10ca-119">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="f10ca-120">Метод GetPEKind</span><span class="sxs-lookup"><span data-stu-id="f10ca-120">GetPEKind Method</span></span>](imetadataimport2-getpekind-method.md)|<span data-ttu-id="f10ca-121">Возвращает значение, определяющее природу кода в переносимом исполняемом (PE) файле (обычно это DLL или EXE-файл), определенный в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="f10ca-121">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="f10ca-122">Метод GetVersionString</span><span class="sxs-lookup"><span data-stu-id="f10ca-122">GetVersionString Method</span></span>](imetadataimport2-getversionstring-method.md)|<span data-ttu-id="f10ca-123">Возвращает номер версии среды выполнения, которая использовалась для построения сборки.</span><span class="sxs-lookup"><span data-stu-id="f10ca-123">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f10ca-124">Требования</span><span class="sxs-lookup"><span data-stu-id="f10ca-124">Requirements</span></span>  

 <span data-ttu-id="f10ca-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f10ca-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f10ca-126">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="f10ca-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f10ca-127">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f10ca-127">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f10ca-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f10ca-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f10ca-129">См. также</span><span class="sxs-lookup"><span data-stu-id="f10ca-129">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="f10ca-130">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="f10ca-130">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="f10ca-131">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f10ca-131">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
