---
title: Настройка перенаправления привязки сборок
description: Узнайте, как настроить перенаправления привязки сборок в .NET с помощью атрибута appliesTo в элементе assemblyBinding файла конфигурации приложения.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: 2455cab19132a208fb99454d4131363a624315c5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236381"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="da994-103">Настройка перенаправления привязки сборок</span><span class="sxs-lookup"><span data-stu-id="da994-103">Configuring Assembly Binding Redirection</span></span>

<span data-ttu-id="da994-104">По умолчанию приложение использует набор сборок .NET Framework, поставляемых вместе с версией среды выполнения, которая использовалась для компиляции приложения.</span><span class="sxs-lookup"><span data-stu-id="da994-104">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="da994-105">Чтобы перенаправить ссылки привязки сборок на определенную версию сборок .NET Framework, можно использовать атрибут **appliesTo** элемента [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="da994-105">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="da994-106">Этот необязательный атрибут содержит номер версии .NET Framework, к которой применяется перенаправление.</span><span class="sxs-lookup"><span data-stu-id="da994-106">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="da994-107">Если атрибут **appliesTo** не указан, элемент **\<assemblyBinding>** применяется ко всем версиям платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da994-107">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="da994-108">Атрибут **appliesTo** появился в .NET Framework 1.1; он игнорируется в .NET Framework 1.0.</span><span class="sxs-lookup"><span data-stu-id="da994-108">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="da994-109">Это означает, что при использовании платформы .NET Framework версии 1.0 применяются все элементы **\<assemblyBinding>** , даже если атрибут **appliesTo** задан.</span><span class="sxs-lookup"><span data-stu-id="da994-109">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da994-110">Используйте атрибут **appliesTo**, чтобы ограничить перенаправление привязки сборки лишь определенной версией среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="da994-110">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="da994-111">Например, чтобы перенаправить привязку сборки .NET Framework версии 1.0, следует включить в файл конфигурации приложения приведенный ниже код XML.</span><span class="sxs-lookup"><span data-stu-id="da994-111">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="da994-112">В элементах **\<assemblyBinding>** учитывается порядок сортировки.</span><span class="sxs-lookup"><span data-stu-id="da994-112">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="da994-113">Сначала следует вводить сведения о перенаправлении привязок для сборок .NET Framework версии 1.0, а затем для сборок .NET Framework версии 1.1.</span><span class="sxs-lookup"><span data-stu-id="da994-113">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="da994-114">И только после этого вводятся сведения о перенаправлении привязок для любых перенаправлений сборок .NET Framework, которые не используют атрибут **appliesTo** и поэтому применимы ко всем версиям .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da994-114">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="da994-115">В случае конфликта перенаправления используется первый подходящий оператор перенаправления в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="da994-115">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="da994-116">Например, чтобы перенаправить одну ссылку на сборку .NET Framework 1.0, а другую ссылку — на сборку .NET Framework 1.1, можно использовать шаблон, показанный в псевдокоде ниже.</span><span class="sxs-lookup"><span data-stu-id="da994-116">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">
  <!-- .NET Framework version 1.0 redirects here. -->
</assemblyBinding>
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">
  <!-- .NET Framework version 1.1 redirects here. -->
</assemblyBinding>
  
<assemblyBinding xmlns="...">
  <!-- Redirects meant for all versions of the .NET Framework. -->
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="da994-117">Отладка файлов конфигурации</span><span class="sxs-lookup"><span data-stu-id="da994-117">Debugging Configuration File Errors</span></span>  

 <span data-ttu-id="da994-118">Среда выполнения анализирует файлы конфигурации один раз при создании домена приложения и загружает код в этот домен.</span><span class="sxs-lookup"><span data-stu-id="da994-118">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="da994-119">Среда CLR обрабатывает ошибки в файле конфигурации, игнорируя данную запись.</span><span class="sxs-lookup"><span data-stu-id="da994-119">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="da994-120">Среда выполнения игнорирует весь файл конфигурации, если он содержит неправильный код XML.</span><span class="sxs-lookup"><span data-stu-id="da994-120">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="da994-121">Что касается недопустимого кода XML, игнорируются только недопустимые разделы.</span><span class="sxs-lookup"><span data-stu-id="da994-121">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="da994-122">Чтобы определить, используется ли файл конфигурации, можно проверить, происходит ли перенаправление привязки сборки.</span><span class="sxs-lookup"><span data-stu-id="da994-122">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="da994-123">Чтобы узнать, какие сборки загружаются, используйте [средство просмотра журнала привязки сборок (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="da994-123">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="da994-124">Чтобы просмотреть все привязки сборок, необходимо создать запись для параметра **ForceLog** в реестре.</span><span class="sxs-lookup"><span data-stu-id="da994-124">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da994-125">См. также</span><span class="sxs-lookup"><span data-stu-id="da994-125">See also</span></span>

- [<span data-ttu-id="da994-126">Практическое руководство. Включение и отключение автоматического перенаправления привязки</span><span class="sxs-lookup"><span data-stu-id="da994-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
