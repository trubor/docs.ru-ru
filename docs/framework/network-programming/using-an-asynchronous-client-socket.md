---
title: Использование асинхронных сокетов клиента
description: В этом примере показано использование асинхронного сокета клиента. Асинхронная модель программирования .NET Framework позволяет приложению продолжать работу во время обработки соединения.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- asynchronous client sockets
- Socket class, asynchronous client sockets
- requesting data from Internet, sockets
- sockets, asynchronous client sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
ms.openlocfilehash: af5379533e51e7488d673359dc24268c6329c082
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265223"
---
# <a name="using-an-asynchronous-client-socket"></a><span data-ttu-id="a22d7-104">Использование асинхронных сокетов клиента</span><span class="sxs-lookup"><span data-stu-id="a22d7-104">Using an Asynchronous Client Socket</span></span>

<span data-ttu-id="a22d7-105">Асинхронный сокет клиента не приостанавливает работу приложения на то время, пока выполняются сетевые операции.</span><span class="sxs-lookup"><span data-stu-id="a22d7-105">An asynchronous client socket does not suspend the application while waiting for network operations to complete.</span></span> <span data-ttu-id="a22d7-106">Вместо этого он использует стандартную модель асинхронного программирования .NET Framework для обработки операций сетевого подключения в одном потоке, пока приложение продолжает работу в изначальном потоке.</span><span class="sxs-lookup"><span data-stu-id="a22d7-106">Instead, it uses the standard .NET Framework asynchronous programming model to process the network connection on one thread while the application continues to run on the original thread.</span></span> <span data-ttu-id="a22d7-107">Асинхронные сокеты подходят для приложений, которые интенсивно используют сеть или не могут ждать, пока сетевые операции завершатся.</span><span class="sxs-lookup"><span data-stu-id="a22d7-107">Asynchronous sockets are appropriate for applications that make heavy use of the network or that cannot wait for network operations to complete before continuing.</span></span>  
  
 <span data-ttu-id="a22d7-108">Класс <xref:System.Net.Sockets.Socket> соответствует шаблону именования платформы .NET Framework для асинхронных методов. Например, синхронный метод <xref:System.Net.Sockets.Socket.Receive%2A> соответствует асинхронным методам <xref:System.Net.Sockets.Socket.BeginReceive%2A> и <xref:System.Net.Sockets.Socket.EndReceive%2A>.</span><span class="sxs-lookup"><span data-stu-id="a22d7-108">The <xref:System.Net.Sockets.Socket> class follows the .NET Framework naming pattern for asynchronous methods; for example, the synchronous <xref:System.Net.Sockets.Socket.Receive%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginReceive%2A> and <xref:System.Net.Sockets.Socket.EndReceive%2A> methods.</span></span>  
  
 <span data-ttu-id="a22d7-109">Чтобы вернуть результат, асинхронным операциям требуется метод обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="a22d7-109">Asynchronous operations require a callback method to return the result of the operation.</span></span> <span data-ttu-id="a22d7-110">Если приложению не требуется результат, то метод обратного вызова не нужен.</span><span class="sxs-lookup"><span data-stu-id="a22d7-110">If your application does not need to know the result, then no callback method is required.</span></span> <span data-ttu-id="a22d7-111">В примере кода в этом разделе демонстрируется использование метода для инициации подключения к сетевому устройству и метода обратного вызова для завершения подключения, метода, который начинает отправку данных, и метода обратного вызова, завершающего отправку, а также метода, который начинает получение данных, и метода обратного вызова, завершающего получение.</span><span class="sxs-lookup"><span data-stu-id="a22d7-111">The example code in this section demonstrates using a method to start connecting to a network device and a callback method to complete the connection, a method to start sending data and a callback method to complete the send, and a method to start receiving data and a callback method to end receiving data.</span></span>  
  
 <span data-ttu-id="a22d7-112">Асинхронные сокеты используют несколько потоков из системного пула потоков для обработки сетевых подключений.</span><span class="sxs-lookup"><span data-stu-id="a22d7-112">Asynchronous sockets use multiple threads from the system thread pool to process network connections.</span></span> <span data-ttu-id="a22d7-113">Один поток отвечает за инициацию отправки или получения данных, а другие завершают подключение к сетевому устройству, а также отправляют или получают данные.</span><span class="sxs-lookup"><span data-stu-id="a22d7-113">One thread is responsible for initiating the sending or receiving of data; other threads complete the connection to the network device and send or receive the data.</span></span> <span data-ttu-id="a22d7-114">В приведенном ниже примере экземпляры класса <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> приостанавливают выполнение главного потока и сообщают, когда оно может быть продолжено.</span><span class="sxs-lookup"><span data-stu-id="a22d7-114">In the following examples, instances of the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class are used to suspend execution of the main thread and signal when execution can continue.</span></span>  
  
 <span data-ttu-id="a22d7-115">В приведенном ниже примере для подключения асинхронного сокета к сетевому устройству метод `Connect` инициализирует объект **Socket**, а затем вызывает метод <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType>, передавая удаленную конечную точку, которая представляет сетевое устройство, метод обратного вызова для подключения и объект состояния (объект **Socket** клиента), который служит для передачи сведений о состоянии между асинхронными вызовами.</span><span class="sxs-lookup"><span data-stu-id="a22d7-115">In the following example, to connect an asynchronous socket to a network device, the `Connect` method initializes a **Socket** and then calls the <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> method, passing a remote endpoint that represents the network device, the connect callback method, and a state object (the client **Socket**), which is used to pass state information between asynchronous calls.</span></span> <span data-ttu-id="a22d7-116">В этом примере реализуется метод `Connect` для подключения указанного объекта **Socket** к определенной конечной точке.</span><span class="sxs-lookup"><span data-stu-id="a22d7-116">The example implements the `Connect` method to connect the specified **Socket** to the specified endpoint.</span></span> <span data-ttu-id="a22d7-117">Предполагается наличие глобального экземпляра класса **ManualResetEvent** с именем `connectDone`.</span><span class="sxs-lookup"><span data-stu-id="a22d7-117">It assumes a global **ManualResetEvent** named `connectDone`.</span></span>  
  
