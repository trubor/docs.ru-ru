---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter::D Ефинедокумент'
title: Метод ISymUnmanagedWriter::DefineDocument
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
ms.openlocfilehash: 35e918292e6ee50e17932645e003d19513e2397a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762543"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="120e0-103">Метод ISymUnmanagedWriter::DefineDocument</span><span class="sxs-lookup"><span data-stu-id="120e0-103">ISymUnmanagedWriter::DefineDocument Method</span></span>

<span data-ttu-id="120e0-104">Определяет исходный документ.</span><span class="sxs-lookup"><span data-stu-id="120e0-104">Defines a source document.</span></span> <span data-ttu-id="120e0-105">Идентификаторы GUID предоставляются для известных языков, поставщиков и типов документов.</span><span class="sxs-lookup"><span data-stu-id="120e0-105">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="120e0-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="120e0-106">Syntax</span></span>  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="120e0-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="120e0-107">Parameters</span></span>  

 `url`  
 <span data-ttu-id="120e0-108">окне Указатель на объект `WCHAR` , который определяет универсальный указатель ресурсов (URL-адрес), определяющий документ.</span><span class="sxs-lookup"><span data-stu-id="120e0-108">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="120e0-109">окне Указатель на идентификатор GUID, определяющий язык документа.</span><span class="sxs-lookup"><span data-stu-id="120e0-109">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="120e0-110">окне Указатель на идентификатор GUID, определяющий удостоверение поставщика для языка документа.</span><span class="sxs-lookup"><span data-stu-id="120e0-110">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="120e0-111">окне Указатель на идентификатор GUID, определяющий тип документа.</span><span class="sxs-lookup"><span data-stu-id="120e0-111">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="120e0-112">заполняет Указатель на возвращаемый интерфейс [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="120e0-112">[out] A pointer to the returned [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="120e0-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="120e0-113">Return Value</span></span>  

 <span data-ttu-id="120e0-114">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="120e0-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="120e0-115">Требования</span><span class="sxs-lookup"><span data-stu-id="120e0-115">Requirements</span></span>  

 <span data-ttu-id="120e0-116">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="120e0-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="120e0-117">См. также</span><span class="sxs-lookup"><span data-stu-id="120e0-117">See also</span></span>

- [<span data-ttu-id="120e0-118">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="120e0-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
