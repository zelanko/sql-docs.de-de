---
title: Bekannte Probleme in dieser Version des SQL Server-Treibers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/15/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- known issues
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 504b5264f44109060bff3b6e5e9a6fd4fca448e9
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "59042309"
---
# <a name="known-issues-in-this-version-of-the-driver"></a>Bekannte Probleme in dieser Version des Treibers

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Dieser Artikel enthält eine Liste der bekannten Probleme mit Microsoft ODBC Driver 13, 13.1 und 17 for SQL Server unter Linux und macOS.

Weitere Probleme werden auf dem [Microsoft ODBC Driver-Teamblog](https://blogs.msdn.com/b/sqlnativeclient/)gepostet.  

- Windows, Linux und macOS konvertieren Zeichen aus der Private Use Area oder benutzerdefinierte Zeichen unterschiedlich. Konvertierungen, die auf dem Server in [!INCLUDE[tsql](../../../includes/tsql-md.md)] ausgeführt werden, verwenden die Microsoft-Konvertierungsbibliothek. Konvertierungen im Treiber verwenden die Konvertierungsbibliotheken von Windows, Linux oder macOS. Jede dieser Bibliotheken führt möglicherweise zu unterschiedlichen Ergebnissen, wenn die Konvertierung ausgeführt wird. Weitere Informationen finden Sie unter [EUDC-Zeichen und Zeichen des benutzerdefinierten Bereichs](/windows/desktop/Intl/end-user-defined-characters).

- Wenn der Client die UTF-8-Codierung aufweist, führt der Treiber-Manager die Konvertierung von UTF-8 auf UTF-16 nicht immer ordnungsgemäß durch. Derzeit tritt Datenbeschädigung auf, wenn mindestens ein Zeichen in der Zeichenfolge kein gültiges UTF-8-Zeichen ist. ASCII-Zeichen werden ordnungsgemäß zugeordnet. Der Treiber-Manager versucht, diese Konvertierung beim Aufruf der SQLCHAR-Versionen der ODBC-API (z.B. SQLDriverConnectA) durchzuführen. Der Treiber-Manager wird nicht versuchen, diese Konvertierung beim Aufruf der SQLWCHAR-Versionen der ODBC-API (zum Beispiel SQLDriverConnectW) durchzuführen.  

- Der Parameter *ColumnSize* von **SQLBindParameter** bezieht sich auch die Anzahl von Zeichen im SQL-Typ, während *BufferLength* der Anzahl von Bytes im Puffer der Anwendung entspricht. Wenn jedoch der SQL-Datentyp `varchar(n)` oder `char(n)` ist und die Anwendung den Parameter als SQL_C_CHAR oder SQL_C_VARCHAR bindet, und wenn die Zeichencodierung des Clients UTF-8 ist, erhalten Sie vom Treiber eventuell die Fehlermeldung „Die Zeichenfolgedaten wurden rechts abgeschnitten.“, selbst wenn der Wert von *ColumnSize* auf die Größe des Datentyps auf dem Server ausgerichtet ist. Dieser Fehler tritt auf, weil Konvertierungen zwischen Zeichencodierungen die Länge der Daten ändern können. Ein rechtes Anführungszeichen (U+2019) wird beispielsweise in CP-1252 als das einzelne Byte „0x92“ codiert, während es in der UTF-8-Codierung jedoch als Sequenz der drei Bytes „0xe2“, „0x80“ und „0x99“ codiert wird.

Wenn Sie beispielsweise die UTF-8-Codierung verwenden, „1“ für *BufferLength* und *ColumnSize* für einen Out-Parameter in **SQLBindParameter** angeben und anschließend versuchen, das vorhergehende Zeichen abzurufen, das auf dem Server in einer `char(1)`-Spalte gespeichert ist (mit CP-1252), versucht der Treiber, ihn in die UTF-8-Codierung mit drei Bytes zu konvertieren. Das Ergebnis passt jedoch nicht in einen Puffer mit einem Byte. Andererseits wird *ColumnSize* mit dem Wert von *BufferLength* in **SQLBindParameter** verglichen, bevor die Konvertierung zwischen den verschiedenen Codepages für den Client und den Server durchgeführt wird. Da ein *ColumnSize* von 1 kleiner ist als eine *Pufferlänge* von (z. B.) 3, generiert der Treiber einen Fehler. Stellen Sie sicher, dass die Länge der Daten nach der Konvertierung in den angegebenen Puffer oder die Spalte passt, um diesen Fehler zu vermeiden. Beachten Sie, dass der Wert von *ColumnSize* mit dem Typ `varchar(n)` nicht größer als 8.000 sein darf.

## <a name="see-also"></a>Weitere Informationen  
[Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md)  
[Versionsanmerkungen](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)  

