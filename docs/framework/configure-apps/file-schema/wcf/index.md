---
description: Дополнительные сведения о схеме конфигурации WCF
title: Схем конфигурации WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 31307fd299cc1e0b63d92b43b33aabafa28858f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725770"
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="1c26b-103">Схем конфигурации WCF</span><span class="sxs-lookup"><span data-stu-id="1c26b-103">WCF Configuration Schema</span></span>

<span data-ttu-id="1c26b-104">Элементы конфигурации Windows Communication Foundation (WCF) позволяют настроить службу WCF и клиентские приложения.</span><span class="sxs-lookup"><span data-stu-id="1c26b-104">Windows Communication Foundation (WCF) configuration elements enable you to configure WCF service and client applications.</span></span> <span data-ttu-id="1c26b-105">[Средство редактирования конфигурации (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) можно использовать для создания и изменения файлов конфигурации для клиентов и служб.</span><span class="sxs-lookup"><span data-stu-id="1c26b-105">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="1c26b-106">Поскольку файлы конфигурации имеют формат XML, для их изменения вручную с помощью текстового редактора необходимо уметь работать с XML-кодом.</span><span class="sxs-lookup"><span data-stu-id="1c26b-106">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="1c26b-107">В противном случае возможно возникновение проблем, таких как отсутствие тега или атрибута элемента XML.</span><span class="sxs-lookup"><span data-stu-id="1c26b-107">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="1c26b-108">Это обусловлено тем, что в тегах и атрибутах элементов XML учитывается регистр символов.</span><span class="sxs-lookup"><span data-stu-id="1c26b-108">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="1c26b-109">Система конфигурации WCF основана на <xref:System.Configuration> пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="1c26b-109">The WCF configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="1c26b-110">Поэтому можно использовать все стандартные возможности, имеющиеся в пространстве имен <xref:System.Configuration>, например блокировку, шифрование и объединение конфигурации для повышения безопасности приложения и его конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1c26b-110">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="1c26b-111">Дополнительные сведения об этих возможностях см. в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="1c26b-111">For more information on these concepts, see the following topics.</span></span>  
  
 <span data-ttu-id="1c26b-112">[Шифрование данных конфигурации](/previous-versions/aspnet/53tyfkaw(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1c26b-112">[Encrypting Configuration Information](/previous-versions/aspnet/53tyfkaw(v=vs.100))</span></span>  
  
 <span data-ttu-id="1c26b-113">[Блокировка параметров конфигурации](/previous-versions/aspnet/55th21y4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1c26b-113">[Locking Configuration Settings](/previous-versions/aspnet/55th21y4(v=vs.100))</span></span>  
  
 <span data-ttu-id="1c26b-114">В этом разделе описаны все возможные значения каждого элемента конфигурации и их взаимодействие с другими элементами конфигурации WCF.</span><span class="sxs-lookup"><span data-stu-id="1c26b-114">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="1c26b-115">Следующая схема иллюстрирует схему конфигурации WCF:</span><span class="sxs-lookup"><span data-stu-id="1c26b-115">The following map illustrates the WCF configuration schema:</span></span>

:::image type="content" source="./media/index/windows-communication-foundation-configuration-schema.gif" alt-text="Схема, на которой показана схема конфигурации WCF." lightbox="./media/index/windows-communication-foundation-configuration-schema.gif":::
  
> [!CAUTION]
> <span data-ttu-id="1c26b-117">Защитите разделы конфигурации WCF в файлах конфигурации приложения (app.config) с соответствующими списками управления доступом (ACL), чтобы предотвратить потенциальные угрозы безопасности.</span><span class="sxs-lookup"><span data-stu-id="1c26b-117">Protect WCF configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span> <span data-ttu-id="1c26b-118">Например, убедитесь, что доступ или изменение параметров безопасности для привязок приложений разрешено только соответствующим пользователям, или раздел Service Model файла конфигурации для службы.</span><span class="sxs-lookup"><span data-stu-id="1c26b-118">For example, make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c26b-119">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="1c26b-119">In This Section</span></span>  

 [\<system.serviceModel>](system-servicemodel.md)  
 <span data-ttu-id="1c26b-120">Приводится описание элемента `ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="1c26b-120">Describes the `ServiceModel` element.</span></span>  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 <span data-ttu-id="1c26b-121">Настраивает средство SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="1c26b-121">Configures the SMSvcHost.exe tool.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
 <span data-ttu-id="1c26b-122">Элемент верхнего уровня для установки параметров при использовании сериализаторов, таких как <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1c26b-122">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1c26b-123">См. также</span><span class="sxs-lookup"><span data-stu-id="1c26b-123">Related Sections</span></span>  

 [<span data-ttu-id="1c26b-124">Configuring Windows Communication Foundation Applications</span><span class="sxs-lookup"><span data-stu-id="1c26b-124">Configuring Windows Communication Foundation Applications</span></span>](../../../wcf/configuring-services.md)  
 <span data-ttu-id="1c26b-125">Описывает настройку служб и клиентов WCF.</span><span class="sxs-lookup"><span data-stu-id="1c26b-125">Describes how to configure WCF services and clients.</span></span>
