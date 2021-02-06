---
description: 'Дополнительные сведения о: Ассембляттрибутесгохерем Class'
title: Класс Ассембляттрибутесгохерем (System. Runtime. CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
ms.openlocfilehash: 9afa72e5adbd539acaf8dfe45b446a61862df49e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638578"
---
# <a name="assemblyattributesgoherem-class"></a><span data-ttu-id="008e9-103">Класс Ассембляттрибутесгохерем</span><span class="sxs-lookup"><span data-stu-id="008e9-103">AssemblyAttributesGoHereM Class</span></span>

<span data-ttu-id="008e9-104">Используется ALink как заполнитель для хранения сведений о пользовательских атрибутах.</span><span class="sxs-lookup"><span data-stu-id="008e9-104">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="008e9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="008e9-105">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereM
```

## <a name="remarks"></a><span data-ttu-id="008e9-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="008e9-106">Remarks</span></span>

<span data-ttu-id="008e9-107">Ссылки на этот тип можно включать в модули NETMODULE, источник которых содержат пользовательские атрибуты сборки.</span><span class="sxs-lookup"><span data-stu-id="008e9-107">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="008e9-108">При построении манифеста сборки из одного или нескольких файлов, содержащих ссылки на эти NETMODULE, ALink использует сведения, подключенные к этим ссылкам, для выдачи фактических пользовательских атрибутов.</span><span class="sxs-lookup"><span data-stu-id="008e9-108">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="008e9-109">Таким образом, экземпляр этого типа никогда не создается, а ссылки на него используются только как часть процесса сборки и бесполезны в окончательной сборке.</span><span class="sxs-lookup"><span data-stu-id="008e9-109">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="008e9-110">Ссылки на этот тип указывают пользовательские атрибуты, не связанные с безопасностью, но многократного использования.</span><span class="sxs-lookup"><span data-stu-id="008e9-110">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>

<span data-ttu-id="008e9-111">Эти типы помечены как "внутренние" в платформа .NET Framework и находятся в <xref:System.Runtime.CompilerServices> пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="008e9-111">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="008e9-112">Требования</span><span class="sxs-lookup"><span data-stu-id="008e9-112">Requirements</span></span>

<span data-ttu-id="008e9-113">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="008e9-113">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="008e9-114">См. также</span><span class="sxs-lookup"><span data-stu-id="008e9-114">See also</span></span>

- [<span data-ttu-id="008e9-115">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="008e9-115">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="008e9-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="008e9-116">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="008e9-117">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="008e9-117">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