```vb  
Public Shared Sub Connect(remoteEP As EndPoint, client As Socket)  
    client.BeginConnect(remoteEP, _  
       AddressOf ConnectCallback, client)  
  
    connectDone.WaitOne()  
End Sub 'Connect  
```  
  
```csharp  
public static void Connect(EndPoint remoteEP, Socket client) {  
    client.BeginConnect(remoteEP,
        new AsyncCallback(ConnectCallback), client );  
  
   connectDone.WaitOne();  
}  
```  
  
 <span data-ttu-id="a22d7-118">Метод обратного вызова подключения `ConnectCallback` реализует делегат <xref:System.AsyncCallback>.</span><span class="sxs-lookup"><span data-stu-id="a22d7-118">The connect callback method `ConnectCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="a22d7-119">Он подключается к удаленному устройству, если оно доступно, а затем сообщает потоку приложения, что подключение завершено, задавая **ManualResetEvent** `connectDone`.</span><span class="sxs-lookup"><span data-stu-id="a22d7-119">It connects to the remote device when the remote device is available and then signals the application thread that the connection is complete by setting the **ManualResetEvent** `connectDone`.</span></span> <span data-ttu-id="a22d7-120">В следующем коде реализуется метод `ConnectCallback`:</span><span class="sxs-lookup"><span data-stu-id="a22d7-120">The following code implements the `ConnectCallback` method.</span></span>  
  
```vb  
Private Shared Sub ConnectCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", _  
            client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ConnectCallback  
```  
  
```csharp  
private static void ConnectCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete the connection.  
        client.EndConnect(ar);  
  
        Console.WriteLine("Socket connected to {0}",  
            client.RemoteEndPoint.ToString());  
  
        // Signal that the connection has been made.  
        connectDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="a22d7-121">Метод `Send` из примера кодирует предоставленные строковые данные в формате ASCII и отправляет их асинхронно сетевому устройству, представленному указанным сокетом.</span><span class="sxs-lookup"><span data-stu-id="a22d7-121">The example method `Send` encodes the specified string data in ASCII format and sends it asynchronously to the network device represented by the specified socket.</span></span> <span data-ttu-id="a22d7-122">В следующем примере реализуется метод `Send`:</span><span class="sxs-lookup"><span data-stu-id="a22d7-122">The following example implements the `Send` method.</span></span>  
  
