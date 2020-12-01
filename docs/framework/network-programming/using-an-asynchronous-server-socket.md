---
title: Использование асинхронных сокетов сервера
description: В этом примере показано использование асинхронного сокета сервера. Класс Socket использует асинхронную модель программирования платформы .NET Framework для обработки запросов сетевых служб.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- sockets, asynchronous server sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- asynchronous server sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
ms.openlocfilehash: 6800a1973d9eb65bbb7520f9db7a8f431656c685
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265210"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="6353f-104">Использование асинхронных сокетов сервера</span><span class="sxs-lookup"><span data-stu-id="6353f-104">Using an Asynchronous Server Socket</span></span>

<span data-ttu-id="6353f-105">Асинхронные сокеты сервера используют асинхронную модель программирования платформы .NET Framework для обработки запросов сетевых служб.</span><span class="sxs-lookup"><span data-stu-id="6353f-105">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="6353f-106">Класс <xref:System.Net.Sockets.Socket> соответствует стандартному шаблону асинхронного именования платформы .NET Framework. Например, синхронный метод <xref:System.Net.Sockets.Socket.Accept%2A> соответствует асинхронным методам <xref:System.Net.Sockets.Socket.BeginAccept%2A> и <xref:System.Net.Sockets.Socket.EndAccept%2A>.</span><span class="sxs-lookup"><span data-stu-id="6353f-106">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="6353f-107">Для асинхронного сокета сервера нужен метод, который начинает принимать запросы на соединение из сети, метод обратного вызова, чтобы обрабатывать запросы на соединение и начинать принимать данные, и метод обратного вызова для завершения получения данных.</span><span class="sxs-lookup"><span data-stu-id="6353f-107">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="6353f-108">Все эти методы описаны ниже в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="6353f-108">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="6353f-109">В следующем примере, чтобы начать принимать запросы на соединение по сети, метод `StartListening` инициализирует **сокет**, а затем использует метод **BeginAccept**, чтобы начать принимать новые соединения.</span><span class="sxs-lookup"><span data-stu-id="6353f-109">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="6353f-110">Метод обратного вызова приема выполняется, когда сокет получает новый запрос на соединение.</span><span class="sxs-lookup"><span data-stu-id="6353f-110">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="6353f-111">Он отвечает за получение экземпляра **сокета**, обрабатывающего соединение, и передачу этого **сокета** в поток, который будет обрабатывать запрос.</span><span class="sxs-lookup"><span data-stu-id="6353f-111">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="6353f-112">Метод обратного вызова приема реализует делегат <xref:System.AsyncCallback>; он возвращает значение void и принимает один параметр типа <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="6353f-112">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="6353f-113">В приведенном ниже примере показана оболочка метода обратного вызова приема.</span><span class="sxs-lookup"><span data-stu-id="6353f-113">The following example is the shell of an accept callback method.</span></span>  
  
```vb  
Sub AcceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
void AcceptCallback(IAsyncResult ar)
{  
    // Add the callback code here.  
}  
```  
  
 <span data-ttu-id="6353f-114">Метод **BeginAccept** принимает 2 параметра: делегат **AsyncCallback**, указывающий на метод обратного вызова приема, и объект, используемый для передачи сведений о состоянии в метод обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="6353f-114">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="6353f-115">В приведенном ниже примере прослушивающий **сокет** передается в метод обратного вызова с помощью параметра *состояния*.</span><span class="sxs-lookup"><span data-stu-id="6353f-115">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="6353f-116">В этом примере создается делегат **AsyncCallback** и начинается прием подключений из сети.</span><span class="sxs-lookup"><span data-stu-id="6353f-116">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 <span data-ttu-id="6353f-117">Асинхронные сокеты используют потоки из системного пула потоков для обработки входящих подключений.</span><span class="sxs-lookup"><span data-stu-id="6353f-117">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="6353f-118">Один поток отвечает за принятие подключений, другой — за обработку каждого входящего соединения, а еще один — за получение данных по соединению.</span><span class="sxs-lookup"><span data-stu-id="6353f-118">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="6353f-119">Это может быть один и тот же поток, если пул потоков назначил его для выполнения всех трех задач.</span><span class="sxs-lookup"><span data-stu-id="6353f-119">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="6353f-120">В приведенном ниже примере класс <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> приостанавливает выполнение главного потока и сообщает, когда оно может быть продолжено.</span><span class="sxs-lookup"><span data-stu-id="6353f-120">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="6353f-121">В этом примере показан асинхронный метод, который создает на локальном компьютере асинхронный сокет TCP/IP и начинает принимать соединения.</span><span class="sxs-lookup"><span data-stu-id="6353f-121">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="6353f-122">В нем предполагается, что существует глобальный экземпляр класса **ManualResetEvent** с именем `allDone`, метод является членом класса `SocketListener` и определен метод обратного вызова с именем `AcceptCallback`.</span><span class="sxs-lookup"><span data-stu-id="6353f-122">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `AcceptCallback` is defined.</span></span>  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}")  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.AcceptCallback), _  
                listener)  
  
            allDone.WaitOne()  
        End While  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
    Console.WriteLine("Closing the listener...")  
