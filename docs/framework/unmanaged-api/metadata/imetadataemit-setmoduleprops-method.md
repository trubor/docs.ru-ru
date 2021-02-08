---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Сетмодулепропс'
title: Метод IMetaDataEmit::SetModuleProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: 0fc68a3f40871ddbb70cef885789ae7fe8ae0cba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772031"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="1951b-103">Метод IMetaDataEmit::SetModuleProps</span><span class="sxs-lookup"><span data-stu-id="1951b-103">IMetaDataEmit::SetModuleProps Method</span></span>

<span data-ttu-id="1951b-104">Обновляет ссылки на модуль, определенный в предыдущем вызове [IMetaDataEmit::D ефинемодулереф](imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="1951b-104">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1951b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1951b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1951b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1951b-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="1951b-107">окне Имя модуля в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="1951b-107">[in] The module name in Unicode.</span></span> <span data-ttu-id="1951b-108">Это только имя файла, а не полный путь.</span><span class="sxs-lookup"><span data-stu-id="1951b-108">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1951b-109">Требования</span><span class="sxs-lookup"><span data-stu-id="1951b-109">Requirements</span></span>  

 <span data-ttu-id="1951b-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1951b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1951b-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="1951b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1951b-112">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1951b-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1951b-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1951b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1951b-114">См. также</span><span class="sxs-lookup"><span data-stu-id="1951b-114">See also</span></span>

- [<span data-ttu-id="1951b-115">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="1951b-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="1951b-116">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="1951b-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
