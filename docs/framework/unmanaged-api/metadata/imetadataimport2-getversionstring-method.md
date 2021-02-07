---
description: 'Дополнительные сведения о методе: IMetaDataImport2:: GetVersionString'
title: Метод IMetaDataImport2::GetVersionString
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 6f7e296607dc3167936c69d52a8baae4f5555b88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688563"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="299eb-103">Метод IMetaDataImport2::GetVersionString</span><span class="sxs-lookup"><span data-stu-id="299eb-103">IMetaDataImport2::GetVersionString Method</span></span>

<span data-ttu-id="299eb-104">Возвращает номер версии среды выполнения, которая использовалась для построения сборки.</span><span class="sxs-lookup"><span data-stu-id="299eb-104">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="299eb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="299eb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="299eb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="299eb-106">Parameters</span></span>  

 `pwzBuf`  
 <span data-ttu-id="299eb-107">заполняет Массив для хранения строки, указывающей версию.</span><span class="sxs-lookup"><span data-stu-id="299eb-107">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="299eb-108">окне Размер массива в расширенных символах `pwzBuf` .</span><span class="sxs-lookup"><span data-stu-id="299eb-108">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="299eb-109">заполняет Число расширенных символов, включая знак завершения null, возвращаемый в `pwzBuf` массиве.</span><span class="sxs-lookup"><span data-stu-id="299eb-109">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="299eb-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="299eb-110">Remarks</span></span>  

 <span data-ttu-id="299eb-111">`GetVersionString`Метод получает встроенную версию текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="299eb-111">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="299eb-112">Если область не была сохранена, она не будет иметь встроенной версии и будет возвращена пустая строка.</span><span class="sxs-lookup"><span data-stu-id="299eb-112">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="299eb-113">Требования</span><span class="sxs-lookup"><span data-stu-id="299eb-113">Requirements</span></span>  

 <span data-ttu-id="299eb-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="299eb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="299eb-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="299eb-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="299eb-116">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="299eb-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="299eb-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="299eb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="299eb-118">См. также</span><span class="sxs-lookup"><span data-stu-id="299eb-118">See also</span></span>

- [<span data-ttu-id="299eb-119">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="299eb-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="299eb-120">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="299eb-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
