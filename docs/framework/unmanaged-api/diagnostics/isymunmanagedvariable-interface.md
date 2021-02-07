---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedVariable'
title: Интерфейс ISymUnmanagedVariable
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
ms.openlocfilehash: 15b6c7018f92ad4c82abb9e5b4e52bf428b3f54b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762699"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="b2874-103">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="b2874-103">ISymUnmanagedVariable Interface</span></span>

<span data-ttu-id="b2874-104">Представляет переменную, например параметр, локальную переменную или поле.</span><span class="sxs-lookup"><span data-stu-id="b2874-104">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2874-105">Методы</span><span class="sxs-lookup"><span data-stu-id="b2874-105">Methods</span></span>  
  
|<span data-ttu-id="b2874-106">Метод</span><span class="sxs-lookup"><span data-stu-id="b2874-106">Method</span></span>|<span data-ttu-id="b2874-107">Описание</span><span class="sxs-lookup"><span data-stu-id="b2874-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2874-108">Метод GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="b2874-108">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="b2874-109">Возвращает первое поле адреса для этой переменной.</span><span class="sxs-lookup"><span data-stu-id="b2874-109">Gets the first address field for this variable.</span></span> <span data-ttu-id="b2874-110">Его значение зависит от типа адреса.</span><span class="sxs-lookup"><span data-stu-id="b2874-110">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="b2874-111">Метод GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="b2874-111">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="b2874-112">Получает второе поле адреса для этой переменной.</span><span class="sxs-lookup"><span data-stu-id="b2874-112">Gets the second address field for this variable.</span></span> <span data-ttu-id="b2874-113">Его значение зависит от типа адреса.</span><span class="sxs-lookup"><span data-stu-id="b2874-113">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="b2874-114">Метод GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="b2874-114">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="b2874-115">Возвращает третье поле адреса для этой переменной.</span><span class="sxs-lookup"><span data-stu-id="b2874-115">Gets the third address field for this variable.</span></span> <span data-ttu-id="b2874-116">Его значение зависит от типа адреса.</span><span class="sxs-lookup"><span data-stu-id="b2874-116">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="b2874-117">Метод GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="b2874-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="b2874-118">Возвращает тип адреса этой переменной.</span><span class="sxs-lookup"><span data-stu-id="b2874-118">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="b2874-119">Метод GetAttributes</span><span class="sxs-lookup"><span data-stu-id="b2874-119">GetAttributes Method</span></span>](isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="b2874-120">Возвращает флаги атрибута для этой переменной.</span><span class="sxs-lookup"><span data-stu-id="b2874-120">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="b2874-121">Метод GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="b2874-121">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="b2874-122">Возвращает конечное смещение данной переменной в родительском объекте.</span><span class="sxs-lookup"><span data-stu-id="b2874-122">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="b2874-123">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="b2874-123">GetName Method</span></span>](isymunmanagedvariable-getname-method.md)|<span data-ttu-id="b2874-124">Возвращает имя этой переменной.</span><span class="sxs-lookup"><span data-stu-id="b2874-124">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="b2874-125">Метод GetSignature</span><span class="sxs-lookup"><span data-stu-id="b2874-125">GetSignature Method</span></span>](isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="b2874-126">Возвращает сигнатуру этой переменной.</span><span class="sxs-lookup"><span data-stu-id="b2874-126">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="b2874-127">Метод GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="b2874-127">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="b2874-128">Возвращает начальное смещение этой переменной в родительском элементе.</span><span class="sxs-lookup"><span data-stu-id="b2874-128">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2874-129">Требования</span><span class="sxs-lookup"><span data-stu-id="b2874-129">Requirements</span></span>  

 <span data-ttu-id="b2874-130">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="b2874-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2874-131">См. также</span><span class="sxs-lookup"><span data-stu-id="b2874-131">See also</span></span>

- [<span data-ttu-id="b2874-132">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="b2874-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
