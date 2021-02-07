---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: Initialize2'
title: Метод ISymUnmanagedWriter::Initialize2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
ms.openlocfilehash: 0d4c769c9f1b571296cbfe159057df083a6d5ca6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762283"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="39483-103">Метод ISymUnmanagedWriter::Initialize2</span><span class="sxs-lookup"><span data-stu-id="39483-103">ISymUnmanagedWriter::Initialize2 Method</span></span>

<span data-ttu-id="39483-104">Задает интерфейс передатчика метаданных, с которым будет связан этот модуль записи, и задает имя выходного файла, в который будут записываться отладочные символы.</span><span class="sxs-lookup"><span data-stu-id="39483-104">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="39483-105">Этот метод также позволяет задать конечное расположение файла базы данных программы (PDB).</span><span class="sxs-lookup"><span data-stu-id="39483-105">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39483-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="39483-106">Syntax</span></span>  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39483-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="39483-107">Parameters</span></span>  

 `emitter`  
 <span data-ttu-id="39483-108">окне Указатель на интерфейс передатчика метаданных.</span><span class="sxs-lookup"><span data-stu-id="39483-108">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="39483-109">окне Указатель на объект `WCHAR` , содержащий имя файла, в который записываются отладочные символы.</span><span class="sxs-lookup"><span data-stu-id="39483-109">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="39483-110">Если имя файла задано для модуля записи, который не использует имена файлов, этот параметр пропускается.</span><span class="sxs-lookup"><span data-stu-id="39483-110">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="39483-111">окне Если указан, средство записи символов создает символы в заданном, а не в <xref:System.Runtime.InteropServices.ComTypes.IStream> файле, указанном в `filename` параметре.</span><span class="sxs-lookup"><span data-stu-id="39483-111">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="39483-112">Параметр `pIStream` не обязателен.</span><span class="sxs-lookup"><span data-stu-id="39483-112">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="39483-113">[входные] `true` значение, если это полная перестроение; `false` если это инкрементная компиляция.</span><span class="sxs-lookup"><span data-stu-id="39483-113">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="39483-114">окне Указатель на объект `WCHAR` , который является строкой пути к окончательному расположению PDB-файла.</span><span class="sxs-lookup"><span data-stu-id="39483-114">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39483-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="39483-115">Return Value</span></span>  

 <span data-ttu-id="39483-116">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="39483-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39483-117">Требования</span><span class="sxs-lookup"><span data-stu-id="39483-117">Requirements</span></span>  

 <span data-ttu-id="39483-118">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="39483-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39483-119">См. также</span><span class="sxs-lookup"><span data-stu-id="39483-119">See also</span></span>

- [<span data-ttu-id="39483-120">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="39483-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="39483-121">Метод Initialize</span><span class="sxs-lookup"><span data-stu-id="39483-121">Initialize Method</span></span>](isymunmanagedwriter-initialize-method.md)
