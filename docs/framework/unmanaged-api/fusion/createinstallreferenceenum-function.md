---
description: Дополнительные сведения о функции CreateInstallReferenceEnum
title: Функция CreateInstallReferenceEnum
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: cc7551707cb46bcf0c475a0095684dbc790836e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761155"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="04958-103">Функция CreateInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="04958-103">CreateInstallReferenceEnum Function</span></span>

<span data-ttu-id="04958-104">Возвращает указатель на экземпляр [IInstallReferenceEnum](iinstallreferenceenum-interface.md) , представляющий список ссылок приложения на указанную сборку.</span><span class="sxs-lookup"><span data-stu-id="04958-104">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04958-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="04958-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="04958-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="04958-106">Parameters</span></span>  

 `ppRefEnum`  
 <span data-ttu-id="04958-107">заполняет Возвращаемый `IInstallReferenceEnum` указатель.</span><span class="sxs-lookup"><span data-stu-id="04958-107">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="04958-108">окне Объект [IAssemblyName](iassemblyname-interface.md) , определяющий сборку, для которой перечисляются ссылки.</span><span class="sxs-lookup"><span data-stu-id="04958-108">[in] The [IAssemblyName](iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="04958-109">окне Флаги, влияющие на поведение перечислителя.</span><span class="sxs-lookup"><span data-stu-id="04958-109">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="04958-110">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="04958-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="04958-111">`pvReserved` должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="04958-111">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04958-112">Требования</span><span class="sxs-lookup"><span data-stu-id="04958-112">Requirements</span></span>  

 <span data-ttu-id="04958-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04958-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04958-114">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="04958-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="04958-115">**Библиотека:** Fusion.dll и Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="04958-115">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="04958-116">Используйте Fusion.dll вместо Mscorwks.dll, чтобы убедиться в правильности целевой версии платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04958-116">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="04958-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04958-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04958-118">См. также</span><span class="sxs-lookup"><span data-stu-id="04958-118">See also</span></span>

- [<span data-ttu-id="04958-119">Интерфейс IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="04958-119">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
- [<span data-ttu-id="04958-120">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="04958-120">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="04958-121">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="04958-121">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
