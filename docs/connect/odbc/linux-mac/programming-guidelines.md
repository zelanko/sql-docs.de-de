---
title: Programmierrichtlinien (ODBC Driver for SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/12/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 45d1fc9d06dd814e4ee6d80ec5ecbbe9e58d09c3
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798750"
---
# <a name="programming-guidelines"></a>Programmierrichtlinien

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Die Features für die Programmierung des [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter macOS und Linux basieren auf ODBC in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ([SQL Server Native Client (ODBC)](https://go.microsoft.com/fwlink/?LinkID=134151)). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client basiert auf ODBC in Windows Data Access Components ([Referenz für ODBC-Programmierer](https://go.microsoft.com/fwlink/?LinkID=45250)).  

Eine ODBC-Anwendung kann Multiple Active Result Sets (MARS) und andere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifische Features verwenden, indem `/usr/local/include/msodbcsql.h` nach den unixODBC-Headern (`sql.h`, `sqlext.h`, `sqltypes.h` und `sqlucode.h`) eingefügt wird. Verwenden Sie anschließend die gleichen symbolischen Namen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifische Elemente, die Sie auch in Ihrer Windows-ODBC-Anwendung verwenden würden.

## <a name="available-features"></a>Verfügbare Funktionen  
Die folgenden Abschnitte aus der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client Dokumentation für ODBC ([SQL Server Native Client (ODBC)](https://go.microsoft.com/fwlink/?LinkID=134151)) sind gültig, wenn der ODBC-Treiber unter macOS und Linux verwendet wird:  

-   [Kommunikation mit SQL Server (ODBC)](https://msdn.microsoft.com/library/ms131692.aspx)  
-   [Verbindungs- und Abfragetimeout-Unterstützung](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
-   [Cursor](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
-   [Datums-/Uhrzeitverbesserungen (ODBC)](https://msdn.microsoft.com/library/bb677319.aspx)  
-   [Ausführen von Abfragen (ODBC)](https://msdn.microsoft.com/library/ms131677.aspx)  
-   [Behandlung von Fehlern und Meldungen](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
-   [Kerberos-Authentifizierung](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md)  
-   [Große benutzerdefinierte CLR-Typen (ODBC)](https://msdn.microsoft.com/library/bb677316.aspx)  
-   [Ausführen von Transaktionen (ODBC) (mit Ausnahme der verteilten Transaktionen)](https://msdn.microsoft.com/library/ms131706.aspx)  
-   [Verarbeiten von Ergebnissen (ODBC)](https://msdn.microsoft.com/library/ms130812.aspx)  
-   [Ausführen gespeicherter Prozeduren](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)
-   [Unterstützung für Spalten mit geringer Dichte (ODBC)](https://msdn.microsoft.com/library/cc280357.aspx)
-   [SSL-Verschlüsselung](../../../relational-databases/native-client/features/using-encryption-without-validation.md)
-   [Table valued parameters (Tabellenwertparameter)](https://docs.microsoft.com/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [UTF-8 und UTF-16 für die Befehls- und Daten-API](https://msdn.microsoft.com/library/ff878241.aspx)
-   [Verwenden von Katalogfunktionen](../../../relational-databases/native-client/odbc/using-catalog-functions.md)  

## <a name="unsupported-features"></a>Nicht unterstützte Funktionen

Die Funktionsweise der folgenden Features wurde in diesem Release des ODBC-Treibers für macOS und Linux überprüft:

-   Failoverclusterverbindung
-   [Transparente Netzwerk-IP-Adressauflösung](https://docs.microsoft.com/sql/connect/odbc/linux/using-transparent-network-ip-resolution) (vor ODBC-Treiber 17)
-   [Erweiterte Treiberablaufverfolgung](https://blogs.msdn.microsoft.com/mattn/2012/05/15/enabling-advanced-driver-tracing-for-the-sql-native-client-odbc-drivers/)

Die folgenden Features sind nicht in dieser Version des ODBC-Treibers für macOS und Linux verfügbar: 

-   Verteilte Transaktionen (das Attribut SQL_ATTR_ENLIST_IN_DTC wird nicht unterstützt)  
-   Datenbankspiegelung  
-   FILESTREAM  
-   Leistungsprofilerstellung des ODBC-Treibers, erläutert in [SQLSetConnectAttr](https://go.microsoft.com/fwlink/?LinkId=234099), sowie die folgenden leistungsbezogenen Verbindungsattribute:  
    -   SQL_COPT_SS_PERF_DATA  
    -   SQL_COPT_SS_PERF_DATA_LOG  
    -   SQL_COPT_SS_PERF_DATA_LOG_NOW  
    -   SQL_COPT_SS_PERF_QUERY  
    -   SQL_COPT_SS_PERF_QUERY_INTERVAL  
    -   SQL_COPT_SS_PERF_QUERY_LOG  
-   SQLBrowseConnect  
-   C-Intervall-Typen, wie z.B. SQL_C_INTERVAL_YEAR_TO_MONTH (dokumentiert in [-Datentypbezeichnungen und Deskriptoren](https://msdn.microsoft.com/library/ms716351(VS.85).aspx)), werden derzeit nicht unterstützt.
-   Der Wert SQL_CUR_USE_ODBC des Attributs SQL_ATTR_ODBC_CURSORS der Funktion SQLSetConnectAttr.

## <a name="character-set-support"></a>Zeichensatzunterstützung

Für ODBC-Treiber 13 und 13.1 müssen die SQLCHAR-Daten die UTF-8-Codierung aufweisen. Es werden keine weiteren Codierungen unterstützt.

Für ODBC-Treiber 17 werden die folgenden Zeichensätze bzw. Codierungen für SQLCHAR-Daten unterstützt:

|Name|und Beschreibung|
|-|-|
|UTF-8|Unicode|
|CP437|MS-DOS-Latin-US|
|CP850|MS-DOS-Latin-1|
|CP874|Lateinisch/Thailändisch|
|CP932|Japanisch (Shift_JIS)|
|CP936|Chinesisch (vereinfacht) (GBK)|
|CP949|Koreanisch, EUC-KR|
|CP950|Chinesisch (traditionell) (Big5)|
|CP1251|Kyrillisch|
|CP1253|Griechisch|
|CP1256|Arabisch|
|CP1257|Baltisch|
|CP1258|Vietnamesisch|
|ISO-8859-1 / CP1252|Latin-1|
|ISO-8859-2 / CP1250|Latin-2|
|ISO-8859-3|Latin-3|
|ISO-8859-4|Latin-4|
|ISO-8859-5|Lateinisch/Kyrillisch|
|ISO-8859-6|Lateinisch/Arabisch|
|ISO-8859-7|Lateinisch/Griechisch|
|ISO-8859-8 / CP1255|Hebräisch|
|ISO-8859-9 / CP1254|Türkisch|
|ISO-8859-13|Latin-7|
|ISO-8859-15|Latin-9|

Wenn die Verbindung hergestellt wird, ermittelt der Treiber das aktuelle Gebietsschema des Prozesses, in dem er geladen wurde. Wenn eine der oben aufgeführten Codierungen verwendet wird, verwendet der Treiber diese Codierung für SQLCHAR-Daten (schmale Zeichen). Andernfalls wird standardmäßig die UTF-8-Codierung verwendet. Da alle Prozesse standardmäßig im Gebietsschema „C“ gestartet werden (und der Treiber daher standardmäßig die UTF-8-Codierung verwendet), sollte die Funktion **setlocale** zum ordnungsgemäßen Festlegen des Gebietsschemas verwendet werden, bevor die Verbindung hergestellt wird. Hierzu muss entweder das Gebietsschema explizit festgelegt oder eine leere Zeichenfolge (z. B. `setlocale(LC_ALL, "")`) verwendet werden, um die Gebietsschemaeinstellungen der Umgebung zu verwenden.

Daher werden Benutzern des ODBC-Treibers 17, die ein Upgrade von Version 13 oder 13.1 ausgeführt haben, in herkömmlichen Linux- oder Mac-Umgebungen keine Unterschiede auffallen, wenn die UTF-8-Codierung verwendet wird. Allerdings müssen Anwendungen, für die mithilfe von `setlocale()` eine andere Codierung aus der obigen Liste festgelegt wurde, diese Codierung anstelle der UTF-8-Codierung für Daten für und aus dem Treiber verwenden.

SQLWCHAR-Daten müssen UTF-16LE (Little Endian) sein.

Wenn ein SQL-Typ mit schmalen Zeichen wie SQL_VARCHAR festgelegt ist und Eingabeparameter mit SQLBindParameter eingebunden werden, konvertiert der Treiber die bereitgestellten Daten aus der Codierung des Clients in die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Standardcodierung (in der Regel Codepage 1252). Für Ausgabeparameter konvertiert der Treiber die in den Sortierungsinformationen festgelegte Codierung, die den Daten zugeordnet ist, in die Codierung des Clients. Es ist jedoch Datenverlust möglich. Zeichen der Quellcodierung, die nicht in der Zielcodierung angezeigt werden können, werden in Fragezeichen („?“) konvertiert.

Legen Sie einen Unicode-SQL-Zeichentyp wie SQL_NVARCHAR fest, um diese Datenverluste beim Einbinden von Eingabeparametern zu vermeiden. In diesem Fall konvertiert der Treiber die Codierung des Clients in die UTF-16-Codierung, die alle Unicode-Zeichen darstellen kann. Darüber hinaus muss die Zielspalte oder der Zielparameter auf dem Server auch entweder einem Unicode-Typ (**nchar**, **nvarchar**, **ntext**) oder einer Sortierung bzw. Codierung entsprechen, die alle Zeichen der ursprünglichen Quelldaten darstellen kann. Legen Sie einen Unicode-SQL-Typ und entweder einen Unicode-C-Typ (SQL_C_WCHAR), wodurch der Treiber die Daten in der UTF-16-Codierung zurückgibt, oder einen schmalen C-Typ fest, und stellen Sie sicher, dass die Codierung des Clients alle Zeichen der Quelldaten darstellen kann (dies wird mit der UTF-8-Codierung immer gewährleistet), um Datenverlust bei Ausgabeparametern zu vermeiden.

Weitere Informationen zur Sortierung und Codierung finden Sie unter [Sortierung und Unicode-Unterstützung](../../../relational-databases/collations/collation-and-unicode-support.md).

Zwischen Windows und mehreren Versionen der iconv-Bibliothek unter Linux und macOS gibt es einige Unterschiede bei der Konvertierung der Codierung. Textdaten in der Codepage 1255 (Hebräisch) verfügen über einen Codepunkt (0xCA), der sich bei der Konvertierung in Unicode anders verhält. Unter Windows wird das Zeichen in den UTF-16-Codepunkt 0x05BA konvertiert. Unter macOS und Linux wird es bei libiconv-Versionen vor Version 1.15 in 0x00CA konvertiert. Zeichen, die unter Linux mit iconv-Bibliotheken hinzugefügt werden, die die Revision von Big5/CP950 (namens `BIG5-2003`) von 2003 nicht unterstützen, werden nicht ordnungsgemäß konvertiert. In der Codepage 932 (Japanisch, Shift_JIS) unterscheidet sich das Ergebnis der Decodierung von Zeichen, die nicht ursprünglich im Codierungsstandard definiert wurden, ebenfalls. Zum Beispiel wird das Byte 0x80 unter Windows in U+0080 konvertiert, jedoch kann es je nach iconv-Version unter Linux und macOS auch in U+30FB konvertiert werden.

Im ODBC-Treiber 13 und 13.1 werden Daten beschädigt, wenn UTF-8-Mehrbytezeichen oder UTF-16-Ersatzzeichen auf SQLPutData-Puffer aufgeteilt werden. Für das Streamen von SQLPutData, verwenden Sie Puffer, die nicht in partiellen Zeichencodierungen enden. Diese Einschränkung wurde mit dem Version 17 des ODBC-Treibers entfernt.

## <a name="additional-notes"></a>Weitere Hinweise  

1.  Sie können eine dedizierte Administratorverbindung (DAC) herstellen, indem Sie die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Authentifizierung und **host,port**verwenden. Ein Mitglied der Sysadmin-Rolle muss zunächst den DAC-Port ermitteln. Weitere Informationen dazu finden Sie unter [Diagnoseverbindung für Datenbankadministratoren](https://docs.microsoft.com/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators#dac-port). Wenn beispielsweise der DAC-Port „33000“ ist, können Sie mit `sqlcmd` wie folgt eine Verbindung herstellen:  

    ```
    sqlcmd -U <user> -P <pwd> -S <host>,33000
    ```

    > [!NOTE]  
    > DAC-Verbindungen müssen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Authentifizierung verwenden.  
    
2.  Der UnixODBC-Treiber-Manager gibt „ Attribut-/Optionsbezeichner ungültig“ für alle Anweisungsattribute zurück, wenn sie über SQLSetConnectAttr übergeben werden. Wenn SQLSetConnectAttr unter Windows einen Anweisungsattributwert erhält, verursacht dieser, dass der Treiber diesen Wert für alle aktiven Anweisungen festlegt, die dem Verbindungshandle untergeordnet sind.  

## <a name="see-also"></a>Weitere Informationen  
[Häufig gestellte Fragen](../../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)

[Bekannte Probleme in dieser Version des Treibers](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[Versionsanmerkungen](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)
