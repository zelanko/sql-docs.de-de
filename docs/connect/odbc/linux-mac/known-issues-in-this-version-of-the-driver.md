---
title: Bekannte Probleme in dieser Version des Treibers für SQLServer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/14/2018
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
ms.openlocfilehash: 25ebc4837eb37604a45e98112fa5fc24bdb3e69b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742998"
---
# <a name="known-issues-in-this-version-of-the-driver"></a>Bekannte Probleme in dieser Version des Treibers

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Dieser Artikel enthält eine Liste der bekannten Probleme mit der Microsoft Odbcdriver 13, 13.1 und 17 für SQL Server unter Linux und MacOS.

Weitere Probleme werden auf dem [Microsoft ODBC Driver-Teamblog](http://blogs.msdn.com/b/sqlnativeclient/)gepostet.  

- Windows, Linux und macOS konvertieren Zeichen aus der Private Use Area oder benutzerdefinierte Zeichen unterschiedlich. Konvertierungen, die auf dem Server in [!INCLUDE[tsql](../../../includes/tsql-md.md)] ausgeführt werden, verwenden die Microsoft-Konvertierungsbibliothek. Konvertierungen im Treiber verwenden, die Konvertierung-Bibliotheken für Windows, Linux oder MacOS. Jede dieser Bibliotheken führt möglicherweise zu unterschiedlichen Ergebnissen, wenn die Konvertierung ausgeführt wird. Weitere Informationen finden Sie unter [EUDC-Zeichen und Zeichen des benutzerdefinierten Bereichs](/windows/desktop/Intl/end-user-defined-characters).

- Wenn der Client, die Codierung UTF-8 ist, konvertiert der Treiber-Manager immer korrekt von UTF-8 in UTF-16 nicht. Derzeit tritt auf, Beschädigung von Daten, wenn ein oder mehrere Zeichen in der Zeichenfolge keine gültige UTF-8-Zeichen sind. ASCII-Zeichen werden korrekt zugeordnet. Der Treiber-Manager versucht, diese Konvertierung beim Aufruf der SQLCHAR-Versionen der ODBC-API (z.B. SQLDriverConnectA) durchzuführen. Der Treiber-Manager wird nicht versuchen, diese Konvertierung beim Aufruf der SQLWCHAR-Versionen der ODBC-API (zum Beispiel SQLDriverConnectW) durchzuführen.  

- Die *ColumnSize* Parameter **SQLBindParameter** bezieht sich auf die Anzahl der Zeichen in der SQL-Typ, während *Pufferlänge* ist die Anzahl der Bytes in der Anwendung Puffer. Wenn jedoch der SQL-Datentyp `varchar(n)` oder `char(n)` ist und die Anwendung den Parameter als SQL_C_CHAR oder SQL_C_VARCHAR bindet, und wenn die Zeichencodierung des Clients UTF-8 ist, erhalten Sie vom Treiber eventuell die Fehlermeldung „Die Zeichenfolgedaten wurden rechts abgeschnitten.“, selbst wenn der Wert von *ColumnSize* auf die Größe des Datentyps auf dem Server ausgerichtet ist. Dieser Fehler tritt auf, da Konvertierungen zwischen zeichencodierungen, die Länge der Daten ändern können. Z. B. eine richtige Apostroph-Zeichen (U + 2019) codiert ist, in der CP-1252 als 0x92 wird das einzelne Byte, aber in UTF-8 als die 3 Bytes bestehende Sequenz 0xe2 0x80 0x99.

Wenn die Codierung UTF-8 ist und Sie 1 für beide angeben, z. B. *Pufferlänge* und *ColumnSize* in **SQLBindParameter** für die Out-Parameter, dann versuchen, eine Rufen Sie das vorherige Zeichen, die in gespeicherten eine `char(1)` Spalte auf dem Server (mit CP-1252), der Treiber versucht, die sie in der 3-Byte-UTF-8-Codierung konvertieren, aber nicht das Ergebnis in einem 1-Byte-Puffer passen. In der anderen Richtung verglichen *ColumnSize* mit der *Pufferlänge* in **SQLBindParameter** vor der Konvertierung zwischen den verschiedenen Codepages auf der Client und Server. Da ein *ColumnSize* von 1 kleiner ist als eine *Pufferlänge* von (z. B.) 3, generiert der Treiber einen Fehler. Um diesen Fehler zu vermeiden, stellen Sie sicher, die die Länge der Daten nach der Konvertierung in den angegebenen Puffer oder in der Spalte passt. Beachten Sie, dass *ColumnSize* darf nicht größer als 8000 für die `varchar(n)` Typ.

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md)  
[Versionsanmerkungen](../../../connect/odbc/linux-mac/release-notes.md)  

