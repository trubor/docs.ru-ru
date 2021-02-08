---
description: Дополнительные сведения о перечислении Кормесодаттр
title: Перечисление CorMethodAttr
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
ms.openlocfilehash: 4050235675f4b237b184d31378a614a0613ab3df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784383"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="17ad2-103">Перечисление CorMethodAttr</span><span class="sxs-lookup"><span data-stu-id="17ad2-103">CorMethodAttr Enumeration</span></span>

<span data-ttu-id="17ad2-104">Содержит значения, описывающие возможности метода.</span><span class="sxs-lookup"><span data-stu-id="17ad2-104">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17ad2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17ad2-105">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="17ad2-106">Члены</span><span class="sxs-lookup"><span data-stu-id="17ad2-106">Members</span></span>  
  
|<span data-ttu-id="17ad2-107">Член</span><span class="sxs-lookup"><span data-stu-id="17ad2-107">Member</span></span>|<span data-ttu-id="17ad2-108">Описание</span><span class="sxs-lookup"><span data-stu-id="17ad2-108">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="17ad2-109">Указывает доступ к члену.</span><span class="sxs-lookup"><span data-stu-id="17ad2-109">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="17ad2-110">Указывает, что элемент не может быть указан.</span><span class="sxs-lookup"><span data-stu-id="17ad2-110">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="17ad2-111">Указывает, что элемент доступен только для родительского типа.</span><span class="sxs-lookup"><span data-stu-id="17ad2-111">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="17ad2-112">Указывает, что элемент доступен только для подтипов в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="17ad2-112">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="17ad2-113">Указывает, что элемент акцессиблися любым пользователем в сборке.</span><span class="sxs-lookup"><span data-stu-id="17ad2-113">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="17ad2-114">Указывает, что элемент доступен только по типу и подтипам.</span><span class="sxs-lookup"><span data-stu-id="17ad2-114">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="17ad2-115">Указывает, что член доступен для производных классов и других типов в его сборке.</span><span class="sxs-lookup"><span data-stu-id="17ad2-115">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="17ad2-116">Указывает, что элемент доступен для всех типов с доступом к области.</span><span class="sxs-lookup"><span data-stu-id="17ad2-116">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="17ad2-117">Указывает, что член определен как часть типа, а не как член экземпляра.</span><span class="sxs-lookup"><span data-stu-id="17ad2-117">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="17ad2-118">Указывает, что метод не может быть переопределен.</span><span class="sxs-lookup"><span data-stu-id="17ad2-118">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="17ad2-119">Указывает, что метод может быть переопределен.</span><span class="sxs-lookup"><span data-stu-id="17ad2-119">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="17ad2-120">Указывает, что метод скрывается по имени и сигнатуре, а не просто по имени.</span><span class="sxs-lookup"><span data-stu-id="17ad2-120">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="17ad2-121">Указывает макет виртуальной таблицы.</span><span class="sxs-lookup"><span data-stu-id="17ad2-121">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="17ad2-122">Указывает, что необходимо повторно использовать слот, используемый для этого метода в виртуальной таблице.</span><span class="sxs-lookup"><span data-stu-id="17ad2-122">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="17ad2-123">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="17ad2-123">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="17ad2-124">Указывает, что метод всегда получает новый слот в виртуальной таблице.</span><span class="sxs-lookup"><span data-stu-id="17ad2-124">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="17ad2-125">Указывает, что метод может быть переопределен теми же типами, для которых он является видимым.</span><span class="sxs-lookup"><span data-stu-id="17ad2-125">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="17ad2-126">Указывает, что метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="17ad2-126">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="17ad2-127">Указывает, что метод является специальным и что его имя описывает, как это делать.</span><span class="sxs-lookup"><span data-stu-id="17ad2-127">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="17ad2-128">Указывает, что реализация метода пересылается с помощью PInvoke.</span><span class="sxs-lookup"><span data-stu-id="17ad2-128">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="17ad2-129">Указывает, что метод является управляемым методом, экспортированным в неуправляемый код.</span><span class="sxs-lookup"><span data-stu-id="17ad2-129">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="17ad2-130">Зарезервировано для внутреннего использования средой CLR.</span><span class="sxs-lookup"><span data-stu-id="17ad2-130">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="17ad2-131">Указывает, что среда CLR должна проверять кодировку имени метода.</span><span class="sxs-lookup"><span data-stu-id="17ad2-131">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="17ad2-132">Указывает, что метод имеет связанную с ним безопасность.</span><span class="sxs-lookup"><span data-stu-id="17ad2-132">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="17ad2-133">Указывает, что метод вызывает другой метод, содержащий код безопасности.</span><span class="sxs-lookup"><span data-stu-id="17ad2-133">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17ad2-134">Требования</span><span class="sxs-lookup"><span data-stu-id="17ad2-134">Requirements</span></span>  

 <span data-ttu-id="17ad2-135">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17ad2-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17ad2-136">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="17ad2-136">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="17ad2-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17ad2-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ad2-138">См. также</span><span class="sxs-lookup"><span data-stu-id="17ad2-138">See also</span></span>

- [<span data-ttu-id="17ad2-139">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="17ad2-139">Metadata Enumerations</span></span>](metadata-enumerations.md)
