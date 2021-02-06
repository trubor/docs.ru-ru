---
description: 'Дополнительные сведения о: My. Resources'
title: Объект My.Resources
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: ecd8e79aacea85080dc341ae36b362a595893034
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640632"
---
# <a name="myresources-object"></a><span data-ttu-id="e84e0-103">Объект My.Resources</span><span class="sxs-lookup"><span data-stu-id="e84e0-103">My.Resources Object</span></span>

<span data-ttu-id="e84e0-104">Предоставляет свойства и классы для доступа к ресурсам приложения.</span><span class="sxs-lookup"><span data-stu-id="e84e0-104">Provides properties and classes for accessing the application's resources.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e84e0-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="e84e0-105">Remarks</span></span>  

 <span data-ttu-id="e84e0-106">`My.Resources`Объект предоставляет доступ к ресурсам приложения и позволяет динамически получать ресурсы для приложения.</span><span class="sxs-lookup"><span data-stu-id="e84e0-106">The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application.</span></span> <span data-ttu-id="e84e0-107">Дополнительные сведения см. в разделе [Управление ресурсами приложения (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="e84e0-107">For more information, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
 <span data-ttu-id="e84e0-108">Объект `My.Resources` предоставляет только глобальные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="e84e0-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="e84e0-109">Он не предоставляет доступ к файлам ресурсов, связанным с формами.</span><span class="sxs-lookup"><span data-stu-id="e84e0-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="e84e0-110">Вам нужно получить доступ к ресурсам формы из формы.</span><span class="sxs-lookup"><span data-stu-id="e84e0-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="e84e0-111">Доступ к файлам ресурсов для конкретного языка и региональных параметров приложения можно получить из `My.Resources` объекта.</span><span class="sxs-lookup"><span data-stu-id="e84e0-111">You can access the application's culture-specific resource files from the `My.Resources` object.</span></span> <span data-ttu-id="e84e0-112">По умолчанию `My.Resources` объект ищет ресурсы из файла ресурсов, соответствующие языку и региональным параметрам в <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> свойстве.</span><span class="sxs-lookup"><span data-stu-id="e84e0-112">By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property.</span></span> <span data-ttu-id="e84e0-113">Однако это поведение можно переопределить и указать конкретный язык и региональные параметры, которые будут использоваться для ресурсов.</span><span class="sxs-lookup"><span data-stu-id="e84e0-113">However, you can override this behavior and specify a particular culture to use for the resources.</span></span> <span data-ttu-id="e84e0-114">Дополнительные сведения см. в разделе [Ресурсы в приложениях для настольных систем](../../../framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="e84e0-114">For more information, see [Resources in Desktop Apps](../../../framework/resources/index.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e84e0-115">Свойства</span><span class="sxs-lookup"><span data-stu-id="e84e0-115">Properties</span></span>  

 <span data-ttu-id="e84e0-116">Свойства `My.Resources` объекта предоставляют доступ только для чтения к ресурсам приложения.</span><span class="sxs-lookup"><span data-stu-id="e84e0-116">The properties of the `My.Resources` object provide read-only access to your application's resources.</span></span> <span data-ttu-id="e84e0-117">Чтобы добавить или удалить ресурсы, используйте **Конструктор проектов**.</span><span class="sxs-lookup"><span data-stu-id="e84e0-117">To add or remove resources, use the **Project Designer**.</span></span> <span data-ttu-id="e84e0-118">Доступ к ресурсам, добавленным с помощью **конструктора проектов** , можно получить с помощью `My.Resources.` *resourceName*.</span><span class="sxs-lookup"><span data-stu-id="e84e0-118">You can access resources added through the **Project Designer** by using `My.Resources.`*resourceName*.</span></span>  
  
 <span data-ttu-id="e84e0-119">Можно также добавлять или удалять файлы ресурсов, выбрав проект в **Обозреватель решений** и выбрав пункт **Добавить новый элемент** или **Добавить существующий элемент** в меню **проект** .</span><span class="sxs-lookup"><span data-stu-id="e84e0-119">You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu.</span></span> <span data-ttu-id="e84e0-120">Доступ к ресурсам, добавленным таким способом, можно получить с помощью `My.Resources.` *ресаурцефиленаме* `.` *resourceName*.</span><span class="sxs-lookup"><span data-stu-id="e84e0-120">You can access resources added in this manner by using `My.Resources.`*resourceFileName*`.`*resourceName*.</span></span>  
  
 <span data-ttu-id="e84e0-121">Каждый ресурс имеет имя, категорию и значение, и эти параметры ресурсов определяют, как свойство для доступа к ресурсу отображается в `My.Resources` объекте.</span><span class="sxs-lookup"><span data-stu-id="e84e0-121">Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object.</span></span> <span data-ttu-id="e84e0-122">Для ресурсов, добавленных в **конструкторе проектов**:</span><span class="sxs-lookup"><span data-stu-id="e84e0-122">For resources added in the **Project Designer**:</span></span>  
  
- <span data-ttu-id="e84e0-123">Имя определяет имя свойства,</span><span class="sxs-lookup"><span data-stu-id="e84e0-123">The name determines the name of the property,</span></span>  
  
- <span data-ttu-id="e84e0-124">Данные ресурса являются значением свойства,</span><span class="sxs-lookup"><span data-stu-id="e84e0-124">The resource data is the value of the property,</span></span>  
  
- <span data-ttu-id="e84e0-125">Категория определяет тип свойства:</span><span class="sxs-lookup"><span data-stu-id="e84e0-125">The category determines the type of the property:</span></span>  
  
|<span data-ttu-id="e84e0-126">Категория</span><span class="sxs-lookup"><span data-stu-id="e84e0-126">Category</span></span>|<span data-ttu-id="e84e0-127">Тип данных свойства</span><span class="sxs-lookup"><span data-stu-id="e84e0-127">Property data type</span></span>|  
|---|---|  
|<span data-ttu-id="e84e0-128">**Строки**</span><span class="sxs-lookup"><span data-stu-id="e84e0-128">**Strings**</span></span>|[<span data-ttu-id="e84e0-129">String</span><span class="sxs-lookup"><span data-stu-id="e84e0-129">String</span></span>](../data-types/string-data-type.md)|  
|<span data-ttu-id="e84e0-130">**Изображения**</span><span class="sxs-lookup"><span data-stu-id="e84e0-130">**Images**</span></span>|<xref:System.Drawing.Bitmap>|  
|<span data-ttu-id="e84e0-131">**Значки**</span><span class="sxs-lookup"><span data-stu-id="e84e0-131">**Icons**</span></span>|<xref:System.Drawing.Icon>|  
|<span data-ttu-id="e84e0-132">**звук;**</span><span class="sxs-lookup"><span data-stu-id="e84e0-132">**Audio**</span></span>|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <span data-ttu-id="e84e0-133"><xref:System.IO.UnmanagedMemoryStream>Класс является производным от <xref:System.IO.Stream> класса, поэтому его можно использовать с методами, принимающими потоки, например <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="e84e0-133">The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.</span></span>|  
|<span data-ttu-id="e84e0-134">**Файлы**</span><span class="sxs-lookup"><span data-stu-id="e84e0-134">**Files**</span></span>|<span data-ttu-id="e84e0-135">-   [Строка](../data-types/string-data-type.md) для текстовых файлов.</span><span class="sxs-lookup"><span data-stu-id="e84e0-135">-   [String](../data-types/string-data-type.md) for text files.</span></span><br /><span data-ttu-id="e84e0-136">-   <xref:System.Drawing.Bitmap> для файлов изображений.</span><span class="sxs-lookup"><span data-stu-id="e84e0-136">-   <xref:System.Drawing.Bitmap> for image files.</span></span><br /><span data-ttu-id="e84e0-137">-   <xref:System.Drawing.Icon> для файлов значков.</span><span class="sxs-lookup"><span data-stu-id="e84e0-137">-   <xref:System.Drawing.Icon> for icon files.</span></span><br /><span data-ttu-id="e84e0-138">-   <xref:System.IO.UnmanagedMemoryStream> для звуковых файлов.</span><span class="sxs-lookup"><span data-stu-id="e84e0-138">-   <xref:System.IO.UnmanagedMemoryStream> for sound files.</span></span>|  
|<span data-ttu-id="e84e0-139">**Другое**</span><span class="sxs-lookup"><span data-stu-id="e84e0-139">**Other**</span></span>|<span data-ttu-id="e84e0-140">Определяется сведениями в столбце **типа** конструктора.</span><span class="sxs-lookup"><span data-stu-id="e84e0-140">Determined by the information in the designer's **Type** column.</span></span>|  
  
## <a name="classes"></a><span data-ttu-id="e84e0-141">Классы</span><span class="sxs-lookup"><span data-stu-id="e84e0-141">Classes</span></span>  

 <span data-ttu-id="e84e0-142">`My.Resources`Объект предоставляет каждый файл ресурсов как класс с общими свойствами.</span><span class="sxs-lookup"><span data-stu-id="e84e0-142">The `My.Resources` object exposes each resource file as a class with shared properties.</span></span> <span data-ttu-id="e84e0-143">Имя класса совпадает с именем файла ресурсов.</span><span class="sxs-lookup"><span data-stu-id="e84e0-143">The class name is the same as the name of the resource file.</span></span> <span data-ttu-id="e84e0-144">Как описано в предыдущем разделе, ресурсы в файле ресурсов предоставляются как свойства в классе.</span><span class="sxs-lookup"><span data-stu-id="e84e0-144">As described in the previous section, the resources in a resource file are exposed as properties in the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e84e0-145">Пример</span><span class="sxs-lookup"><span data-stu-id="e84e0-145">Example</span></span>  

 <span data-ttu-id="e84e0-146">В этом примере задается заголовок формы в виде строкового ресурса, указанного `Form1Title` в файле ресурсов приложения.</span><span class="sxs-lookup"><span data-stu-id="e84e0-146">This example sets the title of a form to the string resource named `Form1Title` in the application resource file.</span></span> <span data-ttu-id="e84e0-147">Чтобы пример работал, приложение должно иметь строку с именем `Form1Title` в файле ресурсов.</span><span class="sxs-lookup"><span data-stu-id="e84e0-147">For the example to work, the application must have a string named `Form1Title` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="e84e0-148">Пример</span><span class="sxs-lookup"><span data-stu-id="e84e0-148">Example</span></span>  

 <span data-ttu-id="e84e0-149">В этом примере значок формы задается значком с именем `Form1Icon` , который хранится в файле ресурсов приложения.</span><span class="sxs-lookup"><span data-stu-id="e84e0-149">This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file.</span></span> <span data-ttu-id="e84e0-150">Чтобы пример работал, приложение должно иметь `Form1Icon` в своем файле ресурсов значок с именем.</span><span class="sxs-lookup"><span data-stu-id="e84e0-150">For the example to work, the application must have an icon named `Form1Icon` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="e84e0-151">Пример</span><span class="sxs-lookup"><span data-stu-id="e84e0-151">Example</span></span>  

 <span data-ttu-id="e84e0-152">В этом примере для фонового изображения формы задается ресурс изображения с именем `Form1Background` , который находится в файле ресурсов приложения.</span><span class="sxs-lookup"><span data-stu-id="e84e0-152">This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file.</span></span> <span data-ttu-id="e84e0-153">Чтобы этот пример работал, приложение должно иметь ресурс образа с именем `Form1Background` в файле ресурсов.</span><span class="sxs-lookup"><span data-stu-id="e84e0-153">For this example to work, the application must have an image resource named `Form1Background` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="e84e0-154">Пример</span><span class="sxs-lookup"><span data-stu-id="e84e0-154">Example</span></span>  

 <span data-ttu-id="e84e0-155">В этом примере воспроизводится звук, который хранится в виде звукового ресурса `Form1Greeting` в файле ресурсов приложения.</span><span class="sxs-lookup"><span data-stu-id="e84e0-155">This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file.</span></span> <span data-ttu-id="e84e0-156">Чтобы пример работал, в файле ресурсов приложения должен быть указан звуковой ресурс `Form1Greeting` .</span><span class="sxs-lookup"><span data-stu-id="e84e0-156">For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file.</span></span> <span data-ttu-id="e84e0-157">`My.Computer.Audio.Play`Метод доступен только для приложений Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e84e0-157">The `My.Computer.Audio.Play` method is available only for Windows Forms applications.</span></span>  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="e84e0-158">Пример</span><span class="sxs-lookup"><span data-stu-id="e84e0-158">Example</span></span>  

 <span data-ttu-id="e84e0-159">В этом примере извлекается версия строкового ресурса приложения на французском языке.</span><span class="sxs-lookup"><span data-stu-id="e84e0-159">This example retrieves the French-culture version of a  string resource of the application.</span></span> <span data-ttu-id="e84e0-160">Ресурс называется `Message` .</span><span class="sxs-lookup"><span data-stu-id="e84e0-160">The resource is named `Message`.</span></span> <span data-ttu-id="e84e0-161">Для изменения языка и региональных параметров, `My.Resources` используемых объектом, в примере используется <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A> .</span><span class="sxs-lookup"><span data-stu-id="e84e0-161">To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span></span>  
  
 <span data-ttu-id="e84e0-162">Для работы этого примера приложение должно иметь строку с именем `Message` в файле ресурсов, а приложение должно иметь версию файла ресурсов для французского языка и региональных параметров Resources.fr-FR. resx.</span><span class="sxs-lookup"><span data-stu-id="e84e0-162">For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx.</span></span> <span data-ttu-id="e84e0-163">Если приложение не имеет версию файла ресурсов для французского языка и региональных параметров, `My.Resource` объект получает ресурс из файла ресурсов языка и региональных параметров по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e84e0-163">If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="e84e0-164">См. также</span><span class="sxs-lookup"><span data-stu-id="e84e0-164">See also</span></span>

- [<span data-ttu-id="e84e0-165">Управление ресурсами приложения (.NET)</span><span class="sxs-lookup"><span data-stu-id="e84e0-165">Managing Application Resources (.NET)</span></span>](/visualstudio/ide/managing-application-resources-dotnet)
- [<span data-ttu-id="e84e0-166">Ресурсы в приложениях для настольных систем</span><span class="sxs-lookup"><span data-stu-id="e84e0-166">Resources in Desktop Apps</span></span>](../../../framework/resources/index.md)