End Sub 'StartListening  
```  
  
```csharp  
public void StartListening()
{  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0], 11000);  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}");  
  
    Socket listener = new Socket(localEP.Address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);  
  
    try
    {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true)
        {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
  
            allDone.WaitOne();  
        }  
    }
    catch (Exception e)
    {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine("Closing the listener...");  
}  
```  
  
 <span data-ttu-id="6353f-123">Метод обратного вызова приема (`AcceptCallback` в предыдущем примере) отвечает за передачу сигнала главному потоку приложения о том, что можно продолжать обработку, установление соединения с клиентом и запуск асинхронной операции чтения данных из клиента.</span><span class="sxs-lookup"><span data-stu-id="6353f-123">The accept callback method (`AcceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="6353f-124">Приведенный ниже пример представляет собой первую часть реализации метода `AcceptCallback`.</span><span class="sxs-lookup"><span data-stu-id="6353f-124">The following example is the first part of an implementation of the `AcceptCallback` method.</span></span> <span data-ttu-id="6353f-125">В ней метод сообщает главному потоку приложения о необходимости продолжить обработку и устанавливает соединение с клиентом.</span><span class="sxs-lookup"><span data-stu-id="6353f-125">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="6353f-126">Предполагается наличие глобального экземпляра класса **ManualResetEvent** с именем `allDone`.</span><span class="sxs-lookup"><span data-stu-id="6353f-126">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
```vb  
Public Sub AcceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
public void AcceptCallback(IAsyncResult ar)
{  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.
}  
```  
  
 <span data-ttu-id="6353f-127">Для чтения данных из сокета клиента требуется объект состояния, который передает значения от одного асинхронного вызова к другому.</span><span class="sxs-lookup"><span data-stu-id="6353f-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="6353f-128">В приведенном ниже примере реализуется объект состояния для получения строки от удаленного клиента.</span><span class="sxs-lookup"><span data-stu-id="6353f-128">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="6353f-129">Он содержит поля для сокета клиента, буфер данных для получения данных и <xref:System.Text.StringBuilder> для создания строки данных, отправленной клиентом.</span><span class="sxs-lookup"><span data-stu-id="6353f-129">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="6353f-130">Добавление этих полей в объект состояния позволяет сохранять их значения между вызовами для чтения данных из сокета клиента.</span><span class="sxs-lookup"><span data-stu-id="6353f-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject
{  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="6353f-131">Часть метода `AcceptCallback`, которая начинает получать данные из сокета клиента, сначала инициализирует экземпляр класса `StateObject`, а затем вызывает метод <xref:System.Net.Sockets.Socket.BeginReceive%2A>, чтобы начать чтение данных из сокета клиента в асинхронном режиме.</span><span class="sxs-lookup"><span data-stu-id="6353f-131">The section of the `AcceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="6353f-132">В приведенном ниже примере показан полный метод `AcceptCallback`.</span><span class="sxs-lookup"><span data-stu-id="6353f-132">The following example shows the complete `AcceptCallback` method.</span></span> <span data-ttu-id="6353f-133">В нем предполагается, что существует глобальный экземпляр класса **ManualResetEvent** с именем `allDone,`, определен класс `StateObject` и определен метод `ReadCallback` в классе с именем `SocketListener`.</span><span class="sxs-lookup"><span data-stu-id="6353f-133">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `ReadCallback` method is defined in a class named `SocketListener`.</span></span>  
  
```vb  
Public Shared Sub AcceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.ReadCallback, state)  
End Sub 'AcceptCallback  
```  
  
```csharp  
public static void AcceptCallback(IAsyncResult ar)
{  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.ReadCallback), state);  
}  
```  
  
 <span data-ttu-id="6353f-134">Последний метод, который необходимо реализовать для асинхронного сокета сервера, — это метод обратного вызова чтения, который возвращает данные, отправленные клиентом.</span><span class="sxs-lookup"><span data-stu-id="6353f-134">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="6353f-135">Как и метод обратного вызова приема, он является делегатом **AsyncCallback**.</span><span class="sxs-lookup"><span data-stu-id="6353f-135">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="6353f-136">Этот метод считывает один или несколько байтов из сокета клиента в буфер данных, а затем снова вызывает метод **BeginReceive**, пока данные, отправленные клиентом, не закончатся.</span><span class="sxs-lookup"><span data-stu-id="6353f-136">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="6353f-137">После того как сообщение от клиента будет прочитано полностью, строка выводится в консоли, а сокет сервера, обрабатывавший соединение с клиентом, закрывается.</span><span class="sxs-lookup"><span data-stu-id="6353f-137">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="6353f-138">В приведенном ниже примере реализуется метод `ReadCallback`.</span><span class="sxs-lookup"><span data-stu-id="6353f-138">The following sample implements the `ReadCallback` method.</span></span> <span data-ttu-id="6353f-139">В нем предполагается, что определен класс `StateObject`.</span><span class="sxs-lookup"><span data-stu-id="6353f-139">It assumes that the `StateObject` class is defined.</span></span>  
  
```vb  
Public Shared Sub ReadCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReadCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine($"Read {content.Length} bytes from socket. {ControlChars.Cr} Data : {content}")  
        End If  
    End If  
End Sub 'ReadCallback  
```  
  
```csharp  
public static void ReadCallback(IAsyncResult ar)
{  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0)
    {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReadCallback), state);  
    }
    else
    {  
        if (state.sb.Length > 1)
        {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine($"Read {content.Length} bytes from socket.\n Data : {content}");
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6353f-140">См. также</span><span class="sxs-lookup"><span data-stu-id="6353f-140">See also</span></span>

- [<span data-ttu-id="6353f-141">Использование синхронного сокета сервера</span><span class="sxs-lookup"><span data-stu-id="6353f-141">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="6353f-142">Пример асинхронного сокета сервера</span><span class="sxs-lookup"><span data-stu-id="6353f-142">Asynchronous Server Socket Example</span></span>](asynchronous-server-socket-example.md)
- [<span data-ttu-id="6353f-143">Работа с потоками</span><span class="sxs-lookup"><span data-stu-id="6353f-143">Threading</span></span>](../../standard/threading/index.md)
- [<span data-ttu-id="6353f-144">Прослушивание с помощью сокетов</span><span class="sxs-lookup"><span data-stu-id="6353f-144">Listening with Sockets</span></span>](listening-with-sockets.md)
