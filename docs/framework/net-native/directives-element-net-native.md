---
description: 'Дополнительные сведения об <Directives> элементе: Element (.NET Native)'
title: <Directives> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 7aa3bf3718f32d55ba8189c65705868c6fb399ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662914"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="3c20e-103">\<Directives> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="3c20e-103">\<Directives> Element (.NET Native)</span></span>

<span data-ttu-id="3c20e-104">Корневой элемент в каждом файле директив среды выполнения для .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3c20e-104">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="3c20e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3c20e-105">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="3c20e-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3c20e-106">Attributes</span></span>  
  
|<span data-ttu-id="3c20e-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="3c20e-107">Attribute</span></span>|<span data-ttu-id="3c20e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="3c20e-108">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="3c20e-109">Пространство имен XML.</span><span class="sxs-lookup"><span data-stu-id="3c20e-109">The XML namespace.</span></span> <span data-ttu-id="3c20e-110">Его значение всегда равно `http://schemas.microsoft.com/netfx/2013/01/metadata` .</span><span class="sxs-lookup"><span data-stu-id="3c20e-110">Its value is always `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="3c20e-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3c20e-111">Child elements</span></span>  
  
|<span data-ttu-id="3c20e-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="3c20e-112">Element</span></span>|<span data-ttu-id="3c20e-113">Описание</span><span class="sxs-lookup"><span data-stu-id="3c20e-113">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="3c20e-114">Служит в качестве контейнера для типов и членов типов приложения, метаданные которого доступны для отражения.</span><span class="sxs-lookup"><span data-stu-id="3c20e-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="3c20e-115">Определяет сборку, чьи дочерние типы и члены типов требуют метаданные во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="3c20e-115">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c20e-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="3c20e-116">Remarks</span></span>  

 <span data-ttu-id="3c20e-117">Каждый файл директив среды выполнения содержит только один элемент `<Directives>`.</span><span class="sxs-lookup"><span data-stu-id="3c20e-117">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="3c20e-118">`<Directives>`Элемент может содержать ноль или один [\<Application>](application-element-net-native.md) элемент, а также ноль, один или несколько [\<Library>](library-element-net-native.md) элементов.</span><span class="sxs-lookup"><span data-stu-id="3c20e-118">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c20e-119">См. также</span><span class="sxs-lookup"><span data-stu-id="3c20e-119">See also</span></span>

- [<span data-ttu-id="3c20e-120">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="3c20e-120">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="3c20e-121">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="3c20e-121">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
