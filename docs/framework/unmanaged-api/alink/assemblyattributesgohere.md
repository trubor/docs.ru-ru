---
description: 'Дополнительные сведения о: Ассембляттрибутесгохере Class'
title: Класс Ассембляттрибутесгохере (System. Runtime. CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHere
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
ms.openlocfilehash: b95ff377f7fa0ffc85136dd69eb4a32121a50dc2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638591"
---
# <a name="assemblyattributesgohere-class"></a><span data-ttu-id="913bb-103">Класс Ассембляттрибутесгохере</span><span class="sxs-lookup"><span data-stu-id="913bb-103">AssemblyAttributesGoHere Class</span></span>

<span data-ttu-id="913bb-104">Используется ALink как заполнитель для хранения сведений о пользовательских атрибутах.</span><span class="sxs-lookup"><span data-stu-id="913bb-104">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="913bb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="913bb-105">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a><span data-ttu-id="913bb-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="913bb-106">Remarks</span></span>

<span data-ttu-id="913bb-107">Ссылки на этот тип можно включать в модули NETMODULE, источник которых содержат пользовательские атрибуты сборки.</span><span class="sxs-lookup"><span data-stu-id="913bb-107">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="913bb-108">При построении манифеста сборки из одного или нескольких файлов, содержащих ссылки на эти NETMODULE, ALink использует сведения, подключенные к этим ссылкам, для выдачи фактических пользовательских атрибутов.</span><span class="sxs-lookup"><span data-stu-id="913bb-108">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="913bb-109">Таким образом, экземпляр этого типа никогда не создается, а ссылки на него используются только как часть процесса сборки и бесполезны в окончательной сборке.</span><span class="sxs-lookup"><span data-stu-id="913bb-109">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="913bb-110">Ссылки на этот тип указывают пользовательские атрибуты, не связанные с безопасностью, которые нельзя использовать многократно.</span><span class="sxs-lookup"><span data-stu-id="913bb-110">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>

<span data-ttu-id="913bb-111">Эти типы помечены как "внутренние" в платформа .NET Framework и находятся в <xref:System.Runtime.CompilerServices> пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="913bb-111">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="913bb-112">Требования</span><span class="sxs-lookup"><span data-stu-id="913bb-112">Requirements</span></span>

<span data-ttu-id="913bb-113">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="913bb-113">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="913bb-114">См. также</span><span class="sxs-lookup"><span data-stu-id="913bb-114">See also</span></span>

- [<span data-ttu-id="913bb-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="913bb-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="913bb-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="913bb-116">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="913bb-117">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="913bb-117">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
