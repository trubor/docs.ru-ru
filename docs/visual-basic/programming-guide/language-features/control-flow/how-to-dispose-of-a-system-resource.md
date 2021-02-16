---
description: 'Дополнительные сведения: как удалить системный ресурс (Visual Basic)'
title: Практическое руководство. Удаление системного ресурса
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: 6594c9e2eedf756cc7a46c2c17deab58fcba3a8c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480665"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="77518-103">Практическое руководство. Удаление системного ресурса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77518-103">How to: Dispose of a System Resource (Visual Basic)</span></span>

<span data-ttu-id="77518-104">Вы можете использовать `Using` блок, чтобы гарантировать, что система уничтожает ресурс, когда код выходит из блока.</span><span class="sxs-lookup"><span data-stu-id="77518-104">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="77518-105">Это полезно, если вы используете системный ресурс, который потребляет большой объем памяти или что другие компоненты также хотят использовать.</span><span class="sxs-lookup"><span data-stu-id="77518-105">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="77518-106">Удаление подключения к базе данных после завершения работы с ним кода</span><span class="sxs-lookup"><span data-stu-id="77518-106">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="77518-107">Убедитесь, что вы включили соответствующий [оператор Imports (пространство имен .NET и тип)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) для подключения к базе данных в начале исходного файла (в данном случае <xref:System.Data.SqlClient> ).</span><span class="sxs-lookup"><span data-stu-id="77518-107">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="77518-108">Создайте `Using` блок с `Using` `End Using` инструкциями и.</span><span class="sxs-lookup"><span data-stu-id="77518-108">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="77518-109">Внутри блока разместите код, который работает с подключением к базе данных.</span><span class="sxs-lookup"><span data-stu-id="77518-109">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="77518-110">Объявите соединение и создайте его экземпляр в составе `Using` инструкции.</span><span class="sxs-lookup"><span data-stu-id="77518-110">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="77518-111">Система уничтожает ресурс независимо от того, как вы выйдете из блока, включая случай необработанного исключения.</span><span class="sxs-lookup"><span data-stu-id="77518-111">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="77518-112">Обратите внимание, что доступ извне блока невозможен `sqc` `Using` , так как его область ограничена блоком.</span><span class="sxs-lookup"><span data-stu-id="77518-112">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="77518-113">Эту же методику можно использовать для системных ресурсов, таких как файловый обработчик или оболочка COM.</span><span class="sxs-lookup"><span data-stu-id="77518-113">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="77518-114">`Using`Если вы хотите оставить ресурс доступным для других компонентов после выхода из блока, используйте блок `Using` .</span><span class="sxs-lookup"><span data-stu-id="77518-114">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77518-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="77518-115">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="77518-116">Поток управления</span><span class="sxs-lookup"><span data-stu-id="77518-116">Control Flow</span></span>](index.md)
- [<span data-ttu-id="77518-117">Структуры решений</span><span class="sxs-lookup"><span data-stu-id="77518-117">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="77518-118">Циклические структуры</span><span class="sxs-lookup"><span data-stu-id="77518-118">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="77518-119">Другие структуры управления</span><span class="sxs-lookup"><span data-stu-id="77518-119">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="77518-120">Вложенные структуры управления</span><span class="sxs-lookup"><span data-stu-id="77518-120">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="77518-121">Оператор using</span><span class="sxs-lookup"><span data-stu-id="77518-121">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
