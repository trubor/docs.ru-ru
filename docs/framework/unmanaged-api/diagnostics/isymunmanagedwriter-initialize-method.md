---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: Initialize'
title: Метод ISymUnmanagedWriter::Initialize
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
ms.openlocfilehash: eab60e9539df3d43a1602268d704ac324f028915
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762296"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="1ef32-103">Метод ISymUnmanagedWriter::Initialize</span><span class="sxs-lookup"><span data-stu-id="1ef32-103">ISymUnmanagedWriter::Initialize Method</span></span>

<span data-ttu-id="1ef32-104">Задает интерфейс передатчика метаданных, с которым будет связан этот модуль записи, и задает имя выходного файла, в который будут записываться отладочные символы.</span><span class="sxs-lookup"><span data-stu-id="1ef32-104">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="1ef32-105">Этот метод может быть вызван только один раз и должен вызываться перед любым другим методом записи.</span><span class="sxs-lookup"><span data-stu-id="1ef32-105">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="1ef32-106">Некоторым модулям записи может потребоваться имя файла.</span><span class="sxs-lookup"><span data-stu-id="1ef32-106">Some writers may require a file name.</span></span> <span data-ttu-id="1ef32-107">Однако всегда можно передать имя файла этому методу без какого-либо негативного воздействия на модули записи, которые не используют имя файла.</span><span class="sxs-lookup"><span data-stu-id="1ef32-107">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef32-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1ef32-108">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ef32-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ef32-109">Parameters</span></span>  

 `emitter`  
 <span data-ttu-id="1ef32-110">окне Указатель на интерфейс передатчика метаданных.</span><span class="sxs-lookup"><span data-stu-id="1ef32-110">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="1ef32-111">окне Имя файла, в который записываются отладочные символы.</span><span class="sxs-lookup"><span data-stu-id="1ef32-111">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="1ef32-112">Если имя файла задано для модуля записи, который не использует имена файлов, этот параметр пропускается.</span><span class="sxs-lookup"><span data-stu-id="1ef32-112">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="1ef32-113">окне Если этот параметр указан, модуль записи символов выдает символы в заданный объект, а не в <xref:System.Runtime.InteropServices.ComTypes.IStream> файл, указанный в `filename` аргументе.</span><span class="sxs-lookup"><span data-stu-id="1ef32-113">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="1ef32-114">Параметр `pIStream` не обязателен.</span><span class="sxs-lookup"><span data-stu-id="1ef32-114">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="1ef32-115">[входные] `true` значение, если это полная перестроение; `false` если это инкрементная компиляция.</span><span class="sxs-lookup"><span data-stu-id="1ef32-115">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ef32-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1ef32-116">Return Value</span></span>  

 <span data-ttu-id="1ef32-117">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="1ef32-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ef32-118">Требования</span><span class="sxs-lookup"><span data-stu-id="1ef32-118">Requirements</span></span>  

 <span data-ttu-id="1ef32-119">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="1ef32-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef32-120">См. также</span><span class="sxs-lookup"><span data-stu-id="1ef32-120">See also</span></span>

- [<span data-ttu-id="1ef32-121">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="1ef32-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="1ef32-122">Метод Initialize2</span><span class="sxs-lookup"><span data-stu-id="1ef32-122">Initialize2 Method</span></span>](isymunmanagedwriter-initialize2-method.md)
