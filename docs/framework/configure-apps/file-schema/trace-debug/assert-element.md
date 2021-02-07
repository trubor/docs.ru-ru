---
description: 'Дополнительные сведения о: <assert> element'
title: Элемент <assert>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: ce8000b30569d0e5ce47a77fbccd4bec833bb5be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725991"
---
# <a name="assert-element"></a><span data-ttu-id="c4e95-103">Элемент \<assert></span><span class="sxs-lookup"><span data-stu-id="c4e95-103">\<assert> Element</span></span>

<span data-ttu-id="c4e95-104">Определяет, должно ли выводиться окно сообщения при вызове метода <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>. Кроме того, задает имя файла, в который записываются сообщения.</span><span class="sxs-lookup"><span data-stu-id="c4e95-104">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**

## <a name="syntax"></a><span data-ttu-id="c4e95-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c4e95-105">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4e95-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="c4e95-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c4e95-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="c4e95-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4e95-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c4e95-108">Attributes</span></span>  
  
|<span data-ttu-id="c4e95-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="c4e95-109">Attribute</span></span>|<span data-ttu-id="c4e95-110">Описание</span><span class="sxs-lookup"><span data-stu-id="c4e95-110">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="c4e95-111">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="c4e95-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c4e95-112">Указывает, следует ли отображать окно сообщения, если метод **Debug. Assert** возвращает **значение false**.</span><span class="sxs-lookup"><span data-stu-id="c4e95-112">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="c4e95-113">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="c4e95-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c4e95-114">Указывает имя файла, в который будет записано сообщение, если **Debug. Assert** имеет значение **false**.</span><span class="sxs-lookup"><span data-stu-id="c4e95-114">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="c4e95-115">Атрибут ассертуиенаблед</span><span class="sxs-lookup"><span data-stu-id="c4e95-115">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="c4e95-116">Значение</span><span class="sxs-lookup"><span data-stu-id="c4e95-116">Value</span></span>|<span data-ttu-id="c4e95-117">Описание</span><span class="sxs-lookup"><span data-stu-id="c4e95-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="c4e95-118">Отображает окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="c4e95-118">Displays the message box.</span></span> <span data-ttu-id="c4e95-119">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c4e95-119">This is the default.</span></span>|  
|`false`|<span data-ttu-id="c4e95-120">Не отображает окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="c4e95-120">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4e95-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c4e95-121">Child Elements</span></span>  

 <span data-ttu-id="c4e95-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="c4e95-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4e95-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c4e95-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c4e95-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="c4e95-124">Element</span></span>|<span data-ttu-id="c4e95-125">Описание</span><span class="sxs-lookup"><span data-stu-id="c4e95-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c4e95-126">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4e95-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c4e95-127">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="c4e95-127">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4e95-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="c4e95-128">Remarks</span></span>  

 <span data-ttu-id="c4e95-129">Оба атрибута в **\<assert>** элементе являются необязательными.</span><span class="sxs-lookup"><span data-stu-id="c4e95-129">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="c4e95-130">Можно отключить окна сообщений, не указывая файл для записи в него, или указать файл для записи сообщений при включении входящих в него окон сообщений.</span><span class="sxs-lookup"><span data-stu-id="c4e95-130">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4e95-131">Пример</span><span class="sxs-lookup"><span data-stu-id="c4e95-131">Example</span></span>  

 <span data-ttu-id="c4e95-132">В следующем примере показано, как отключить отображение окон сообщений при вызове **Debug. Assert** и записи сообщений в `c:\log.txt` .</span><span class="sxs-lookup"><span data-stu-id="c4e95-132">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4e95-133">См. также</span><span class="sxs-lookup"><span data-stu-id="c4e95-133">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="c4e95-134">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="c4e95-134">Trace and Debug Settings Schema</span></span>](index.md)
