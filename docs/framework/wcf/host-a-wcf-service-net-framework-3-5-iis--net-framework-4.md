---
description: Дополнительные сведения о том, как разместить службу WCF, написанную с помощью платформа .NET Framework 3,5, в службах IIS, работающих под платформа .NET Framework 4
title: Практическое руководство. Размещение службы WCF, написанной для.NET Framework 3.5 в IIS, которая работает в .NET Framework 4
ms.date: 03/30/2017
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
ms.openlocfilehash: 3ea46b589df293b39369521a133cf9facad97d93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755971"
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a><span data-ttu-id="4ea80-103">Практическое руководство. Размещение службы WCF, написанной для.NET Framework 3.5 в IIS, которая работает в .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="4ea80-103">How to: Host a WCF Service Written with .NET Framework 3.5 in IIS Running Under .NET Framework 4</span></span>

<span data-ttu-id="4ea80-104">При размещении службы Windows Communication Foundation (WCF), написанной с платформа .NET Framework 3,5 на компьютере с платформа .NET Framework 4, вы можете получить <xref:System.ServiceModel.ProtocolException> со следующим текстом.</span><span class="sxs-lookup"><span data-stu-id="4ea80-104">When hosting a Windows Communication Foundation (WCF) service written with .NET Framework 3.5 on a machine running .NET Framework 4, you may get a <xref:System.ServiceModel.ProtocolException> with the following text.</span></span>
  
```output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 <span data-ttu-id="4ea80-105">При попытке перехода к SVC-файлу службы может отобразиться страница ошибки со следующим текстом.</span><span class="sxs-lookup"><span data-stu-id="4ea80-105">Or if you try to browse to the service's .svc file you may see an error page with the following text.</span></span>  
  
```output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 <span data-ttu-id="4ea80-106">Эти ошибки возникают из-за того, что домен приложения IIS запущен в среде платформа .NET Framework 4, а служба WCF ожидает запуска от имени платформа .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="4ea80-106">These errors occur because the application domain IIS is running within is running .NET Framework 4 and the WCF service is expecting to run under .NET Framework 3.5.</span></span> <span data-ttu-id="4ea80-107">В этом разделе описываются изменения, которые необходимо выполнить для запуска службы.</span><span class="sxs-lookup"><span data-stu-id="4ea80-107">This topic explains the modifications required to get the service to run.</span></span>
  
 <span data-ttu-id="4ea80-108">Затем найдите `compilers` элемент> <и измените значение параметра Поставщик компилерверсион на 4,0.</span><span class="sxs-lookup"><span data-stu-id="4ea80-108">Next find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="4ea80-109">По умолчанию `compiler` в элементе> <есть два <> элементов `compilers` .</span><span class="sxs-lookup"><span data-stu-id="4ea80-109">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="4ea80-110">Необходимо обновить параметр поставщика CompilerVersion для обоих элементов, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="4ea80-110">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
```xml  
<system.codedom>  
      <compilers>  
        <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                  type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
        <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                  type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="OptionInfer" value="true"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
      </compilers>  
    </system.codedom>  
```  
  
### <a name="add-the-required-targetframework-attribute"></a><span data-ttu-id="4ea80-111">Добавьте необходимый атрибут targetFramework</span><span class="sxs-lookup"><span data-stu-id="4ea80-111">Add the required targetFramework attribute</span></span>  
  
1. <span data-ttu-id="4ea80-112">Откройте файл Web.config службы и найдите `compilation` элемент <>.</span><span class="sxs-lookup"><span data-stu-id="4ea80-112">Open the service's Web.config file and look for the <`compilation`> element.</span></span>  
  
2. <span data-ttu-id="4ea80-113">Добавьте `targetFramework` атрибут к `compilation` элементу> <, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="4ea80-113">Add the `targetFramework` attribute to the <`compilation`> element as shown in the following example.</span></span>  
  
    ```xml  
    <compilation debug="false"  
            targetFramework="4.0">  
  
            <assemblies>  
              <add assembly="System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>  
              <add assembly="System.Data.DataSetExtensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
            </assemblies>  
  
          </compilation>  
    ```  
  
3. <span data-ttu-id="4ea80-114">Найдите `compilers` элемент> <и измените параметр поставщика компилерверсион, чтобы он имел значение 4,0.</span><span class="sxs-lookup"><span data-stu-id="4ea80-114">Find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="4ea80-115">По умолчанию `compiler` в элементе> <есть два <> элементов `compilers` .</span><span class="sxs-lookup"><span data-stu-id="4ea80-115">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="4ea80-116">Необходимо обновить параметр поставщика CompilerVersion для обоих элементов, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="4ea80-116">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
    ```xml  
    <system.codedom>  
          <compilers>  
            <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                      type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
            <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                      type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="OptionInfer" value="true"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
          </compilers>  
        </system.codedom>  
    ```
