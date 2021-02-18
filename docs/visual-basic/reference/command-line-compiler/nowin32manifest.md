---
description: 'Дополнительные сведения: -nowin32manifest (Visual Basic)'
title: -nowin32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: 3aa07ee26e47d48da69f1d1b34c8ec4643b7422e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426724"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="b7d86-103">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7d86-103">-nowin32manifest (Visual Basic)</span></span>

<span data-ttu-id="b7d86-104">Указывает компилятору не внедрять манифест приложения в исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="b7d86-104">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7d86-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b7d86-105">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="b7d86-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="b7d86-106">Remarks</span></span>  

 <span data-ttu-id="b7d86-107">При использовании этого параметра приложение будет подлежать виртуализации в Windows Vista, если манифест приложения не будет предоставлен в файле ресурсов Win32 или на более поздних этапах сборки.</span><span class="sxs-lookup"><span data-stu-id="b7d86-107">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="b7d86-108">Дополнительные сведения о виртуализации см. в статье [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista) (Развертывание ClickOnce в Windows Vista).</span><span class="sxs-lookup"><span data-stu-id="b7d86-108">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="b7d86-109">Дополнительные сведения о создании манифестов см. в разделе [-win32manifest (Visual Basic)](win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="b7d86-109">For more information about manifest creation, see [-win32manifest (Visual Basic)](win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d86-110">См. также</span><span class="sxs-lookup"><span data-stu-id="b7d86-110">See also</span></span>

- [<span data-ttu-id="b7d86-111">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="b7d86-111">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b7d86-112">Страница "Приложение" в конструкторе проектов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7d86-112">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
