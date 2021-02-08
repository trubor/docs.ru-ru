---
description: Дополнительные сведения о перечислении Корфиелдаттр
title: Перечисление CorFieldAttr
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
ms.openlocfilehash: ac342f67a53da75fd9711ebfdd2f2c448cf27d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784500"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="497bd-103">Перечисление CorFieldAttr</span><span class="sxs-lookup"><span data-stu-id="497bd-103">CorFieldAttr Enumeration</span></span>

<span data-ttu-id="497bd-104">Содержит значения, описывающие метаданные поля.</span><span class="sxs-lookup"><span data-stu-id="497bd-104">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="497bd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="497bd-105">Syntax</span></span>  
  
```cpp  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="497bd-106">Члены</span><span class="sxs-lookup"><span data-stu-id="497bd-106">Members</span></span>  
  
|<span data-ttu-id="497bd-107">Член</span><span class="sxs-lookup"><span data-stu-id="497bd-107">Member</span></span>|<span data-ttu-id="497bd-108">Описание</span><span class="sxs-lookup"><span data-stu-id="497bd-108">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="497bd-109">Указывает сведения о специальных возможностях.</span><span class="sxs-lookup"><span data-stu-id="497bd-109">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="497bd-110">Определяет, что на поле нельзя ссылаться.</span><span class="sxs-lookup"><span data-stu-id="497bd-110">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="497bd-111">Указывает, что поле доступно только для его родительского типа.</span><span class="sxs-lookup"><span data-stu-id="497bd-111">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="497bd-112">Указывает, что поле доступно для производных классов в его сборке.</span><span class="sxs-lookup"><span data-stu-id="497bd-112">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="497bd-113">Указывает, что поле доступно для всех типов в его сборке.</span><span class="sxs-lookup"><span data-stu-id="497bd-113">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="497bd-114">Указывает, что поле доступно только для его типа и производных классов.</span><span class="sxs-lookup"><span data-stu-id="497bd-114">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="497bd-115">Указывает, что поле доступно для производных классов и всех типов в его сборке.</span><span class="sxs-lookup"><span data-stu-id="497bd-115">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="497bd-116">Указывает, что поле доступно для всех типов с видимостью этой области.</span><span class="sxs-lookup"><span data-stu-id="497bd-116">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="497bd-117">Указывает, что поле является членом его типа, а не членом экземпляра.</span><span class="sxs-lookup"><span data-stu-id="497bd-117">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="497bd-118">Указывает, что поле нельзя изменить после его инициализации.</span><span class="sxs-lookup"><span data-stu-id="497bd-118">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="497bd-119">Указывает, что значение поля является константой времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="497bd-119">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="497bd-120">Указывает, что поле не сериализуется при удаленном типе.</span><span class="sxs-lookup"><span data-stu-id="497bd-120">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="497bd-121">Указывает, что поле является специальным, и что его имя описывает, как это делать.</span><span class="sxs-lookup"><span data-stu-id="497bd-121">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="497bd-122">Указывает, что реализация поля пересылается через PInvoke.</span><span class="sxs-lookup"><span data-stu-id="497bd-122">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="497bd-123">Зарезервировано для внутреннего использования средой CLR.</span><span class="sxs-lookup"><span data-stu-id="497bd-123">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="497bd-124">Указывает, что внутренние API метаданных среды CLR должны проверять кодировку имени.</span><span class="sxs-lookup"><span data-stu-id="497bd-124">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="497bd-125">Указывает, что поле содержит сведения о маршалировании.</span><span class="sxs-lookup"><span data-stu-id="497bd-125">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="497bd-126">Определяет, что для поля задано значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="497bd-126">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="497bd-127">Указывает, что поле имеет относительный виртуальный адрес.</span><span class="sxs-lookup"><span data-stu-id="497bd-127">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="497bd-128">Требования</span><span class="sxs-lookup"><span data-stu-id="497bd-128">Requirements</span></span>  

 <span data-ttu-id="497bd-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="497bd-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="497bd-130">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="497bd-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="497bd-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="497bd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="497bd-132">См. также</span><span class="sxs-lookup"><span data-stu-id="497bd-132">See also</span></span>

- [<span data-ttu-id="497bd-133">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="497bd-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
