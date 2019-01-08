---
title: Erstellen von Clientanwendungen für FILESTREAM-Daten | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Win32
ms.assetid: 8a02aff6-e54c-40c6-a066-2083e9b090aa
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 017762b9897af951020793fdd02fc34d3209da2d
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53363652"
---
# <a name="create-client-applications-for-filestream-data"></a>Erstellen von Clientanwendungen für FILESTREAM-Daten
  Sie können Win32 zum Lesen und Schreiben von Daten in einem FILESTREAM BLOB verwenden. Hierfür sind die folgenden Schritte erforderlich:  
  
-   Lesen des FILESTREAM-Dateipfads.  
  
-   Lesen des aktuellen Transaktionskontexts.  
  
-   Abrufen eines Win32-Handles und Lesen und Schreiben von Daten im FILESTREAM BLOB mit diesem Handle.  
  
> [!NOTE]  
>  Für die Beispiele in diesem Thema sind die FILESTREAM-aktivierte Datenbank und die Tabelle erforderlich, die unter [Erstellen einer FILESTREAM-aktivierten Datenbank](create-a-filestream-enabled-database.md) und [Erstellen einer Tabelle zum Speichern von FILESTREAM-Daten](create-a-table-for-storing-filestream-data.md)erstellt werden.  
  
##  <a name="func"></a> Funktionen zum Arbeiten mit FILESTREAM-Daten  
 Wenn Sie FILESTREAM zum Speichern von Binary Large Object (BLOB)-Daten verwenden, können Sie die Dateien mit Win32-APIs bearbeiten. Zum Arbeiten mit FILESTREAM BLOB-Daten in Win32-Anwendungen stellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die folgenden Funktionen und die folgende API bereit:  
  
-   [PathName](/sql/relational-databases/system-functions/pathname-transact-sql) gibt einen Pfad als Token an ein BLOB zurück. Eine Anwendung verwendet dieses Token, um ein Win32-Handle zu erhalten und mit BLOB-Daten zu arbeiten.  
  
     Wenn die Datenbank, die FILESTREAM-Daten enthält, zu einer AlwaysOn-Verfügbarkeitsgruppe gehört, dann gibt die PathName-Funktion den Namen eines virtuellen Netzwerks (VNN) statt eines Computernamens zurück.  
  
-   [GET_FILESTREAM_TRANSACTION_CONTEXT()](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) gibt ein Token zurück, das die aktuelle Transaktion einer Sitzung darstellt. Anwendungen verwenden dieses Token, um FILESTREAM-Dateisystem-Streamingvorgänge an die Transaktion zu binden.  
  
