---
description: Дополнительные сведения см. в разделе Пошаговое руководство. Сохранение объекта в Visual Studio (Visual Basic)
title: Сохранение объекта в Visual Studio
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 4145f84d14eadae6a305a4a1f5860cdcc38450c8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486866"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="1caab-103">Пошаговое руководство. Сохранение объекта в Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1caab-103">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>

<span data-ttu-id="1caab-104">Несмотря на то, что во время разработки свойствам объекта можно задать значения по умолчанию, любые значения, введенные во время выполнения, будут потеряны при уничтожении объекта.</span><span class="sxs-lookup"><span data-stu-id="1caab-104">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="1caab-105">С помощью сериализации можно сохранить данные объекта между экземплярами, что позволит сохранять значения и извлекать их при следующем создании экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="1caab-105">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1caab-106">В Visual Basic можно использовать объект `My.Settings` для хранения простых данных, таких как имя или число.</span><span class="sxs-lookup"><span data-stu-id="1caab-106">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="1caab-107">Дополнительные сведения см. в разделе [Объект My.Settings](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="1caab-107">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="1caab-108">В этом пошаговом руководстве будет создан простой объект `Loan`, а его данные сохранены в файл.</span><span class="sxs-lookup"><span data-stu-id="1caab-108">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="1caab-109">Затем при повторном создании объекта вы получите данные из файла.</span><span class="sxs-lookup"><span data-stu-id="1caab-109">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1caab-110">В этом примере создается файл (если файл отсутствует).</span><span class="sxs-lookup"><span data-stu-id="1caab-110">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="1caab-111">Если приложение должно создать файл, ему необходимо разрешение `Create` для папки.</span><span class="sxs-lookup"><span data-stu-id="1caab-111">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="1caab-112">Для задания разрешений используются списки управления доступом.</span><span class="sxs-lookup"><span data-stu-id="1caab-112">Permissions are set by using access control lists.</span></span> <span data-ttu-id="1caab-113">Если файл уже существует, приложению требуется лишь разрешение `Write` (с более низким уровнем).</span><span class="sxs-lookup"><span data-stu-id="1caab-113">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="1caab-114">Если возможно, безопаснее создать файл во время развертывания и предоставить только разрешение `Read` для одного файла (вместо разрешения Create для папки).</span><span class="sxs-lookup"><span data-stu-id="1caab-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="1caab-115">По тем же соображениям рекомендуется записывать данные в пользовательские папки, а не в коревую папку или папку Program Files.</span><span class="sxs-lookup"><span data-stu-id="1caab-115">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1caab-116">В этом примере данные сохраняются в двоичном формате.</span><span class="sxs-lookup"><span data-stu-id="1caab-116">This example stores data in a binary.</span></span> <span data-ttu-id="1caab-117">Эти форматы не следует использовать для конфиденциальных данных, таких как пароли или сведения о кредитных картах.</span><span class="sxs-lookup"><span data-stu-id="1caab-117">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1caab-118">Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.</span><span class="sxs-lookup"><span data-stu-id="1caab-118">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1caab-119">Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** .</span><span class="sxs-lookup"><span data-stu-id="1caab-119">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1caab-120">Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="1caab-120">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="1caab-121">Создание объекта Loan</span><span class="sxs-lookup"><span data-stu-id="1caab-121">Creating the Loan Object</span></span>  

 <span data-ttu-id="1caab-122">Первым шагом является создание класса `Loan` и тестового приложения, которое использует класс.</span><span class="sxs-lookup"><span data-stu-id="1caab-122">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="1caab-123">Создание класса Loan</span><span class="sxs-lookup"><span data-stu-id="1caab-123">To create the Loan class</span></span>  
  
