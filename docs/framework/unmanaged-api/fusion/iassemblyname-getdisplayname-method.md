---
description: 'Дополнительные сведения о методе IAssemblyName:: DisplayName'
title: Метод IAssemblyName::GetDisplayName
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
ms.openlocfilehash: 9b52a901385fa9b3ba7cb6bcd1678d0718f8f695
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760762"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="3f422-103">Метод IAssemblyName::GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="3f422-103">IAssemblyName::GetDisplayName Method</span></span>

<span data-ttu-id="3f422-104">Возвращает удобное для восприятия имя сборки, на которую ссылается этот объект [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3f422-104">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f422-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3f422-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f422-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3f422-106">Parameters</span></span>  

 `szDisplayName`  
 <span data-ttu-id="3f422-107">заполняет Строковый буфер, содержащий имя сборки, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="3f422-107">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="3f422-108">[вход, выход] Размер `szDisplayName` в расширенных символах, включая символ конца null.</span><span class="sxs-lookup"><span data-stu-id="3f422-108">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="3f422-109">окне Побитовое сочетание значений [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) , влияющих на функции `szDisplayName` .</span><span class="sxs-lookup"><span data-stu-id="3f422-109">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f422-110">Требования</span><span class="sxs-lookup"><span data-stu-id="3f422-110">Requirements</span></span>  

 <span data-ttu-id="3f422-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f422-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f422-112">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="3f422-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3f422-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f422-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f422-114">См. также</span><span class="sxs-lookup"><span data-stu-id="3f422-114">See also</span></span>

- [<span data-ttu-id="3f422-115">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="3f422-115">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="3f422-116">Перечисления Fusion</span><span class="sxs-lookup"><span data-stu-id="3f422-116">Fusion Enumerations</span></span>](fusion-enumerations.md)