-   Die [OpenSqlFilestream-API](access-filestream-data-with-opensqlfilestream.md) bezieht ein Win32-Dateihandle. Die Anwendung verwendet dieses Handle in Stream die FILESTREAM-Daten, und Sie können das Handle dann an die folgenden Win32-APIs übergeben: [ReadFile](https://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](https://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](https://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](https://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](https://go.microsoft.com/fwlink/?LinkId=86426), oder [ FlushFileBuffers](https://go.microsoft.com/fwlink/?LinkId=86427). Wenn die Anwendung mit dem Handle irgendeine andere API anruft, wird ein ERROR_ACCESS_DENIED-Fehler zurückgegeben. Die Anwendung sollte das Handle mit [CloseHandle](https://go.microsoft.com/fwlink/?LinkId=86428)schließen.  
  
 Alle Zugriffe auf FILESTREAM-Datencontainer müssen in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Transaktion erfolgen. [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen können auch in der gleichen Transaktion ausgeführt werden, damit die SQL-Daten mit den FILESTREAM-Daten konsistent bleiben.  
  
##  <a name="steps"></a> Schritte zum Zugreifen auf FILESTREAM-Daten  
  
###  <a name="path"></a> Lesen des FILESTREAM-Dateipfads  
 Jeder Zelle in einer FILESTREAM-Tabelle ist ein Dateipfad zugeordnet. Verwenden Sie zum Lesen des Pfads die `PathName`-Eigenschaft einer `varbinary(max)`-Spalte in einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung. Das folgende Beispiel zeigt, wie der Dateipfad einer `varbinary(max)`-Spalte gelesen wird.  
  
 [!code-sql[FILESTREAM#FS_PathName](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_pathname)]  
  
###  <a name="trx"></a> Lesen des Transaktionskontexts  
 Um den aktuellen Transaktionskontext abzurufen, verwenden Sie die [!INCLUDE[tsql](../../includes/tsql-md.md)] [GET_FILESTREAM_TRANSACTION_CONTEXT()](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) function. Das folgende Beispiel zeigt, wie eine Transaktion gestartet und der aktuelle Transaktionskontext gelesen wird.  
  
 [!code-sql[FILESTREAM#FS_GET_TRANSACTION_CONTEXT](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_get_transaction_context)]  
  
###  <a name="handle"></a> Abrufen eines Win32-Dateihandles  
 Um ein Win32-Dateihandle abzurufen, rufen Sie die OpenSqlFilestream-API auf. Diese API wird aus der Datei sqlncli.dll exportiert. Das zurückgegebene Handle kann an eine der folgenden Win32-APIs übergeben werden: [ReadFile](https://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](https://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](https://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](https://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](https://go.microsoft.com/fwlink/?LinkId=86426), oder [ FlushFileBuffers](https://go.microsoft.com/fwlink/?LinkId=86427). Die folgenden Beispiele veranschaulichen, wie Sie ein Win32-Handle abrufen und zum Lesen und Schreiben von FILESTREAM BLOB-Daten verwenden.  
  
 [!code-csharp[FILESTREAM#FS_CS_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cs/filestream.cs#fs_cs_readandwriteblob)]  
  
 [!code-vb[FILESTREAM#FS_VB_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/vb/filestream.vb#fs_vb_readandwriteblob)]  
  
 [!code-cpp[FILESTREAM#FS_CPP_WriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_writeblob)]  
  
##  <a name="best"></a> Bewährte Methoden für Anwendungsentwurf und Implementierung  
  
-   Wenn Sie Anwendungen entwerfen und implementieren, die FILESTREAM verwenden, beachten Sie die folgenden Richtlinien:  
  
-   Verwenden Sie NULL statt 0x, um eine nicht initialisierte FILESTREAM-Spalte darzustellen. Der 0x-Wert bewirkt, dass eine Datei erstellt wird. Bei NULL ist dies nicht der Fall.  
  
-   Vermeiden Sie Einfüge- und Löschvorgänge in Tabellen, die FILESTREAM-Spalten ungleich NULL enthalten. Bei Einfüge- und Löschvorgängen können die FILESTREAM-Tabellen geändert werden, die für Garbage Collection verwendet werden. Dies kann dazu führen, dass die Leistung einer Anwendung mit der Zeit nachlässt.  
  
-   Verwenden Sie in Anwendungen, die Replikation verwenden, NEWSEQUENTIALID() statt NEWID(). NEWSEQUENTIALID() erzielt in diesen Anwendungen bei der GUID-Generierung eine bessere Leistung als NEWID().  
  
-   Die FILESTREAM-API ist für Win32-Streamingzugriff auf Daten vorgesehen. Vermeiden Sie die Verwendung von [!INCLUDE[tsql](../../includes/tsql-md.md)] zum Lesen oder Schreiben von FILESTREAM-BLOBs (Binary Large Objects), die größer als 2 MB sind. Wenn Sie BLOB-Daten aus [!INCLUDE[tsql](../../includes/tsql-md.md)]lesen oder schreiben müssen, stellen Sie sicher, dass alle BLOB-Daten verarbeitet werden, bevor Sie versuchen, den FILESTREAM-BLOB über Win32 zu öffnen. Werden nicht alle [!INCLUDE[tsql](../../includes/tsql-md.md)] -Daten verarbeitet, schlagen möglicherweise alle folgenden FILESTREAM-Vorgänge zum Öffnen oder Schließen fehl.  
  
-   Vermeiden Sie [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, die FILESTREAM-BLOBs aktualisieren oder diesen Daten anfügen bzw. voranstellen. Dies bewirkt, dass die BLOB-Daten in die Datenbank tempdb und anschließend zurück in eine neue physische Datei gespoolt werden.  
  
-   Vermeiden Sie, kleine BLOB-Updates an ein FILESTREAM-BLOB anzufügen. Jeder Anfügevorgang bewirkt, dass die zugrunde liegenden FILESTREAM-Dateien kopiert werden. Wenn eine Anwendung kleine BLOBs anfügen muss, schreiben Sie die BLOBs in eine `varbinary(max)`-Spalte, und führen Sie dann einen einzelnen Schreibvorgang für den FILESTREAM-BLOB durch, wenn die Anzahl der BLOBs eine vorher festgelegte Beschränkung erreicht.  
  
-   Vermeiden Sie, die Datenlänge von vielen BLOB-Dateien in einer Anwendung abzurufen. Dies ist ein zeitaufwendiger Vorgang, da die Größe nicht in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]gespeichert wird. Wenn Sie die Länge einer BLOB-Datei festlegen müssen, verwenden Sie die [!INCLUDE[tsql](../../includes/tsql-md.md)] -DATALENGTH()-Funktion, um die Größe des BLOB zu bestimmen, wenn dieses geschlossen ist. DATALENGTH() öffnet die BLOB-Datei nicht, um deren Größe zu bestimmen.  
  
-   Wenn eine Anwendung das SMB (Server Message Block)-Protokoll verwendet, sollten FILESTREAM-BLOB-Daten in einem Vielfachen von 60 KB gelesen werden, um die Leistung zu optimieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Vermeiden von Konflikten mit Datenbankvorgängen in FILESTREAM-Anwendungen](avoid-conflicts-with-database-operations-in-filestream-applications.md)   
 [Zugreifen auf FILESTREAM-Daten mit OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md)   
 [Binary Large Object &#40;BLOB&#41;-Daten &#40;SQL Server&#41;](binary-large-object-blob-data-sql-server.md)   
 [Vornehmen von Teilupdates an FILESTREAM-Daten](make-partial-updates-to-filestream-data.md)  
  
  
