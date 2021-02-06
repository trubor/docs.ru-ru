---
description: 'Дополнительные сведения о: Ассембляттрибутесгохересм Class'
title: Класс Ассембляттрибутесгохересм (System. Runtime. CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereSM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
ms.openlocfilehash: ac38017b6ae9169b853da1daa8533d4c1cf44d97
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638526"
---
# <a name="assemblyattributesgoheresm-class"></a><span data-ttu-id="51dcc-103">Класс Ассембляттрибутесгохересм</span><span class="sxs-lookup"><span data-stu-id="51dcc-103">AssemblyAttributesGoHereSM Class</span></span>

<span data-ttu-id="51dcc-104">Используется ALink как заполнитель для хранения сведений о пользовательских атрибутах.</span><span class="sxs-lookup"><span data-stu-id="51dcc-104">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="51dcc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="51dcc-105">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereSM
```

## <a name="remarks"></a><span data-ttu-id="51dcc-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="51dcc-106">Remarks</span></span>

<span data-ttu-id="51dcc-107">Ссылки на этот тип можно включать в модули NETMODULE, источник которых содержат пользовательские атрибуты сборки.</span><span class="sxs-lookup"><span data-stu-id="51dcc-107">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="51dcc-108">При построении манифеста сборки из одного или нескольких файлов, содержащих ссылки на эти NETMODULE, ALink использует сведения, подключенные к этим ссылкам, для выдачи фактических пользовательских атрибутов.</span><span class="sxs-lookup"><span data-stu-id="51dcc-108">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="51dcc-109">Таким образом, экземпляр этого типа никогда не создается, а ссылки на него используются только как часть процесса сборки и бесполезны в окончательной сборке.</span><span class="sxs-lookup"><span data-stu-id="51dcc-109">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="51dcc-110">Ссылки на этот тип указывают пользовательские атрибуты многократного использования, связанные с безопасностью.</span><span class="sxs-lookup"><span data-stu-id="51dcc-110">References to this type indicate custom attributes that are security related and multiple-use.</span></span>

<span data-ttu-id="51dcc-111">Эти типы помечены как "внутренние" в платформа .NET Framework и находятся в <xref:System.Runtime.CompilerServices> пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="51dcc-111">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="51dcc-112">Требования</span><span class="sxs-lookup"><span data-stu-id="51dcc-112">Requirements</span></span>

<span data-ttu-id="51dcc-113">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="51dcc-113">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="51dcc-114">См. также</span><span class="sxs-lookup"><span data-stu-id="51dcc-114">See also</span></span>

- [<span data-ttu-id="51dcc-115">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="51dcc-115">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="51dcc-116">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="51dcc-116">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="51dcc-117">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="51dcc-117">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