1. <span data-ttu-id="1caab-124">Создайте проект библиотеки классов и назовите его LoanClass.</span><span class="sxs-lookup"><span data-stu-id="1caab-124">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="1caab-125">Дополнительные сведения см. в разделе [Создание проектов и решений](/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="1caab-125">For more information, see [Creating Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2. <span data-ttu-id="1caab-126">В **обозревателе решений** щелкните правой кнопкой мыши файл Class1 и выберите команду **Переименовать**.</span><span class="sxs-lookup"><span data-stu-id="1caab-126">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="1caab-127">Измените имя файла на `Loan` и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="1caab-127">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="1caab-128">При переименовании файла класс также будет переименован в `Loan`.</span><span class="sxs-lookup"><span data-stu-id="1caab-128">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3. <span data-ttu-id="1caab-129">Добавьте в класс следующие открытые члены:</span><span class="sxs-lookup"><span data-stu-id="1caab-129">Add the following public members to the class:</span></span>  
  
    ```vb  
    Public Class Loan  
        Implements System.ComponentModel.INotifyPropertyChanged  
  
        Public Property LoanAmount As Double  
        Public Property InterestRate As Double  
        Public Property Term As Integer  
  
        Private p_Customer As String  
        Public Property Customer As String  
            Get  
                Return p_Customer  
            End Get  
            Set(ByVal value As String)  
                p_Customer = value  
                RaiseEvent PropertyChanged(Me,  
                  New System.ComponentModel.PropertyChangedEventArgs("Customer"))  
            End Set  
        End Property  
  
        Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
          Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
  
        Public Sub New(ByVal loanAmount As Double,  
                       ByVal interestRate As Double,  
                       ByVal term As Integer,  
                       ByVal customer As String)  
  
            Me.LoanAmount = loanAmount  
            Me.InterestRate = interestRate  
            Me.Term = term  
            p_Customer = customer  
        End Sub  
    End Class  
    ```  
  
 <span data-ttu-id="1caab-130">Также потребуется создать простое приложение, которое использует класс `Loan`.</span><span class="sxs-lookup"><span data-stu-id="1caab-130">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="1caab-131">Создание тестового приложения</span><span class="sxs-lookup"><span data-stu-id="1caab-131">To create a test application</span></span>  
  
1. <span data-ttu-id="1caab-132">Чтобы добавить проект приложения Windows Forms в существующее решение, щелкните в меню **Файл** пункт **Добавить**, а затем **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="1caab-132">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2. <span data-ttu-id="1caab-133">В диалоговом окне **Добавление нового проекта** выберите **Приложение Windows Forms** и введите `LoanApp` в качестве имени проекта, а затем нажмите кнопку **ОК**, чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="1caab-133">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="1caab-134">В **обозревателе решений** выберите проект LoanApp.</span><span class="sxs-lookup"><span data-stu-id="1caab-134">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4. <span data-ttu-id="1caab-135">В меню **Проект** выберите команду **Назначить запускаемым проектом**.</span><span class="sxs-lookup"><span data-stu-id="1caab-135">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="1caab-136">В меню **Проект** выберите **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="1caab-136">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6. <span data-ttu-id="1caab-137">В диалоговом окне **Добавление ссылки** откройте вкладку **Проекты** и выберите проект LoanClass.</span><span class="sxs-lookup"><span data-stu-id="1caab-137">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7. <span data-ttu-id="1caab-138">Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="1caab-138">Click **OK** to close the dialog box.</span></span>  
  
8. <span data-ttu-id="1caab-139">В конструкторе добавьте на форму четыре элемента управления <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="1caab-139">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="1caab-140">В редакторе кода добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="1caab-140">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="1caab-141">Добавьте в форму обработчик события для события `PropertyChanged`, воспользовавшись следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="1caab-141">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="1caab-142">Теперь можно собрать и запустить приложение.</span><span class="sxs-lookup"><span data-stu-id="1caab-142">At this point, you can build and run the application.</span></span> <span data-ttu-id="1caab-143">Обратите внимание, что в текстовых полях отображаются значения по умолчанию из класса `Loan`.</span><span class="sxs-lookup"><span data-stu-id="1caab-143">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="1caab-144">Попробуйте изменить значение процентной ставки с 7,5 на 7,1, затем закройте приложение и запустите его снова — будет восстановлено заданное по умолчанию значение 7,5.</span><span class="sxs-lookup"><span data-stu-id="1caab-144">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="1caab-145">В реальной жизни процентная ставка время от времени меняется, но не при каждом запуске этого приложения.</span><span class="sxs-lookup"><span data-stu-id="1caab-145">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="1caab-146">Чтобы не заставлять пользователя обновлять процентную ставку при каждом запуске приложения, рекомендуется сохранять самое последнее значение процентной ставки между экземплярами приложения.</span><span class="sxs-lookup"><span data-stu-id="1caab-146">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="1caab-147">На следующем шаге для этого в класс Loan будет добавлена сериализация.</span><span class="sxs-lookup"><span data-stu-id="1caab-147">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="1caab-148">Использование сериализации для хранения объекта</span><span class="sxs-lookup"><span data-stu-id="1caab-148">Using Serialization to Persist the Object</span></span>  

 <span data-ttu-id="1caab-149">Чтобы сохранить значения для класса Loan, прежде всего необходимо отметить класс атрибутом `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="1caab-149">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="1caab-150">Отметка класса как сериализуемого</span><span class="sxs-lookup"><span data-stu-id="1caab-150">To mark a class as serializable</span></span>  
  
- <span data-ttu-id="1caab-151">Измените объявление класса для класса Loan следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1caab-151">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="1caab-152">Атрибут `Serializable` сообщает компилятору, что все находящееся в классе может быть сохранено в файле.</span><span class="sxs-lookup"><span data-stu-id="1caab-152">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="1caab-153">Поскольку событие `PropertyChanged` обрабатывается в объекте Windows Form, его невозможно сериализовать.</span><span class="sxs-lookup"><span data-stu-id="1caab-153">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="1caab-154">Атрибут `NonSerialized` используется для пометки членов класса, которые не следует сохранять.</span><span class="sxs-lookup"><span data-stu-id="1caab-154">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="1caab-155">Предотвращение сериализации членов</span><span class="sxs-lookup"><span data-stu-id="1caab-155">To prevent a member from being serialized</span></span>  
  
- <span data-ttu-id="1caab-156">Измените объявление события `PropertyChanged` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1caab-156">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="1caab-157">Следующим шагом будет добавление кода сериализации в приложение LoanApp.</span><span class="sxs-lookup"><span data-stu-id="1caab-157">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="1caab-158">Чтобы выполнить сериализацию класса и записать данные в файл, используйте пространства имен <xref:System.IO> и <xref:System.Xml.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="1caab-158">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="1caab-159">Во избежание ввода полных имен можно добавить ссылки на необходимые библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="1caab-159">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="1caab-160">Добавление ссылок на пространства имен</span><span class="sxs-lookup"><span data-stu-id="1caab-160">To add references to namespaces</span></span>  
  
- <span data-ttu-id="1caab-161">Добавьте в начало файла `Form1` следующие инструкции:</span><span class="sxs-lookup"><span data-stu-id="1caab-161">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="1caab-162">В этом случае используется двоичный модуль форматирования для сохранения объекта в двоичном формате.</span><span class="sxs-lookup"><span data-stu-id="1caab-162">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="1caab-163">Следующим шагом является добавление кода для десериализации объекта из файла при создании объекта.</span><span class="sxs-lookup"><span data-stu-id="1caab-163">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="1caab-164">Десериализация объекта</span><span class="sxs-lookup"><span data-stu-id="1caab-164">To deserialize an object</span></span>  
  
1. <span data-ttu-id="1caab-165">Добавьте в класс константу для имени файла сериализованных данных.</span><span class="sxs-lookup"><span data-stu-id="1caab-165">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. <span data-ttu-id="1caab-166">Измените код процедуры события `Form1_Load` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1caab-166">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        If File.Exists(FileName) Then  
            Dim TestFileStream As Stream = File.OpenRead(FileName)  
            Dim deserializer As New BinaryFormatter  
            TestLoan = CType(deserializer.Deserialize(TestFileStream), LoanClass.Loan)  
            TestFileStream.Close()  
        End If  
  
        AddHandler TestLoan.PropertyChanged, AddressOf Me.CustomerPropertyChanged  
  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
     <span data-ttu-id="1caab-167">Прежде всего убедитесь, что файл существует.</span><span class="sxs-lookup"><span data-stu-id="1caab-167">Note that you first must check that the file exists.</span></span> <span data-ttu-id="1caab-168">Если он существует, создайте класс <xref:System.IO.Stream> для чтения двоичного файла и класс <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> для преобразования файла.</span><span class="sxs-lookup"><span data-stu-id="1caab-168">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="1caab-169">Кроме того, необходимо преобразовать тип потока в тип объекта Loan.</span><span class="sxs-lookup"><span data-stu-id="1caab-169">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="1caab-170">Далее необходимо добавить код для сохранения данных, введенных в текстовые поля класса `Loan`, а затем сериализовать класс в файл.</span><span class="sxs-lookup"><span data-stu-id="1caab-170">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="1caab-171">Сохранение данных и сериализация класса</span><span class="sxs-lookup"><span data-stu-id="1caab-171">To save the data and serialize the class</span></span>  
  
- <span data-ttu-id="1caab-172">В процедуру события `Form1_FormClosing` добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="1caab-172">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
    ```vb  
    Private Sub Form1_FormClosing() Handles MyBase.FormClosing  
        TestLoan.LoanAmount = CDbl(TextBox1.Text)  
        TestLoan.InterestRate = CDbl(TextBox2.Text)  
        TestLoan.Term = CInt(TextBox3.Text)  
        TestLoan.Customer = TextBox4.Text  
  
        Dim TestFileStream As Stream = File.Create(FileName)  
        Dim serializer As New BinaryFormatter  
        serializer.Serialize(TestFileStream, TestLoan)  
        TestFileStream.Close()  
    End Sub  
    ```  
  
 <span data-ttu-id="1caab-173">Теперь можно снова собрать и запустить приложение.</span><span class="sxs-lookup"><span data-stu-id="1caab-173">At this point, you can again build and run the application.</span></span> <span data-ttu-id="1caab-174">Первоначально в текстовых полях отображаются значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1caab-174">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="1caab-175">Попробуйте изменить их и ввести имя в четвертое текстовое поле.</span><span class="sxs-lookup"><span data-stu-id="1caab-175">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="1caab-176">Закройте приложение, а затем снова запустите его.</span><span class="sxs-lookup"><span data-stu-id="1caab-176">Close the application and then run it again.</span></span> <span data-ttu-id="1caab-177">Обратите внимание, что теперь в текстовых полях отображаются новые значения.</span><span class="sxs-lookup"><span data-stu-id="1caab-177">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1caab-178">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1caab-178">See also</span></span>

- [<span data-ttu-id="1caab-179">Сериализация (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1caab-179">Serialization (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="1caab-180">Руководство по программированию на Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1caab-180">Visual Basic Programming Guide</span></span>](../../index.md)
