---
description: 'Дополнительные сведения о: GUID_ManagedName атрибут'
title: Атрибут GUID_ManagedName
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
ms.openlocfilehash: c139e8bdc00aa3b008a706de0c42cfbf8e3510c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799997"
---
# <a name="guid_managedname-attribute"></a><span data-ttu-id="83585-103">Атрибут GUID_ManagedName</span><span class="sxs-lookup"><span data-stu-id="83585-103">GUID_ManagedName Attribute</span></span>

<span data-ttu-id="83585-104">Определяет настраиваемый атрибут интерфейса, указывающий имя управляемого пространства имен для библиотеки COM.</span><span class="sxs-lookup"><span data-stu-id="83585-104">Defines a custom interface attribute that specifies the managed namespace name for a component object model (COM) library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83585-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83585-105">Syntax</span></span>  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a><span data-ttu-id="83585-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="83585-106">Parameters</span></span>  

 `value`  
 <span data-ttu-id="83585-107">Имя управляемого пространства имен для библиотеки.</span><span class="sxs-lookup"><span data-stu-id="83585-107">The managed namespace name for the library.</span></span>  
  
## <a name="definition"></a><span data-ttu-id="83585-108">Определение</span><span class="sxs-lookup"><span data-stu-id="83585-108">Definition</span></span>  

 <span data-ttu-id="83585-109">`GUID_ManagedName` определяется в COR. h следующим образом:</span><span class="sxs-lookup"><span data-stu-id="83585-109">`GUID_ManagedName` is defined in Cor.h as follows:</span></span>  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a><span data-ttu-id="83585-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="83585-110">Remarks</span></span>  

 <span data-ttu-id="83585-111">Пользовательский атрибут интерфейса определяет метаданные для объекта в библиотеке типов.</span><span class="sxs-lookup"><span data-stu-id="83585-111">A custom interface attribute defines metadata for an object in the type library.</span></span>  
  
 <span data-ttu-id="83585-112">Используйте <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> или <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> для получения управляемого имени из атрибута.</span><span class="sxs-lookup"><span data-stu-id="83585-112">Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> to retrieve the managed name from the attribute.</span></span>  
  
 <span data-ttu-id="83585-113">Дополнительные сведения см. в разделе [атрибуты интерфейса](/cpp/windows/attributes/interface-attributes) в справочной документации по Visual C++.</span><span class="sxs-lookup"><span data-stu-id="83585-113">For more information, see [Interface Attributes](/cpp/windows/attributes/interface-attributes) in the Visual C++ reference documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83585-114">Пример</span><span class="sxs-lookup"><span data-stu-id="83585-114">Example</span></span>  

 <span data-ttu-id="83585-115">В следующем примере показано определение библиотеки с помощью `GUID_ManagedName` атрибута.</span><span class="sxs-lookup"><span data-stu-id="83585-115">The following example shows a library definition using the `GUID_ManagedName` attribute.</span></span>  
  
```idl
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="83585-116">Требования</span><span class="sxs-lookup"><span data-stu-id="83585-116">Requirements</span></span>  

 <span data-ttu-id="83585-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="83585-117">**Header:** Cor.h</span></span>
