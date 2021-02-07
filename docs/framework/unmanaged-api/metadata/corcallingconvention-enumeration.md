---
description: Дополнительные сведения о перечислении Коркаллингконвентион
title: Перечисление CorCallingConvention
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
ms.openlocfilehash: 2e823fe3566ef7a54f759cd5debbbd7d5dcf3ceb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678449"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="65814-103">Перечисление CorCallingConvention</span><span class="sxs-lookup"><span data-stu-id="65814-103">CorCallingConvention Enumeration</span></span>

<span data-ttu-id="65814-104">Содержит значения, описывающие типы соглашений о вызовах, выполняемых в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="65814-104">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65814-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="65814-105">Syntax</span></span>  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="65814-106">Члены</span><span class="sxs-lookup"><span data-stu-id="65814-106">Members</span></span>  
  
|<span data-ttu-id="65814-107">Член</span><span class="sxs-lookup"><span data-stu-id="65814-107">Member</span></span>|<span data-ttu-id="65814-108">Описание</span><span class="sxs-lookup"><span data-stu-id="65814-108">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="65814-109">Указывает соглашение о вызовах по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="65814-109">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="65814-110">Указывает, что метод принимает переменное число параметров.</span><span class="sxs-lookup"><span data-stu-id="65814-110">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="65814-111">Указывает, что вызов относится к полю.</span><span class="sxs-lookup"><span data-stu-id="65814-111">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="65814-112">Указывает, что вызов осуществляется в локальный метод.</span><span class="sxs-lookup"><span data-stu-id="65814-112">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="65814-113">Указывает, что вызов относится к свойству.</span><span class="sxs-lookup"><span data-stu-id="65814-113">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="65814-114">Указывает, что вызов является неуправляемым.</span><span class="sxs-lookup"><span data-stu-id="65814-114">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="65814-115">Указывает на создание экземпляра универсального метода.</span><span class="sxs-lookup"><span data-stu-id="65814-115">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="65814-116">Обозначает 64-разрядный вызов PInvoke для метода, принимающего переменное число параметров.</span><span class="sxs-lookup"><span data-stu-id="65814-116">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="65814-117">Описывает недопустимое 4-битовое значение.</span><span class="sxs-lookup"><span data-stu-id="65814-117">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="65814-118">Указывает, что соглашение о вызовах описывается четырьмя нижними битами.</span><span class="sxs-lookup"><span data-stu-id="65814-118">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="65814-119">Указывает, что верхний бит описывает `this` параметр.</span><span class="sxs-lookup"><span data-stu-id="65814-119">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="65814-120">Указывает, что `this` параметр явно описан в сигнатуре.</span><span class="sxs-lookup"><span data-stu-id="65814-120">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="65814-121">Указывает сигнатуру универсального метода с явным числом аргументов типа.</span><span class="sxs-lookup"><span data-stu-id="65814-121">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="65814-122">Это значение предшествует обычному числу параметров.</span><span class="sxs-lookup"><span data-stu-id="65814-122">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65814-123">Требования</span><span class="sxs-lookup"><span data-stu-id="65814-123">Requirements</span></span>  

 <span data-ttu-id="65814-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65814-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65814-125">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="65814-125">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="65814-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65814-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65814-127">См. также</span><span class="sxs-lookup"><span data-stu-id="65814-127">See also</span></span>

- [<span data-ttu-id="65814-128">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="65814-128">Metadata Enumerations</span></span>](metadata-enumerations.md)
