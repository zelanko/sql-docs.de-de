---
title: Bekannte Probleme des ODBC-Treibers unter Linux und macOS
ms.date: 03/05/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- known issues
author: rothja
ms.author: jroth
ms.openlocfilehash: 9746456a4a38f2a19e485d1e17786073b97b243e
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79286434"
---
# <a name="known-issues-for-the-odbc-driver-on-linux-and-macos"></a>Bekannte Probleme des ODBC-Treibers unter Linux und macOS

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Dieser Artikel enthält eine Liste der bekannten Probleme mit Microsoft ODBC Driver 13, 13.1 und 17 for SQL Server unter Linux und macOS. Außerdem enthält er Schritte zur Behandlung von Konnektivitätsproblemen.

## <a name="known-issues"></a>Bekannte Probleme

Weitere Probleme werden auf dem [Microsoft ODBC Driver-Teamblog](https://blogs.msdn.com/b/sqlnativeclient/)gepostet.  

- Aufgrund von Einschränkungen der Systembibliothek unterstützt Alpine Linux weniger Zeichencodierungen und Schemas. Beispielsweise ist en_US.UTF-8 nicht verfügbar. Weitere Informationen finden Sie unter [Functional differences from glibc](https://wiki.musl-libc.org/functional-differences-from-glibc.html) (Funktionsbezogene Unterschiede zu glibc).

- Windows, Linux und macOS konvertieren Zeichen aus der Private Use Area oder benutzerdefinierte Zeichen unterschiedlich. Konvertierungen, die auf dem Server in [!INCLUDE[tsql](../../../includes/tsql-md.md)] ausgeführt werden, verwenden die Microsoft-Konvertierungsbibliothek. Konvertierungen im Treiber verwenden die Konvertierungsbibliotheken von Windows, Linux oder macOS. Jede dieser Bibliotheken führt möglicherweise zu unterschiedlichen Ergebnissen, wenn die Konvertierung ausgeführt wird. Weitere Informationen finden Sie unter [EUDC-Zeichen und Zeichen des benutzerdefinierten Bereichs](/windows/desktop/Intl/end-user-defined-characters).

- Wenn der Client die UTF-8-Codierung aufweist, führt der Treiber-Manager die Konvertierung von UTF-8 auf UTF-16 nicht immer ordnungsgemäß durch. Derzeit tritt Datenbeschädigung auf, wenn mindestens ein Zeichen in der Zeichenfolge kein gültiges UTF-8-Zeichen ist. ASCII-Zeichen werden ordnungsgemäß zugeordnet. Der Treiber-Manager versucht, diese Konvertierung beim Aufruf der SQLCHAR-Versionen der ODBC-API (z.B. SQLDriverConnectA) durchzuführen. Der Treiber-Manager wird nicht versuchen, diese Konvertierung beim Aufruf der SQLWCHAR-Versionen der ODBC-API (zum Beispiel SQLDriverConnectW) durchzuführen.  

- Der Parameter *ColumnSize* von **SQLBindParameter** bezieht sich auch die Anzahl von Zeichen im SQL-Typ, während *BufferLength* der Anzahl von Bytes im Puffer der Anwendung entspricht. Wenn jedoch der SQL-Datentyp `varchar(n)` oder `char(n)` ist und die Anwendung den Parameter als SQL_C_CHAR oder SQL_C_VARCHAR bindet, und wenn die Zeichencodierung des Clients UTF-8 ist, erhalten Sie vom Treiber eventuell die Fehlermeldung „Die Zeichenfolgedaten wurden rechts abgeschnitten.“, selbst wenn der Wert von *ColumnSize* auf die Größe des Datentyps auf dem Server ausgerichtet ist. Dieser Fehler tritt auf, weil Konvertierungen zwischen Zeichencodierungen die Länge der Daten ändern können. Ein rechtes Anführungszeichen (U+2019) wird beispielsweise in CP-1252 als das einzelne Byte „0x92“ codiert, während es in der UTF-8-Codierung jedoch als Sequenz der drei Bytes „0xe2“, „0x80“ und „0x99“ codiert wird.

Wenn Sie beispielsweise die UTF-8-Codierung verwenden, „1“ für *BufferLength* und *ColumnSize* für einen Out-Parameter in **SQLBindParameter** angeben und anschließend versuchen, das vorhergehende Zeichen abzurufen, das auf dem Server in einer `char(1)`-Spalte gespeichert ist (mit CP-1252), versucht der Treiber, ihn in die UTF-8-Codierung mit drei Bytes zu konvertieren. Das Ergebnis passt jedoch nicht in einen Puffer mit einem Byte. Andererseits wird *ColumnSize* mit dem Wert von *BufferLength* in **SQLBindParameter** verglichen, bevor die Konvertierung zwischen den verschiedenen Codepages für den Client und den Server durchgeführt wird. Da ein *ColumnSize* von 1 kleiner ist als eine *Pufferlänge* von (z. B.) 3, generiert der Treiber einen Fehler. Stellen Sie sicher, dass die Länge der Daten nach der Konvertierung in den angegebenen Puffer oder die Spalte passt, um diesen Fehler zu vermeiden. Beachten Sie, dass der Wert von *ColumnSize* mit dem Typ `varchar(n)` nicht größer als 8.000 sein darf.

## <a name="troubleshooting-connection-problems"></a><a id="connectivity"></a> Beheben von Verbindungsproblemen  

Falls Sie keine Verbindung mittels ODBC-Treiber mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herstellen können, verwenden Sie die folgenden Informationen, um das Problem zu identifizieren.  
  
Das häufigste Verbindungsproblem besteht darin, dass der unixODBC-Treiber-Manager doppelt installiert wurde. Durchsuchen Sie „/usr“ nach „libodbc\*.so\*“. Falls Sie mehr als eine Version der Datei sehen, haben Sie (möglicherweise) mehr als einen Treiber-Manager installiert. Ihre Anwendung verwendet eventuell die falsche Version.
  
Aktivieren Sie das Verbindungsprotokoll, indem Sie Ihre `/etc/odbcinst.ini`-Datei so bearbeiten, dass Sie den folgenden Bereich mit diesen Elementen enthält:

```
[ODBC]
Trace = Yes
TraceFile = (path to log file, or /dev/stdout to output directly to the terminal)
```  
  
Falls der Verbindungsversuch wieder fehlschlägt und Ihnen keine Protokolldatei angezeigt wird, gibt es (möglicherweise) zwei Kopien des Treiber-Managers auf Ihrem Computer. Andernfalls sollte die Ausgabe des Protokolls etwa so aussehen:  
  
```
[ODBC][28783][1321576347.077780][SQLDriverConnectW.c][290]  
        Entry:  
            Connection = 0x17c858e0  
            Window Hdl = (nil)  
            Str In = [DRIVER={ODBC Driver 13 for SQL Server};SERVER={contoso.com};Trusted_Connection={YES};WSID={mydb.contoso.com};AP...][length = 139 (SQL_NTS)]  
            Str Out = (nil)  
            Str Out Max = 0  
            Str Out Ptr = (nil)  
            Completion = 0  
        UNICODE Using encoding ASCII 'UTF8' and UNICODE 'UTF16LE'  
```  
  
Falls die ASCII-Zeichencodierung beispielsweise nicht UTF-8 ist: 
  
```
UNICODE Using encoding ASCII 'ISO8859-1' and UNICODE 'UCS-2LE'  
```  
  
Mehr als ein Treiber-Manager ist installiert und Ihre Anwendung verwendet den falschen, oder der Treiber-Manager wurde nicht korrekt erstellt.  
  
Weitere Informationen zum Beheben von Verbindungsproblemen finden Sie hier:  

- [Schritte zum Beheben von SQL-Konnektivitätsproblemen](https://docs.microsoft.com/archive/blogs/sql_protocols/steps-to-troubleshoot-sql-connectivity-issues)  
  
- [SQL Server 2005 Beheben von Konnektivitätsproblemen – Teil I](https://techcommunity.microsoft.com/t5/sql-server/sql-server-2005-connectivity-issue-troubleshoot-part-i/ba-p/383034)  
  
- [Konnektivitätsproblembehebung in SQL Server 2008 mit dem Konnektivitätsringpuffer](https://techcommunity.microsoft.com/t5/sql-server/connectivity-troubleshooting-in-sql-server-2008-with-the/ba-p/383393)  
  
- [Problembehebung für die SQL Server-Authentifizierung](https://docs.microsoft.com/archive/blogs/sqlsecurity/sql-server-authentication-troubleshooter)  

## <a name="next-steps"></a>Nächste Schritte

Installationsanweisungen für den ODBC-Treiber finden Sie in den folgenden Artikeln:

- [Installieren von Microsoft ODBC Driver for SQL Server unter Linux](installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Installieren von Microsoft ODBC Driver for SQL Server unter macOS](install-microsoft-odbc-driver-sql-server-macos.md)

Weitere Informationen finden Sie in den [Programmierrichtlinien](programming-guidelines.md) und den [Versionshinweisen](release-notes-odbc-sql-server-linux-mac.md).  
