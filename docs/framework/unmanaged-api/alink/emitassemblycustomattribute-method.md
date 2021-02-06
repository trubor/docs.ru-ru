---
description: Дополнительные сведения о методе Емитассембликустоматтрибуте
title: Метод EmitAssemblyCustomAttribute
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
ms.openlocfilehash: c91eb563c14b442a22db8f328287c10e5cc9a63c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638331"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="904bb-103">Метод EmitAssemblyCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="904bb-103">EmitAssemblyCustomAttribute Method</span></span>

<span data-ttu-id="904bb-104">Вызовите метод, чтобы установить настраиваемые атрибуты уровня сборки.</span><span class="sxs-lookup"><span data-stu-id="904bb-104">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="904bb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="904bb-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="904bb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="904bb-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="904bb-107">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="904bb-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="904bb-108">Файл, который разфайлет атрибут.</span><span class="sxs-lookup"><span data-stu-id="904bb-108">File that defiles the attribute.</span></span> <span data-ttu-id="904bb-109">Может иметь значение NULL `AssemblyID` , если не указывает на непривязанный netmodule.</span><span class="sxs-lookup"><span data-stu-id="904bb-109">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="904bb-110">Тип настраиваемого атрибута.</span><span class="sxs-lookup"><span data-stu-id="904bb-110">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="904bb-111">Пользовательские данные значения.</span><span class="sxs-lookup"><span data-stu-id="904bb-111">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="904bb-112">Длина данных пользовательского значения.</span><span class="sxs-lookup"><span data-stu-id="904bb-112">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="904bb-113">Значение TRUE, если настраиваемый атрибут связан с подписыванием сборки.</span><span class="sxs-lookup"><span data-stu-id="904bb-113">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="904bb-114">Значение TRUE, если требуется выдавать несколько атрибутов.</span><span class="sxs-lookup"><span data-stu-id="904bb-114">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="904bb-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="904bb-115">Return Value</span></span>  

 <span data-ttu-id="904bb-116">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="904bb-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="904bb-117">Требования</span><span class="sxs-lookup"><span data-stu-id="904bb-117">Requirements</span></span>  

 <span data-ttu-id="904bb-118">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="904bb-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="904bb-119">См. также</span><span class="sxs-lookup"><span data-stu-id="904bb-119">See also</span></span>

- [<span data-ttu-id="904bb-120">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="904bb-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="904bb-121">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="904bb-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="904bb-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="904bb-122">ALink API</span></span>](index.md)
