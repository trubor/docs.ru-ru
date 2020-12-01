---
title: Практическое руководство. Загрузка сборок в домен приложения
description: Сведения о загрузке сборок в домен приложения .NET. Рекомендуется использовать статический (или общий) метод Load класса System.Reflection.Assembly.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
ms.openlocfilehash: cc37b5b5c64a65655d06418d08a66231577a5bad
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271490"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="2619c-104">Практическое руководство. Загрузка сборок в домен приложения</span><span class="sxs-lookup"><span data-stu-id="2619c-104">How to: Load Assemblies into an Application Domain</span></span>

<span data-ttu-id="2619c-105">Существует несколько способов загрузки сборки в домен приложения.</span><span class="sxs-lookup"><span data-stu-id="2619c-105">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="2619c-106">Рекомендуется использовать метод <xref:System.Reflection.Assembly.Load%2A>`static` (`Shared` в Visual Basic) класса <xref:System.Reflection.Assembly?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2619c-106">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="2619c-107">Другими способами загрузки сборок являются:</span><span class="sxs-lookup"><span data-stu-id="2619c-107">Other ways assemblies can be loaded include:</span></span>  
  
- <span data-ttu-id="2619c-108">Метод <xref:System.Reflection.Assembly.LoadFrom%2A> класса <xref:System.Reflection.Assembly> загружает сборку, заданную расположением ее файла.</span><span class="sxs-lookup"><span data-stu-id="2619c-108">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="2619c-109">При загрузке сборок с помощью этого метода используется другой контекст загрузки.</span><span class="sxs-lookup"><span data-stu-id="2619c-109">Loading assemblies with this method uses a different load context.</span></span>  
  
- <span data-ttu-id="2619c-110">Методы <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> и <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> загружают сборку в контекст, предназначенный только для отражения.</span><span class="sxs-lookup"><span data-stu-id="2619c-110">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="2619c-111">Сборки, загруженные в этом контексте, могут быть проверены, но не выполнены, позволяя производить проверку сборок, предназначенных для других платформ.</span><span class="sxs-lookup"><span data-stu-id="2619c-111">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="2619c-112">См. практическое руководство по [ Загрузка сборок в контекст, предназначенный только для отражения](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="2619c-112">See [How to: Load Assemblies into the Reflection-Only Context](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2619c-113">Контекст только для отражения впервые появился в платформе .NET Framework версии 2.0.</span><span class="sxs-lookup"><span data-stu-id="2619c-113">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
- <span data-ttu-id="2619c-114">Такие методы, как <xref:System.AppDomain.CreateInstance%2A> и <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> класса <xref:System.AppDomain> могут загружать сборки в домен приложения.</span><span class="sxs-lookup"><span data-stu-id="2619c-114">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
- <span data-ttu-id="2619c-115">Метод <xref:System.Type.GetType%2A> класса <xref:System.Type> может загружать сборки.</span><span class="sxs-lookup"><span data-stu-id="2619c-115">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
- <span data-ttu-id="2619c-116">Метод <xref:System.AppDomain.Load%2A> класса <xref:System.AppDomain?displayProperty=nameWithType> может загружать сборки, но в основном он используется для COM-взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="2619c-116">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="2619c-117">Его не следует использовать для загрузки сборок в домен приложения, отличный от домена приложения, из которого он вызывается.</span><span class="sxs-lookup"><span data-stu-id="2619c-117">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2619c-118">Начиная с платформы .NET Framework версии 2.0, среда выполнения не загружает сборки, которые были скомпилированы версиями платформы .NET Framework, чей номер версии выше, чем у текущей среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="2619c-118">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="2619c-119">Это применимо к сочетанию основного и дополнительного номеров для номера версии.</span><span class="sxs-lookup"><span data-stu-id="2619c-119">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="2619c-120">Можно определить способ, которым JIT-скомпилированный код из загруженных сборок будет распределен между доменами приложений.</span><span class="sxs-lookup"><span data-stu-id="2619c-120">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="2619c-121">Дополнительные сведения см. в статье [Домены приложений и сборки](application-domains.md#application-domains-and-assemblies).</span><span class="sxs-lookup"><span data-stu-id="2619c-121">For more information, see [Application domains and assemblies](application-domains.md#application-domains-and-assemblies).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2619c-122">Пример</span><span class="sxs-lookup"><span data-stu-id="2619c-122">Example</span></span>  

 <span data-ttu-id="2619c-123">Следующий код загружает сборку с именем "example.exe" или "example.dll" в текущий домен приложения, получает тип с именем `Example` из сборки, получает метод без параметров `MethodA` для этого типа и выполняет этот метод.</span><span class="sxs-lookup"><span data-stu-id="2619c-123">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="2619c-124">Полное описание получения сведений из загруженной сборки см. в разделе [Динамическая загрузка и использование типов](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="2619c-124">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2619c-125">См. также</span><span class="sxs-lookup"><span data-stu-id="2619c-125">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="2619c-126">Программирование с использованием доменов приложений</span><span class="sxs-lookup"><span data-stu-id="2619c-126">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="2619c-127">Отражение</span><span class="sxs-lookup"><span data-stu-id="2619c-127">Reflection</span></span>](../reflection-and-codedom/reflection.md)
- [<span data-ttu-id="2619c-128">Использование доменов приложений</span><span class="sxs-lookup"><span data-stu-id="2619c-128">Using Application Domains</span></span>](use.md)
- [<span data-ttu-id="2619c-129">Практическое руководство. Загрузка сборок в контекст, предназначенный только для отражения</span><span class="sxs-lookup"><span data-stu-id="2619c-129">How to: Load Assemblies into the Reflection-Only Context</span></span>](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [<span data-ttu-id="2619c-130">Домены приложений и сборки</span><span class="sxs-lookup"><span data-stu-id="2619c-130">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
