---
description: 'Дополнительные сведения: данные FILESTREAM'
title: Данные FILESTREAM
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 0110be6b867a07ec1cd204e2a3de371367bbfa36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802051"
---
# <a name="filestream-data"></a><span data-ttu-id="4977b-103">Данные FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="4977b-103">FILESTREAM Data</span></span>

<span data-ttu-id="4977b-104">Для двоичных (BLOB) данных, хранимых в столбце varbinary(max), появился новый атрибут хранилища FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="4977b-104">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="4977b-105">Перед созданием FILESTREAM для хранения двоичных данных требовалась специальная обработка.</span><span class="sxs-lookup"><span data-stu-id="4977b-105">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="4977b-106">Неструктурированные данные, такие как текстовые документы, изображения и видео, часто хранятся вне базы данных, что затрудняет управление ими.</span><span class="sxs-lookup"><span data-stu-id="4977b-106">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>

> [!NOTE]
> <span data-ttu-id="4977b-107">Для работы с данными FILESTREAM через SqlClient необходимо установить .NET Framework 3.5 с пакетом обновления 1 (SP1) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="4977b-107">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>

<span data-ttu-id="4977b-108">При указании для столбца varbinary(max) атрибута FILESTREAM сервер SQL Server сохраняет данные не в файле базы данных, а в файловой системе NTFS на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="4977b-108">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="4977b-109">Хотя эти данные хранятся отдельно, для работы с ними можно использовать те же инструкции Transact-SQL, что и для данных varbinary(max), хранящихся в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4977b-109">Although it is stored separately, you can use the same Transact-SQL statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>

## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="4977b-110">Поддержка атрибута FILESTREAM в SqlClient</span><span class="sxs-lookup"><span data-stu-id="4977b-110">SqlClient Support for FILESTREAM</span></span>

<span data-ttu-id="4977b-111">Платформа .NET Framework поставщик данных для SQL Server, <xref:System.Data.SqlClient> поддерживает чтение и запись данных FILESTREAM с помощью <xref:System.Data.SqlTypes.SqlFileStream> класса, определенного в <xref:System.Data.SqlTypes> пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="4977b-111">The .NET Framework Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="4977b-112">`SqlFileStream` наследует от класса <xref:System.IO.Stream>, который предоставляет методы для чтения и записи в потоки данных.</span><span class="sxs-lookup"><span data-stu-id="4977b-112">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="4977b-113">После считывания из потока данные передаются из потока в структуру данных, например массив байтов.</span><span class="sxs-lookup"><span data-stu-id="4977b-113">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="4977b-114">Запись передает данные из структуры данных в поток.</span><span class="sxs-lookup"><span data-stu-id="4977b-114">Writing transfers the data from the data structure into a stream.</span></span>

### <a name="creating-the-sql-server-table"></a><span data-ttu-id="4977b-115">Создание таблицы SQL Server</span><span class="sxs-lookup"><span data-stu-id="4977b-115">Creating the SQL Server Table</span></span>

<span data-ttu-id="4977b-116">Приведенная ниже инструкция Transact-SQL создает таблицу employees и вставляет в нее строку данных.</span><span class="sxs-lookup"><span data-stu-id="4977b-116">The following Transact-SQL statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="4977b-117">После включения хранилища FILESTREAM эту таблицу можно использовать вместе с приведенными ниже примерами кода.</span><span class="sxs-lookup"><span data-stu-id="4977b-117">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="4977b-118">Ссылки на ресурсы электронной документации на SQL Server приведены в конце данного раздела.</span><span class="sxs-lookup"><span data-stu-id="4977b-118">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>

```sql
CREATE TABLE employees
(
  EmployeeId INT  NOT NULL  PRIMARY KEY,
  Photo VARBINARY(MAX) FILESTREAM  NULL,
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL
  UNIQUE DEFAULT NEWID()
)
GO
Insert into employees
Values(1, 0x00, default)
GO
```

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="4977b-119">Пример. Чтение, перезапись и вставка данных FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="4977b-119">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>