```vb  
Private Shared Sub Send(client As Socket, data As [String])  
    ' Convert the string data to byte data using ASCII encoding.  
    Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
    ' Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None, _  
        AddressOf SendCallback, client)  
End Sub 'Send  
```  
  
```csharp  
private static void Send(Socket client, String data) {  
    // Convert the string data to byte data using ASCII encoding.  
    byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
    // Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None,  
        new AsyncCallback(SendCallback), client);  
}  
```  
  
 <span data-ttu-id="a22d7-123">Метод обратного вызова отправки `SendCallback` реализует делегат <xref:System.AsyncCallback>.</span><span class="sxs-lookup"><span data-stu-id="a22d7-123">The send callback method `SendCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="a22d7-124">Он отправляет данные, когда сетевое устройство готово к их приему.</span><span class="sxs-lookup"><span data-stu-id="a22d7-124">It sends the data when the network device is ready to receive.</span></span> <span data-ttu-id="a22d7-125">В приведенном ниже примере показана реализация метода `SendCallback`.</span><span class="sxs-lookup"><span data-stu-id="a22d7-125">The following example shows the implementation of the `SendCallback` method.</span></span> <span data-ttu-id="a22d7-126">Предполагается наличие глобального экземпляра класса **ManualResetEvent** с именем `sendDone`.</span><span class="sxs-lookup"><span data-stu-id="a22d7-126">It assumes a global **ManualResetEvent** named `sendDone`.</span></span>  
  
```vb  
Private Shared Sub SendCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'SendCallback  
```  
  
```csharp  
private static void SendCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete sending the data to the remote device.  
        int bytesSent = client.EndSend(ar);  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent);  
  
        // Signal that all bytes have been sent.  
        sendDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="a22d7-127">Для чтения данных из сокета клиента требуется объект состояния, который передает значения от одного асинхронного вызова к другому.</span><span class="sxs-lookup"><span data-stu-id="a22d7-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="a22d7-128">Следующий класс — это пример объекта состояния для получения данных из сокета клиента.</span><span class="sxs-lookup"><span data-stu-id="a22d7-128">The following class is an example state object for receiving data from a client socket.</span></span> <span data-ttu-id="a22d7-129">Он содержит поле для сокета клиента, буфер для принимаемых данных и объект <xref:System.Text.StringBuilder> для хранения полученной строки данных.</span><span class="sxs-lookup"><span data-stu-id="a22d7-129">It contains a field for the client socket, a buffer for the received data, and a <xref:System.Text.StringBuilder> to hold the incoming data string.</span></span> <span data-ttu-id="a22d7-130">Добавление этих полей в объект состояния позволяет сохранять их значения между вызовами для чтения данных из сокета клиента.</span><span class="sxs-lookup"><span data-stu-id="a22d7-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing
    ' Size of receive buffer.  
    Public BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(256) As Byte
    ' Received data string.  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    // Client socket.  
    public Socket workSocket = null;  
    // Size of receive buffer.  
    public const int BufferSize = 256;  
    // Receive buffer.  
    public byte[] buffer = new byte[BufferSize];  
    // Received data string.  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="a22d7-131">Метод `Receive` из примера создает объект состояния, а затем вызывает метод **BeginReceive** для чтения данных из сокета клиента в асинхронном режиме.</span><span class="sxs-lookup"><span data-stu-id="a22d7-131">The example `Receive` method sets up the state object and then calls the **BeginReceive** method to read the data from the client socket asynchronously.</span></span> <span data-ttu-id="a22d7-132">В следующем примере реализуется метод `Receive`:</span><span class="sxs-lookup"><span data-stu-id="a22d7-132">The following example implements the `Receive` method.</span></span>  
  
```vb  
Private Shared Sub Receive(client As Socket)  
    Try  
        ' Create the state object.  
        Dim state As New StateObject()  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReceiveCallback, state)  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'Receive  
```  
  
