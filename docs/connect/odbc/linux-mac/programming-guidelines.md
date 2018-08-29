---
title: Programmierrichtlinien (ODBC-Treiber für SQLServer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3068d2a796e7e28e4eda58514cc316fe504bbce3
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "42786705"
---
# <a name="programming-guidelines"></a>Programmierrichtlinien

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Die Features für die Programmierung des [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter macOS und Linux basieren auf ODBC in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ([SQL Server Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client basiert auf ODBC in Windows Data Access Components ([Referenz für ODBC-Programmierer](http://go.microsoft.com/fwlink/?LinkID=45250)).  

Eine ODBC-Anwendung verwenden kann, Multiple Active Result Sets (MARS) und andere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bestimmte Funktionen dazu `/usr/local/include/msodbcsql.h` nach dem einschließen des UnixODBC-Header (`sql.h`, `sqlext.h`, `sqltypes.h`, und `sqlucode.h`). Verwenden Sie anschließend die gleichen symbolischen Namen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifische Elemente, die Sie auch in Ihrer Windows-ODBC-Anwendung verwenden würden.

## <a name="available-features"></a>Verfügbare Funktionen  
Die folgenden Abschnitte aus der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client Dokumentation für ODBC ([SQL Server Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)) sind gültig, wenn der ODBC-Treiber unter macOS und Linux verwendet wird:  

-   [Kommunikation mit SQL Server (ODBC)](http://msdn.microsoft.com/library/ms131692.aspx)  
-   [Verbindungs- und Abfragetimeout-Unterstützung](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
-   [Cursor](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
-   [Datums-/Uhrzeitverbesserungen (ODBC)](http://msdn.microsoft.com/library/bb677319.aspx)  
-   [Ausführen von Abfragen (ODBC)](http://msdn.microsoft.com/library/ms131677.aspx)  
-   [Behandlung von Fehlern und Meldungen](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
-   [Kerberos-Authentifizierung](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md)  
-   [Große benutzerdefinierte CLR-Typen (ODBC)](http://msdn.microsoft.com/library/bb677316.aspx)  
-   [Ausführen von Transaktionen (ODBC) (mit Ausnahme der verteilten Transaktionen)](http://msdn.microsoft.com/library/ms131706.aspx)  
-   [Verarbeiten von Ergebnissen (ODBC)](http://msdn.microsoft.com/library/ms130812.aspx)  
-   [Ausführen gespeicherter Prozeduren](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)
-   [Unterstützung für Spalten mit geringer Dichte (ODBC)](http://msdn.microsoft.com/library/cc280357.aspx)
-   [SSL-Verschlüsselung](../../../relational-databases/native-client/features/using-encryption-without-validation.md)
-   [Table valued parameters (Tabellenwertparameter)](https://docs.microsoft.com/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [UTF-8 und UTF-16 für die Befehls- und Daten-API](http://msdn.microsoft.com/library/ff878241.aspx)
-   [Verwenden von Katalogfunktionen](../../../relational-databases/native-client/odbc/using-catalog-functions.md)  

## <a name="unsupported-features"></a>Nicht unterstützte Funktionen

Die folgenden Features wurden nicht ordnungsgemäß funktioniert in dieser Version des ODBC-Treibers unter MacOS und Linux überprüft:

-   Failover-Cluster-Verbindung
-   [Transparente Netzwerk-IP-Adressauflösung](https://docs.microsoft.com/sql/connect/odbc/linux/using-transparent-network-ip-resolution) (vor der ODBC-Treiber 17)
-   [Erweiterte Treiber-Ablaufverfolgung](https://blogs.msdn.microsoft.com/mattn/2012/05/15/enabling-advanced-driver-tracing-for-the-sql-native-client-odbc-drivers/)

Die folgenden Features sind nicht in dieser Version des ODBC-Treibers für macOS und Linux verfügbar: 

-   Verteilte Transaktionen (das Attribut SQL_ATTR_ENLIST_IN_DTC wird nicht unterstützt)  
-   Datenbankspiegelung  
-   FILESTREAM  
-   Leistungsprofilerstellung des ODBC-Treibers, erläutert in [SQLSetConnectAttr](http://go.microsoft.com/fwlink/?LinkId=234099), sowie die folgenden leistungsbezogenen Verbindungsattribute:  
    -   SQL_COPT_SS_PERF_DATA  
    -   SQL_COPT_SS_PERF_DATA_LOG  
    -   SQL_COPT_SS_PERF_DATA_LOG_NOW  
    -   SQL_COPT_SS_PERF_QUERY  
    -   SQL_COPT_SS_PERF_QUERY_INTERVAL  
    -   SQL_COPT_SS_PERF_QUERY_LOG  
-   SQLBrowseConnect  
-   C-Intervall-Typen, wie z.B. SQL_C_INTERVAL_YEAR_TO_MONTH (dokumentiert in [-Datentypbezeichnungen und Deskriptoren](http://msdn.microsoft.com/library/ms716351(VS.85).aspx)), werden derzeit nicht unterstützt.
-   Der Wert SQL_CUR_USE_ODBC des Attributs SQL_ATTR_ODBC_CURSORS der Funktion SQLSetConnectAttr.

## <a name="character-set-support"></a>Zeichensatzunterstützung

ODBC Driver 13 und 13.1 müssen SQLCHAR-Daten als UTF-8 sein. Keine andere Codierungen werden unterstützt.

Für ODBC Driver 17 werden die SQLCHAR-Daten in einem der folgenden Gruppen/zeichencodierung unterstützt:

|Name|und Beschreibung|
|-|-|
|UTF-8|Unicode|
|CP437|MS-DOS-Lateinisch US|
|CP850|MS-DOS-Latin-1|
|CP874|Lateinisch/Thai|
|CP932|Japanisch (Shift_JIS)|
|CP936|Chinesisch (vereinfacht) (GBK)|
|CP949|Koreanisch, EUC-KR|
|CP950|Chinesisch (traditionell) (Big5)|
|CP1251|Kyrillisch|
|CP1253|Griechisch|
|CP1256|Arabisch|
|CP1257|Baltisch|
|CP1258|Vietnamesisch|
|ISO-8859-1 / CP1252|Lateinisch-1|
|ISO-8859-2 / CP1250|Lateinisch-2|
|ISO-8859-3|Lateinisch-3|
|ISO-8859-4|Lateinisch-4|
|ISO-8859-5|Lateinisch/Kyrillisch|
|ISO-8859-6|Lateinisch/Arabisch|
|ISO-8859-7|Lateinisch/Griechisch|
|ISO-8859-8 / CP1255|Hebräisch|
|ISO-8859-9 / CP1254|Türkisch|
|ISO-8859-13|Lateinisch-7|
|ISO-8859-15|Lateinisch-9|

Beim Herstellen der Verbindung erkennt der Treiber das aktuelle Gebietsschema des Prozesses, die in der sie geladen wird. Wenn eine der oben genannten Codierungen verwendet wird, verwendet der Treiber mit diese Codierung für (schmale Zeichen) SQLCHAR-Daten; Andernfalls wird es standardmäßig in UTF-8. Da alle Prozesse im Gebietsschema "C", wird standardmäßig beginnen (und daher dazu führen, den Treiber Standard auf UTF-8 dass), wenn eine Anwendung eine der oben genannten Codierungen verwenden muss, muss bei Verwendung der **Setlocale** Funktion zum entsprechend vor dem Festlegen des Gebietsschemas Herstellen einer Verbindung; entweder, indem Sie das gewünschte Gebietsschema explizit angeben oder eine leere Zeichenfolge beispielsweise `setlocale(LC_ALL, "")` die gebietsschemaeinstellungen der Umgebung zu verwenden.

Daher werden Benutzer von ODBC Driver 17 von 13 "oder" 13.1 aktualisieren in einer typischen Linux- oder Mac-Umgebung, in dem die Codierung UTF-8 ist, keine Unterschiede beobachten. Anwendungen, die verwenden jedoch eine nicht-UTF-8-Codierung in der obigen Liste über `setlocale()` , Codierungen für Daten in einen/aus dem anstelle von UTF-8-Treiber verwenden müssen.

SQLWCHAR-Daten müssen UTF-16LE (Little Endian) sein.

Beim Binden von Eingabeparametern mit SQLBindParameter, wenn ein schmaler SQL eingeben, z. B. SQL_VARCHAR angegeben ist, konvertiert der Treiber die angegebenen Daten auf dem Client, der auf den Standardwert (in der Regel Codepage 1252) Codierung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Codierung. Für Output-Parameter konvertiert der Treiber aus der Codierung in die Sortierungsinformationen, die die Daten an den Client, die Codierung angegeben. Allerdings ist Datenverlust möglich – konvertiert Zeichen in die quellcodierung nicht darstellbar ist, in der zielcodierung in ein Fragezeichen ("?").

Um diese Datenverluste zu vermeiden, wenn Eingabeparameter gebunden, geben Sie einen Unicode SQL-Zeichentyp, z. B. SQL_NVARCHAR. In diesem Fall konvertiert der Treiber auf dem Client, der die Codierung in UTF-16, das alle Unicode-Zeichen darstellen, kann ein. Darüber hinaus der Zielspalte oder der Parameter auf dem Server zudem muss entweder einen Unicode-Datentyp (**Nchar**, **Nvarchar**, **Ntext**) oder einen mit einer Sortierung/Codierung können Stellen Sie alle Zeichen aus der ursprünglichen Datenquelle dar. Zur Vermeidung von Datenverlust mit Output-Parameter, geben Sie einen Unicode SQL-Typ, und ein Unicode-C geben Sie entweder (SQL_C_WCHAR), verursacht des zurückzugebenden Daten als UTF-16-Treibers; oder eine schmale C geben, und stellen Sie sicher, dass die Client-Codierung darstellen kann, alle Zeichen aus den Quelldaten (Dies ist immer möglich, mit UTF-8.)

Weitere Informationen zu Sortierungen und Codierungen finden Sie unter [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md).

Es gibt einige Codierung Konvertierung Unterschiede zwischen Windows und mehrere Versionen der Iconv-Bibliothek unter Linux und MacOS. Text-Daten in Codepage 1255 (Hebräisch) verfügt über einen Codepunkt (0xCA), die bei der Konvertierung in Unicode anders verhält. Auf Windows konvertiert dieses Zeichen dem UTF-16-Codepunkt des Werts 0x05BA. Unter MacOS und Linux mit Libiconv-Versionen vor 1.15 konvertiert in Werts 0x00CA. Unter Linux mit Iconv-Bibliotheken, die die 2003-Revision des Big5/CP950 nicht unterstützen (mit dem Namen `BIG5-2003`), Zeichen, die mit dieser Revision hinzugefügt werden nicht ordnungsgemäß konvertiert. In Codepage 932 (Japanisch, Shift-JIS) unterscheidet sich auch das Ergebnis der Decodierung von Zeichen, die ursprünglich nicht in die angegebene Codierung aus. Z. B. das Byte 0 x 80 konvertiert in U + 0080 auf Windows jedoch eventuell 30FB U + unter Linux und MacOS, je nach Iconv-Version.

Im ODBC-Treiber 13 und 13.1 werden Daten beschädigt, wenn UTF-8-Mehrbytezeichen oder UTF-16-Ersatzzeichen auf SQLPutData-Puffer aufgeteilt werden. Für das Streamen von SQLPutData, verwenden Sie Puffer, die nicht in partiellen Zeichencodierungen enden. Diese Einschränkung wurde mit ODBC Driver 17 entfernt.

## <a name="additional-notes"></a>Weitere Hinweise  

1.  Sie können eine dedizierte Administratorverbindung (DAC) herstellen, indem Sie die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Authentifizierung und **host,port**verwenden. Ein Mitglied der Sysadmin-Rolle muss zunächst den DAC-Port ermitteln. Finden Sie unter [Diagnoseverbindung für Datenbankadministratoren](https://docs.microsoft.com/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators#dac-port) ermitteln wie. Wenn beispielsweise der DAC-Port „33000“ ist, können Sie mit `sqlcmd` wie folgt eine Verbindung herstellen:  

    ```
    sqlcmd –U <user> -P <pwd> -S <host>,33000
    ```

    > [!NOTE]  
    > DAC-Verbindungen müssen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Authentifizierung verwenden.  
    
2.  Der UnixODBC-Treiber-Manager gibt „ Attribut-/Optionsbezeichner ungültig“ für alle Anweisungsattribute zurück, wenn sie über SQLSetConnectAttr übergeben werden. Wenn SQLSetConnectAttr unter Windows einen Anweisungsattributwert erhält, verursacht dieser, dass der Treiber diesen Wert für alle aktiven Anweisungen festlegt, die dem Verbindungshandle untergeordnet sind.  

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Häufig gestellte Fragen](../../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)

[Bekannte Probleme in dieser Version des Treibers](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[Versionsanmerkungen](../../../connect/odbc/linux-mac/release-notes.md)
