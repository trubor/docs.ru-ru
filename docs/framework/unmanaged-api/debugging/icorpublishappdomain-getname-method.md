---
description: 'Дополнительные сведения о методе: ICorPublishAppDomain:: Name'
title: Метод ICorPublishAppDomain::GetName
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
ms.openlocfilehash: 05b1b14f7e0db371b29059ec3d44333ac40428e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721805"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="5fcbc-103">Метод ICorPublishAppDomain::GetName</span><span class="sxs-lookup"><span data-stu-id="5fcbc-103">ICorPublishAppDomain::GetName Method</span></span>

<span data-ttu-id="5fcbc-104">Возвращает имя домена приложения, представленного этим [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5fcbc-104">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fcbc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5fcbc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fcbc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5fcbc-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="5fcbc-107">[in] Размер массива `szName`.</span><span class="sxs-lookup"><span data-stu-id="5fcbc-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5fcbc-108">заполняет Указатель на число расширенных символов, включая символ null, возвращаемый в `szName` массиве.</span><span class="sxs-lookup"><span data-stu-id="5fcbc-108">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="5fcbc-109">заполняет Массив, в котором сохраняется имя.</span><span class="sxs-lookup"><span data-stu-id="5fcbc-109">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fcbc-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="5fcbc-110">Remarks</span></span>  

 <span data-ttu-id="5fcbc-111">Если `szName` параметр имеет значение, отличное от NULL, `GetName` метод копирует до `cchName` символов (включая знак завершения null) в `szName` .</span><span class="sxs-lookup"><span data-stu-id="5fcbc-111">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="5fcbc-112">Если в возвращается значение, отличное от NULL `pcchName` , то фактическое число символов в имени (включая знак завершения null) сохраняется в `szName` массиве.</span><span class="sxs-lookup"><span data-stu-id="5fcbc-112">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="5fcbc-113">`GetName`Метод возвращает S_OK HRESULT, независимо от количества скопированных символов.</span><span class="sxs-lookup"><span data-stu-id="5fcbc-113">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fcbc-114">Требования</span><span class="sxs-lookup"><span data-stu-id="5fcbc-114">Requirements</span></span>  

 <span data-ttu-id="5fcbc-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fcbc-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fcbc-116">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="5fcbc-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5fcbc-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fcbc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fcbc-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fcbc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fcbc-119">См. также</span><span class="sxs-lookup"><span data-stu-id="5fcbc-119">See also</span></span>

- [<span data-ttu-id="5fcbc-120">Интерфейс ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="5fcbc-120">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
