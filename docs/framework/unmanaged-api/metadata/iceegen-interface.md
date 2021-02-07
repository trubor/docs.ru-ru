---
description: 'Дополнительные сведения о: ICeeGen Interface'
title: Интерфейс ICeeGen
ms.date: 03/30/2017
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
ms.openlocfilehash: 43e9e0696523346ffbcf0b8823a48ed2c9c359e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706816"
---
# <a name="iceegen-interface"></a><span data-ttu-id="ecc2f-103">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="ecc2f-103">ICeeGen Interface</span></span>

<span data-ttu-id="ecc2f-104">Предоставляет методы для динамической компиляции кода.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-104">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="ecc2f-105">Этот интерфейс устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-105">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ecc2f-106">Методы</span><span class="sxs-lookup"><span data-stu-id="ecc2f-106">Methods</span></span>  
  
|<span data-ttu-id="ecc2f-107">Метод</span><span class="sxs-lookup"><span data-stu-id="ecc2f-107">Method</span></span>|<span data-ttu-id="ecc2f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ecc2f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ecc2f-109">Метод AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="ecc2f-109">AddSectionReloc Method</span></span>](iceegen-addsectionreloc-method.md)|<span data-ttu-id="ecc2f-110">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-110">Obsolete.</span></span> <span data-ttu-id="ecc2f-111">Добавляет инструкцию. reloc в базу кода.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-111">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="ecc2f-112">Метод AllocateMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="ecc2f-112">AllocateMethodBuffer Method</span></span>](iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="ecc2f-113">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-113">Obsolete.</span></span> <span data-ttu-id="ecc2f-114">Создает буфер указанного размера для метода и получает относительный виртуальный адрес метода.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-114">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="ecc2f-115">Метод ComputePointer</span><span class="sxs-lookup"><span data-stu-id="ecc2f-115">ComputePointer Method</span></span>](iceegen-computepointer-method.md)|<span data-ttu-id="ecc2f-116">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-116">Obsolete.</span></span> <span data-ttu-id="ecc2f-117">Определяет буфер для указанного раздела кода.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-117">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="ecc2f-118">Метод EmitString</span><span class="sxs-lookup"><span data-stu-id="ecc2f-118">EmitString Method</span></span>](iceegen-emitstring-method.md)|<span data-ttu-id="ecc2f-119">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-119">Obsolete.</span></span> <span data-ttu-id="ecc2f-120">Порождает указанную строку в базу кода.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-120">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="ecc2f-121">Метод GenerateCeeFile</span><span class="sxs-lookup"><span data-stu-id="ecc2f-121">GenerateCeeFile Method</span></span>](iceegen-generateceefile-method.md)|<span data-ttu-id="ecc2f-122">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-122">Obsolete.</span></span> <span data-ttu-id="ecc2f-123">Создает файл с базовым кодом, который содержит базу кода, загруженную в данный момент `ICeeGen` .</span><span class="sxs-lookup"><span data-stu-id="ecc2f-123">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="ecc2f-124">Метод GenerateCeeMemoryImage</span><span class="sxs-lookup"><span data-stu-id="ecc2f-124">GenerateCeeMemoryImage Method</span></span>](iceegen-generateceememoryimage-method.md)|<span data-ttu-id="ecc2f-125">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-125">Obsolete.</span></span> <span data-ttu-id="ecc2f-126">Создает изображение в памяти для базы кода.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-126">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="ecc2f-127">Метод GetIlSection</span><span class="sxs-lookup"><span data-stu-id="ecc2f-127">GetIlSection Method</span></span>](iceegen-getilsection-method.md)|<span data-ttu-id="ecc2f-128">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-128">Obsolete.</span></span> <span data-ttu-id="ecc2f-129">Возвращает раздел базы кода промежуточного языка, на который ссылается указанный обработчик.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-129">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="ecc2f-130">Метод GetIMapTokenIface</span><span class="sxs-lookup"><span data-stu-id="ecc2f-130">GetIMapTokenIface Method</span></span>](iceegen-getimaptokeniface-method.md)|<span data-ttu-id="ecc2f-131">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-131">Obsolete.</span></span> <span data-ttu-id="ecc2f-132">Возвращает интерфейс, на который ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-132">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="ecc2f-133">Метод GetMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="ecc2f-133">GetMethodBuffer Method</span></span>](iceegen-getmethodbuffer-method.md)|<span data-ttu-id="ecc2f-134">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-134">Obsolete.</span></span> <span data-ttu-id="ecc2f-135">Возвращает буфер соответствующего размера для метода по указанному относительному виртуальному адресу.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-135">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="ecc2f-136">Метод GetSectionBlock</span><span class="sxs-lookup"><span data-stu-id="ecc2f-136">GetSectionBlock Method</span></span>](iceegen-getsectionblock-method.md)|<span data-ttu-id="ecc2f-137">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-137">Obsolete.</span></span> <span data-ttu-id="ecc2f-138">Возвращает блок базы кода.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-138">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="ecc2f-139">Метод GetSectionCreate</span><span class="sxs-lookup"><span data-stu-id="ecc2f-139">GetSectionCreate Method</span></span>](iceegen-getsectioncreate-method.md)|<span data-ttu-id="ecc2f-140">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-140">Obsolete.</span></span> <span data-ttu-id="ecc2f-141">Создает и получает раздел кода, используя указанные значения имени и флага.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-141">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="ecc2f-142">Метод GetSectionDataLen</span><span class="sxs-lookup"><span data-stu-id="ecc2f-142">GetSectionDataLen Method</span></span>](iceegen-getsectiondatalen-method.md)|<span data-ttu-id="ecc2f-143">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-143">Obsolete.</span></span> <span data-ttu-id="ecc2f-144">Возвращает длину указанного раздела.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-144">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="ecc2f-145">Метод GetString</span><span class="sxs-lookup"><span data-stu-id="ecc2f-145">GetString Method</span></span>](iceegen-getstring-method.md)|<span data-ttu-id="ecc2f-146">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-146">Obsolete.</span></span> <span data-ttu-id="ecc2f-147">Возвращает строку, хранящуюся по указанному относительному виртуальному адресу.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-147">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="ecc2f-148">Метод GetStringSection</span><span class="sxs-lookup"><span data-stu-id="ecc2f-148">GetStringSection Method</span></span>](iceegen-getstringsection-method.md)|<span data-ttu-id="ecc2f-149">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-149">Obsolete.</span></span> <span data-ttu-id="ecc2f-150">Возвращает строковое представление раздела кода, на который ссылается указанный маркер.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-150">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="ecc2f-151">Метод TruncateSection</span><span class="sxs-lookup"><span data-stu-id="ecc2f-151">TruncateSection Method</span></span>](iceegen-truncatesection-method.md)|<span data-ttu-id="ecc2f-152">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-152">Obsolete.</span></span> <span data-ttu-id="ecc2f-153">Усекает указанный раздел кода на заданную длину.</span><span class="sxs-lookup"><span data-stu-id="ecc2f-153">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ecc2f-154">Требования</span><span class="sxs-lookup"><span data-stu-id="ecc2f-154">Requirements</span></span>  

 <span data-ttu-id="ecc2f-155">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecc2f-155">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecc2f-156">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="ecc2f-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ecc2f-157">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecc2f-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ecc2f-158">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecc2f-158">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc2f-159">См. также</span><span class="sxs-lookup"><span data-stu-id="ecc2f-159">See also</span></span>

- [<span data-ttu-id="ecc2f-160">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="ecc2f-160">Metadata Interfaces</span></span>](metadata-interfaces.md)