<span data-ttu-id="4977b-120">В приведенном ниже примере демонстрируется чтение данных из потока FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="4977b-120">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="4977b-121">Код получает логический путь к файлу, устанавливая для `FileAccess` значение `Read` и для `FileOptions` — `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="4977b-121">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="4977b-122">Затем код считывает байты из SqlFileStream и передает их в буфер.</span><span class="sxs-lookup"><span data-stu-id="4977b-122">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="4977b-123">Затем байты записываются в окно консоли.</span><span class="sxs-lookup"><span data-stu-id="4977b-123">The bytes are then written to the console window.</span></span>

<span data-ttu-id="4977b-124">В примере также демонстрируется запись данных в поток FILESTREAM с перезаписью всех существующих данных.</span><span class="sxs-lookup"><span data-stu-id="4977b-124">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="4977b-125">Код получает логический путь к файлу и создает `SqlFileStream` устанавливая для `FileAccess` значение `Write` и для `FileOptions` — `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="4977b-125">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="4977b-126">Один байт записывается в `SqlFileStream`, заменяя все данные в файле.</span><span class="sxs-lookup"><span data-stu-id="4977b-126">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>

<span data-ttu-id="4977b-127">В приведенном примере также демонстрируется запись данных в поток FILESTREAM с использованием метода Seek для добавления данных в конец файла.</span><span class="sxs-lookup"><span data-stu-id="4977b-127">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="4977b-128">Код получает логический путь к файлу и создает `SqlFileStream` устанавливая для `FileAccess` значение `ReadWrite` и для `FileOptions` — `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="4977b-128">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="4977b-129">Код использует метод Seek для поиска конца файла, добавляя один байт к существующему файлу.</span><span class="sxs-lookup"><span data-stu-id="4977b-129">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Data.SqlTypes;
using System.Data;
using System.IO;

namespace FileStreamTest
{
    class Program
    {
        static void Main(string[] args)
        {
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for the file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Read the contents as bytes and write them to the console
                            for (long index = 0; index < fileStream.Length; index++)
                            {
                                Console.WriteLine(fileStream.ReadByte());
                            }
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Write a single byte to the file. This will
                            // replace any data in the file.
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Seek to the end of the file
                            fileStream.Seek(0, SeekOrigin.End);

                            // Append a single byte
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }

        }
    }
}
```

<span data-ttu-id="4977b-130">Другой пример см. в разделе [Как сохранять и извлекать двоичные данные в столбце файлового потока](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="4977b-130">For another sample, see [How to store and fetch binary data into a file stream column](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>

## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="4977b-131">Ресурсы в электронной документации по SQL Server</span><span class="sxs-lookup"><span data-stu-id="4977b-131">Resources in SQL Server Books Online</span></span>

<span data-ttu-id="4977b-132">Полная документация по FILESTREAM содержится в указанных ниже разделах электронной документации на SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4977b-132">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>

|<span data-ttu-id="4977b-133">Раздел</span><span class="sxs-lookup"><span data-stu-id="4977b-133">Topic</span></span>|<span data-ttu-id="4977b-134">Описание</span><span class="sxs-lookup"><span data-stu-id="4977b-134">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="4977b-135">FILESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4977b-135">FILESTREAM (SQL Server)</span></span>](/sql/relational-databases/blob/filestream-sql-server)|<span data-ttu-id="4977b-136">Описывает, когда следует использовать хранилище FILESTREAM, и как оно интегрирует ядро СУБД Microsoft SQL Server с файловой системой NTFS.</span><span class="sxs-lookup"><span data-stu-id="4977b-136">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|
|[<span data-ttu-id="4977b-137">Создание клиентских приложений для данных FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="4977b-137">Create Client Applications for FILESTREAM Data</span></span>](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|<span data-ttu-id="4977b-138">Описывает функции API Windows для работы с данными FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="4977b-138">Describes the Windows API functions for working with FILESTREAM data.</span></span>|
|[<span data-ttu-id="4977b-139">FILESTREAM и другие возможности SQL Server</span><span class="sxs-lookup"><span data-stu-id="4977b-139">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="4977b-140">Содержит рекомендации, направляющие и ограничения для использования данных FILESTREAM с другими функциями SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4977b-140">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4977b-141">См. также</span><span class="sxs-lookup"><span data-stu-id="4977b-141">See also</span></span>

- [<span data-ttu-id="4977b-142">Типы данных SQL Server и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4977b-142">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="4977b-143">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4977b-143">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="4977b-144">Управление доступом для кода и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4977b-144">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="4977b-145">Двоичные данные и данные больших значений SQL Server</span><span class="sxs-lookup"><span data-stu-id="4977b-145">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="4977b-146">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4977b-146">ADO.NET Overview</span></span>](../ado-net-overview.md)
