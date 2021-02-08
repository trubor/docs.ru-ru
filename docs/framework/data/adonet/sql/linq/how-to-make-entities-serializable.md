---
description: Дополнительные сведения см. в статье как сделать сущности сериализуемыми.
title: Практическое руководство. Как обеспечить сериализации сущностей
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: cb2253d7933f3584543b4b030bc8b5aa3cc62921
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785943"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="f2530-103">Практическое руководство. Как обеспечить сериализации сущностей</span><span class="sxs-lookup"><span data-stu-id="f2530-103">How to: Make Entities Serializable</span></span>

<span data-ttu-id="f2530-104">Возможность сериализации сущностей можно обеспечить при создании кода.</span><span class="sxs-lookup"><span data-stu-id="f2530-104">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="f2530-105">К классам сущностей добавляется атрибут <xref:System.Runtime.Serialization.DataContractAttribute>, а к столбцам - атрибут <xref:System.Runtime.Serialization.DataMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f2530-105">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="f2530-106">Разработчики, использующие Visual Studio, могут использовать реляционный конструктор объектов для этой цели.</span><span class="sxs-lookup"><span data-stu-id="f2530-106">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="f2530-107">При использовании программы командной строки SQLMetal используйте параметр **/Serialization** с `unidirectional` аргументом.</span><span class="sxs-lookup"><span data-stu-id="f2530-107">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="f2530-108">Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="f2530-108">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2530-109">Пример</span><span class="sxs-lookup"><span data-stu-id="f2530-109">Example</span></span>  

 <span data-ttu-id="f2530-110">В следующих командах средства командной строки SQLMetal создают файлы, содержащие сериализуемые сущности.</span><span class="sxs-lookup"><span data-stu-id="f2530-110">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2530-111">См. также</span><span class="sxs-lookup"><span data-stu-id="f2530-111">See also</span></span>

- [<span data-ttu-id="f2530-112">Сериализация</span><span class="sxs-lookup"><span data-stu-id="f2530-112">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="f2530-113">Создание модели объектов</span><span class="sxs-lookup"><span data-stu-id="f2530-113">Creating the Object Model</span></span>](creating-the-object-model.md)
