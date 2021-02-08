---
description: Дополнительные сведения о перечислении Кормесодимпл
title: Перечисление CorMethodImpl
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
ms.openlocfilehash: 157db81a72742f1f2aae7e95249b819b2396ef4b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784396"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="6122e-103">Перечисление CorMethodImpl</span><span class="sxs-lookup"><span data-stu-id="6122e-103">CorMethodImpl Enumeration</span></span>

<span data-ttu-id="6122e-104">Содержит значения, описывающие возможности реализации метода.</span><span class="sxs-lookup"><span data-stu-id="6122e-104">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6122e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6122e-105">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a><span data-ttu-id="6122e-106">Члены</span><span class="sxs-lookup"><span data-stu-id="6122e-106">Members</span></span>  
  
|<span data-ttu-id="6122e-107">Член</span><span class="sxs-lookup"><span data-stu-id="6122e-107">Member</span></span>|<span data-ttu-id="6122e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="6122e-108">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="6122e-109">Флаги, описывающие тип кода.</span><span class="sxs-lookup"><span data-stu-id="6122e-109">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="6122e-110">Указывает, что реализация метода является промежуточным языком Майкрософт (MSIL).</span><span class="sxs-lookup"><span data-stu-id="6122e-110">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="6122e-111">Указывает, что для метода используется стандартная реализация.</span><span class="sxs-lookup"><span data-stu-id="6122e-111">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="6122e-112">Указывает, что реализация метода — OPIL.</span><span class="sxs-lookup"><span data-stu-id="6122e-112">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="6122e-113">Указывает, что реализация метода предоставляется средой CLR.</span><span class="sxs-lookup"><span data-stu-id="6122e-113">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="6122e-114">Флаги, указывающие, является ли код управляемым или неуправляемым.</span><span class="sxs-lookup"><span data-stu-id="6122e-114">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="6122e-115">Указывает, что реализация метода является неуправляемой.</span><span class="sxs-lookup"><span data-stu-id="6122e-115">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="6122e-116">Указывает, что реализация метода является управляемой.</span><span class="sxs-lookup"><span data-stu-id="6122e-116">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="6122e-117">Указывает, что метод определен.</span><span class="sxs-lookup"><span data-stu-id="6122e-117">Specifies that the method is defined.</span></span> <span data-ttu-id="6122e-118">Этот флаг используется в основном в сценариях слияния.</span><span class="sxs-lookup"><span data-stu-id="6122e-118">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="6122e-119">Указывает, что подпись метода не может быть искажена для преобразования HRESULT.</span><span class="sxs-lookup"><span data-stu-id="6122e-119">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="6122e-120">Зарезервировано для внутреннего использования средой CLR.</span><span class="sxs-lookup"><span data-stu-id="6122e-120">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="6122e-121">Указывает, что метод является однопотоковым через его тело.</span><span class="sxs-lookup"><span data-stu-id="6122e-121">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="6122e-122">Указывает, что метод нельзя выполнять как встроенный.</span><span class="sxs-lookup"><span data-stu-id="6122e-122">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="6122e-123">Указывает, что метод должен быть встроенным, если это возможно.</span><span class="sxs-lookup"><span data-stu-id="6122e-123">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="6122e-124">Указывает, что метод не должен быть оптимизирован.</span><span class="sxs-lookup"><span data-stu-id="6122e-124">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="6122e-125">Максимальное допустимое значение для `CorMethodImpl` .</span><span class="sxs-lookup"><span data-stu-id="6122e-125">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6122e-126">Требования</span><span class="sxs-lookup"><span data-stu-id="6122e-126">Requirements</span></span>  

 <span data-ttu-id="6122e-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6122e-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6122e-128">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="6122e-128">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6122e-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6122e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6122e-130">См. также</span><span class="sxs-lookup"><span data-stu-id="6122e-130">See also</span></span>

- [<span data-ttu-id="6122e-131">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="6122e-131">Metadata Enumerations</span></span>](metadata-enumerations.md)
