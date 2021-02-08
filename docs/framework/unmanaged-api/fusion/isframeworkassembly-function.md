---
description: Дополнительные сведения о функции Исфрамеворкассембли
title: Функция IsFrameworkAssembly
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
ms.openlocfilehash: 8f264df7b1ae5c494298b11ebd94cc93aed5543a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800023"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="4af9c-103">Функция IsFrameworkAssembly</span><span class="sxs-lookup"><span data-stu-id="4af9c-103">IsFrameworkAssembly Function</span></span>

<span data-ttu-id="4af9c-104">Возвращает значение, указывающее, является ли указанная сборка управляемой.</span><span class="sxs-lookup"><span data-stu-id="4af9c-104">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af9c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4af9c-105">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4af9c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4af9c-106">Parameters</span></span>  

 `pwzAssemblyReference`  
 <span data-ttu-id="4af9c-107">окне Имя проверяемой сборки.</span><span class="sxs-lookup"><span data-stu-id="4af9c-107">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="4af9c-108">заполняет Логическое значение, указывающее, является ли сборка управляемой.</span><span class="sxs-lookup"><span data-stu-id="4af9c-108">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="4af9c-109">окне Неканоническая строка, содержащая уникальный идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="4af9c-109">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="4af9c-110">[входной] Размер `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="4af9c-110">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4af9c-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="4af9c-111">Remarks</span></span>  

 <span data-ttu-id="4af9c-112">`pwzAssemblyReference`Параметр является указателем на символьную строку, содержащую имя сборки.</span><span class="sxs-lookup"><span data-stu-id="4af9c-112">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="4af9c-113">Если эта сборка является частью платформа .NET Framework, `pbIsFrameworkAssembly` параметр будет содержать логическое значение `true` .</span><span class="sxs-lookup"><span data-stu-id="4af9c-113">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="4af9c-114">Если именованная сборка не является частью платформа .NET Framework или если `pwzAssemblyReference` параметр не имеет имени сборки, `pbIsFrameworkAssembly` то будет содержать логическое значение `false` .</span><span class="sxs-lookup"><span data-stu-id="4af9c-114">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4af9c-115">Требования</span><span class="sxs-lookup"><span data-stu-id="4af9c-115">Requirements</span></span>  

 <span data-ttu-id="4af9c-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4af9c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af9c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="4af9c-117">See also</span></span>

- [<span data-ttu-id="4af9c-118">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="4af9c-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
