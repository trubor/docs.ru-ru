---
description: 'Дополнительные сведения о методе: ISymUnmanagedBinder2:: GetReaderForFile2'
title: Метод ISymUnmanagedBinder2::GetReaderForFile2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
ms.openlocfilehash: c1a180ceec07c3087150613365acfce646adc34e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689941"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="533d8-103">Метод ISymUnmanagedBinder2::GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="533d8-103">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>

<span data-ttu-id="533d8-104">При наличии интерфейса метаданных и имени файла возвращает правильный интерфейс [ISymUnmanagedReader](isymunmanagedreader-interface.md) , который будет считывать символы отладки, связанные с модулем.</span><span class="sxs-lookup"><span data-stu-id="533d8-104">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="533d8-105">Этот метод обеспечивает более широкий поиск файла базы данных программы (PDB), чем метод [ISymUnmanagedBinder:: getreaderforfile:](isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="533d8-105">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="533d8-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="533d8-106">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="533d8-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="533d8-107">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="533d8-108">окне Указатель на интерфейс импорта метаданных.</span><span class="sxs-lookup"><span data-stu-id="533d8-108">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="533d8-109">окне Указатель на имя файла.</span><span class="sxs-lookup"><span data-stu-id="533d8-109">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="533d8-110">окне Указатель на путь поиска.</span><span class="sxs-lookup"><span data-stu-id="533d8-110">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="533d8-111">окне Значение перечисления [корсимсеарчполициаттрибутес](corsymsearchpolicyattributes-enumeration.md) , указывающее политику, используемую при поиске средства чтения символов.</span><span class="sxs-lookup"><span data-stu-id="533d8-111">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="533d8-112">заполняет Указатель, которому присваивается возвращаемый интерфейс [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="533d8-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="533d8-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="533d8-113">Return Value</span></span>  

 <span data-ttu-id="533d8-114">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="533d8-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="533d8-115">Требования</span><span class="sxs-lookup"><span data-stu-id="533d8-115">Requirements</span></span>  

 <span data-ttu-id="533d8-116">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="533d8-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="533d8-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="533d8-117">Remarks</span></span>  

 <span data-ttu-id="533d8-118">Эта версия метода может искать PDB-файл в областях, отличных от right рядом с модулем.</span><span class="sxs-lookup"><span data-stu-id="533d8-118">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="533d8-119">Политику поиска можно контролировать путем объединения [корсимсеарчполициаттрибутес](corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="533d8-119">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="533d8-120">Например, `AllowReferencePathAccess | AllowSymbolServerAccess` выполняет поиск PDB-файла рядом с исполняемым файлом и на сервере символов, но не запрашивает реестр или не использует путь в исполняемом файле.</span><span class="sxs-lookup"><span data-stu-id="533d8-120">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="533d8-121">Если `searchPath` указан параметр, то поиск в этих каталогах будет выполняться всегда.</span><span class="sxs-lookup"><span data-stu-id="533d8-121">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="533d8-122">См. также</span><span class="sxs-lookup"><span data-stu-id="533d8-122">See also</span></span>

- [<span data-ttu-id="533d8-123">Интерфейс ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="533d8-123">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="533d8-124">Метод GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="533d8-124">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)