```csharp  
private static void Receive(Socket client) {  
    try {  
        // Create the state object.  
        StateObject state = new StateObject();  
        state.workSocket = client;  
  
        // Begin receiving the data from the remote device.  
        client.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReceiveCallback), state);  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="a22d7-133">Метод обратного вызова получения `ReceiveCallback` реализует делегат **AsyncCallback**.</span><span class="sxs-lookup"><span data-stu-id="a22d7-133">The receive callback method `ReceiveCallback` implements the **AsyncCallback** delegate.</span></span> <span data-ttu-id="a22d7-134">Он получает данные от сетевого устройства и формирует строку сообщения.</span><span class="sxs-lookup"><span data-stu-id="a22d7-134">It receives the data from the network device and builds a message string.</span></span> <span data-ttu-id="a22d7-135">Этот метод считывает один или несколько байтов данных из сети в буфер данных, а затем снова вызывает метод **BeginReceive**, пока данные, отправленные клиентом, не закончатся.</span><span class="sxs-lookup"><span data-stu-id="a22d7-135">It reads one or more bytes of data from the network into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="a22d7-136">После считывания всех данных из клиента `ReceiveCallback` сообщает потоку приложения о том, что данные закончились, задавая **ManualResetEvent** `sendDone`.</span><span class="sxs-lookup"><span data-stu-id="a22d7-136">Once all the data is read from the client, `ReceiveCallback` signals the application thread that the data is complete by setting the **ManualResetEvent** `sendDone`.</span></span>  
  
 <span data-ttu-id="a22d7-137">В приведенном ниже примере реализуется метод `ReceiveCallback`.</span><span class="sxs-lookup"><span data-stu-id="a22d7-137">The following example code implements the `ReceiveCallback` method.</span></span> <span data-ttu-id="a22d7-138">В нем предполагается наличие глобальной строковой переменной с именем `response`, в которой хранится полученная строка, и глобального экземпляра класса **ManualResetEvent** с именем `receiveDone`.</span><span class="sxs-lookup"><span data-stu-id="a22d7-138">It assumes a global string named `response` that holds the received string and a global **ManualResetEvent** named `receiveDone`.</span></span> <span data-ttu-id="a22d7-139">Для завершения сетевого сеанса сервер должен завершить работу сокета клиента надлежащим образом.</span><span class="sxs-lookup"><span data-stu-id="a22d7-139">The server must shut down the client socket gracefully to end the network session.</span></span>  
  
```vb  
Private Shared Sub ReceiveCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the state object and the client socket
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, _  
                bytesRead))  
  
            '  Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
                AddressOf ReceiveCallback, state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ReceiveCallback  
```  
  
```csharp  
private static void ReceiveCallback( IAsyncResult ar ) {  
    try {  
        // Retrieve the state object and the client socket
        // from the asynchronous state object.  
        StateObject state = (StateObject) ar.AsyncState;  
        Socket client = state.workSocket;  
        // Read data from the remote device.  
        int bytesRead = client.EndReceive(ar);  
        if (bytesRead > 0) {  
            // There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,bytesRead));  
                //  Get the rest of the data.  
            client.BeginReceive(state.buffer,0,StateObject.BufferSize,0,  
                new AsyncCallback(ReceiveCallback), state);  
        } else {  
            // All the data has arrived; put it in response.  
            if (state.sb.Length > 1) {  
                response = state.sb.ToString();  
            }  
            // Signal that all bytes have been received.  
            receiveDone.Set();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a22d7-140">См. также</span><span class="sxs-lookup"><span data-stu-id="a22d7-140">See also</span></span>

- [<span data-ttu-id="a22d7-141">Использование синхронного сокета клиента</span><span class="sxs-lookup"><span data-stu-id="a22d7-141">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="a22d7-142">Прослушивание с помощью сокетов</span><span class="sxs-lookup"><span data-stu-id="a22d7-142">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="a22d7-143">Примеры асинхронных сокетов клиента</span><span class="sxs-lookup"><span data-stu-id="a22d7-143">Asynchronous Client Socket Example</span></span>](asynchronous-client-socket-example.md)
