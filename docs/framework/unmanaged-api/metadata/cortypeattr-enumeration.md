---
description: Дополнительные сведения о перечислении Кортипеаттр
title: Перечисление CorTypeAttr
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
ms.openlocfilehash: d4f7d25ce8ead945790defae800b7a45dc88bc38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721171"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="cd863-103">Перечисление CorTypeAttr</span><span class="sxs-lookup"><span data-stu-id="cd863-103">CorTypeAttr Enumeration</span></span>

<span data-ttu-id="cd863-104">Содержит значения, указывающие тип метаданных.</span><span class="sxs-lookup"><span data-stu-id="cd863-104">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd863-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cd863-105">Syntax</span></span>  
  
```cpp  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="cd863-106">Члены</span><span class="sxs-lookup"><span data-stu-id="cd863-106">Members</span></span>  
  
|<span data-ttu-id="cd863-107">Член</span><span class="sxs-lookup"><span data-stu-id="cd863-107">Member</span></span>|<span data-ttu-id="cd863-108">Описание</span><span class="sxs-lookup"><span data-stu-id="cd863-108">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="cd863-109">Используется для сведений о видимости типа.</span><span class="sxs-lookup"><span data-stu-id="cd863-109">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="cd863-110">Указывает, что тип не находится в общедоступной области.</span><span class="sxs-lookup"><span data-stu-id="cd863-110">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="cd863-111">Указывает, что тип находится в общедоступной области.</span><span class="sxs-lookup"><span data-stu-id="cd863-111">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="cd863-112">Указывает, что тип является вложенным с открытой видимостью.</span><span class="sxs-lookup"><span data-stu-id="cd863-112">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="cd863-113">Указывает, что тип является вложенным с закрытой видимостью.</span><span class="sxs-lookup"><span data-stu-id="cd863-113">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="cd863-114">Указывает, что тип является вложенным с видимостью в семействе.</span><span class="sxs-lookup"><span data-stu-id="cd863-114">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="cd863-115">Указывает, что тип является вложенным с видимостью сборки.</span><span class="sxs-lookup"><span data-stu-id="cd863-115">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="cd863-116">Указывает, что тип является вложенным с видимостью в семействе и сборке.</span><span class="sxs-lookup"><span data-stu-id="cd863-116">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="cd863-117">Указывает, что тип является вложенным с видимостью семейства или сборки.</span><span class="sxs-lookup"><span data-stu-id="cd863-117">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="cd863-118">Возвращает сведения о макете для типа.</span><span class="sxs-lookup"><span data-stu-id="cd863-118">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="cd863-119">Указывает, что поля этого типа размещаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="cd863-119">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="cd863-120">Указывает, что поля этого типа располагаются последовательно.</span><span class="sxs-lookup"><span data-stu-id="cd863-120">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="cd863-121">Указывает, что макет поля указан явно.</span><span class="sxs-lookup"><span data-stu-id="cd863-121">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="cd863-122">Возвращает семантическую информацию о типе.</span><span class="sxs-lookup"><span data-stu-id="cd863-122">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="cd863-123">Указывает, что данный тип является классом.</span><span class="sxs-lookup"><span data-stu-id="cd863-123">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="cd863-124">Указывает, что данный тип является интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="cd863-124">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="cd863-125">Указывает, что данный тип является абстрактным.</span><span class="sxs-lookup"><span data-stu-id="cd863-125">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="cd863-126">Указывает, что тип не может быть расширен.</span><span class="sxs-lookup"><span data-stu-id="cd863-126">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="cd863-127">Указывает, что имя класса является специальным.</span><span class="sxs-lookup"><span data-stu-id="cd863-127">Specifies that the class name is special.</span></span> <span data-ttu-id="cd863-128">Его имя описывает, как это делать.</span><span class="sxs-lookup"><span data-stu-id="cd863-128">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="cd863-129">Указывает, что тип импортирован.</span><span class="sxs-lookup"><span data-stu-id="cd863-129">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="cd863-130">Указывает, что тип является сериализуемым.</span><span class="sxs-lookup"><span data-stu-id="cd863-130">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="cd863-131">Указывает, что этот тип является типом среда выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="cd863-131">Specifies that this type is a Windows Runtime type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="cd863-132">Получает сведения о кодировке и форматировании строк.</span><span class="sxs-lookup"><span data-stu-id="cd863-132">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="cd863-133">Указывает, что этот тип интерпретирует LPTSTR как ANSI.</span><span class="sxs-lookup"><span data-stu-id="cd863-133">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="cd863-134">Указывает, что этот тип интерпретирует LPTSTR как Юникод.</span><span class="sxs-lookup"><span data-stu-id="cd863-134">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="cd863-135">Указывает, что этот тип интерпретирует LPTSTR автоматически.</span><span class="sxs-lookup"><span data-stu-id="cd863-135">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="cd863-136">Указывает, что тип имеет нестандартную кодировку, как указано в `CustomFormatMask` .</span><span class="sxs-lookup"><span data-stu-id="cd863-136">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="cd863-137">Используйте эту маску для получения нестандартных сведений о кодировке для собственного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="cd863-137">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="cd863-138">Значение этих двух битов не определено.</span><span class="sxs-lookup"><span data-stu-id="cd863-138">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="cd863-139">Указывает, что тип должен быть инициализирован перед первой попыткой доступа к статическому полю.</span><span class="sxs-lookup"><span data-stu-id="cd863-139">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="cd863-140">Указывает, что тип экспортирован и является пересылкой типа.</span><span class="sxs-lookup"><span data-stu-id="cd863-140">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="cd863-141">Этот флаг и указанные ниже флаги используются внутри среды CLR.</span><span class="sxs-lookup"><span data-stu-id="cd863-141">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="cd863-142">Указывает, что среда CLR должна проверять кодировку имен.</span><span class="sxs-lookup"><span data-stu-id="cd863-142">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="cd863-143">Указывает, что с типом связана безопасность.</span><span class="sxs-lookup"><span data-stu-id="cd863-143">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd863-144">Требования</span><span class="sxs-lookup"><span data-stu-id="cd863-144">Requirements</span></span>  

 <span data-ttu-id="cd863-145">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd863-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd863-146">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="cd863-146">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cd863-147">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd863-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd863-148">См. также</span><span class="sxs-lookup"><span data-stu-id="cd863-148">See also</span></span>

- [<span data-ttu-id="cd863-149">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="cd863-149">Metadata Enumerations</span></span>](metadata-enumerations.md)
