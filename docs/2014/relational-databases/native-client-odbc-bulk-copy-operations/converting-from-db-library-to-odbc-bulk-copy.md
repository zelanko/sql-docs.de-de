---
title: Umstellen von DB-Library in ODBC-Massen Kopiervorgänge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- converting DB-Library to ODBC bulk copy
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], DB-Library bulk copy
- ODBC, bulk copy operations
- DB-Library bulk copy
ms.assetid: 0bc15bdb-f19f-4537-ac6c-f249f42cf07f
author: rothja
ms.author: jroth
ms.openlocfilehash: 29a8ee59db4cade8cc3ddf649b54d4c2c47e87ee
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021322"
---
# <a name="converting-from-db-library-to-odbc-bulk-copy"></a>Konvertieren von DB-Library-Programmen zum Massenkopieren in ODBC-Programme
  Die Umstellung eines DB-Library-Massen Kopier Programms in ODBC ist einfach, da die vom Native Client-ODBC-Treiber unterstützten Massen Kopierfunktionen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit den DB-Library-Funktionen zum Massen kopieren vergleichbar sind, mit den folgenden Ausnahmen:  
  
-   DB-Library-Anwendungen übergeben als ersten Parameter von Funktionen zum Massenkopieren einen Zeiger auf eine DBPROCESS-Struktur. In ODBC-Anwendungen wird der DBPROCESS-Zeiger durch ein ODBC-Verbindungshandle ersetzt.  
  
-   DB-Library-Anwendungen **BCP_SETL** vor dem Herstellen einer Verbindung, um Massen Kopiervorgänge für einen DBPROCESS zu aktivieren. ODBC-Anwendungen aufrufen stattdessen [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) , bevor Sie eine Verbindung herstellen, um Massen Vorgänge für ein Verbindungs Handle zu aktivieren:  
  
    ```  
    SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP,  
        (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
    ```  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt keine DB-Library-Nachrichten-und Fehlerhandler. Sie müssen **SQLGetDiagRec** aufrufen, um Fehler und Nachrichten zu erhalten, die von den ODBC-Funktionen zum Massen kopieren ausgelöst werden. Die ODBC-Versionen der Massenkopierfunktionen geben die Standardrückgabecodes SUCCEED bzw. FAILED für das Massenkopieren zurück statt der Rückgabecodes im ODBC-Stil, wie SQL_SUCCESS oder SQL_ERROR.  
  
-   Die für den DB-Library- [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*varlen* -Parameter angegebenen Werte werden anders interpretiert als der ODBC- **bcp_bind**_cbData_ -Parameter.  
  
    |Angegebene Bedingung|DB-Library- *varlen* -Wert|ODBC *cbData* -Wert|  
    |-------------------------|--------------------------------|-------------------------|  
    |Angabe von NULL-Werten|0|-1 (SQL_NULL_DATA)|  
    |Angabe von variablen Daten|-1|-10 (SQL_VARLEN_DATA)|  
    |Zeichen oder binäre Zeichenfolge mit der Länge 0|Nicht verfügbar|0|  
  
     In DB-Library gibt der *varlen* -Wert-1 an, dass Daten variabler Länge angegeben werden, die in den ODBC- *cbData* so interpretiert werden, dass nur NULL-Werte angegeben werden. Ändern Sie alle DB-Library- *varlen* -Spezifikationen von-1 in SQL_VARLEN_DATA und alle *varlen* -Spezifikationen von 0 in SQL_NULL_DATA.  
  
-   Die **bcp \_ Colf**-_Datei ( \_ Collen_ ) der DB-Library und der ODBC- [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)*cbUserData* haben das gleiche Problem wie die oben genannten Parameter **bcp_bind**_varlen_ und *cbData* . Ändern Sie alle DB-Library- *file_collen* Spezifikationen von-1 in SQL_VARLEN_DATA und alle *file_collen* Spezifikationen von 0 bis SQL_NULL_DATA.  
  
-   Der *iValue* -Parameter der ODBC- [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) Funktion ist ein void-Zeiger. In DB-Library war *iValue* eine ganze Zahl. Konvertieren Sie die Werte für den ODBC *iValue* in void *.  
  
-   Die **bcp_control** Option BCPMAXERRS gibt an, wie viele einzelne Zeilen Fehler aufweisen können, bevor ein Massen Kopiervorgang fehlschlägt. Der Standardwert für BCPMAXERRS ist 0 (Fehler beim ersten Fehler) in der DB-Library-Version von **bcp_control** und 10 in der ODBC-Version. DB-Library-Anwendungen, die vom Standardwert 0 zum Beenden eines Massen Kopiervorgangs abhängen, müssen so geändert werden, dass der ODBC- **bcp_control** aufgerufen wird, um BCPMAXERRS auf 0 (null) festzulegen.  
  
-   Die ODBC- **bcp_control** Funktion unterstützt die folgenden Optionen, die von der DB-Library-Version von **bcp_control**nicht unterstützt werden:  
  
    -   BCPODBC  
  
         Wenn diese Einstellung auf true festgelegt ist, wird angegeben, dass die im Zeichenformat gespeicherten Werte **DateTime** und **smalldatetime** das ODBC-Zeitstempel-escapesequenzpräfix und-Suffix aufweisen Dies gilt nur für BCP_OUT-Vorgänge.  
  
         Wenn BCPODBC auf false festgelegt ist, wird ein in eine Zeichenfolge konvertierter **DateTime** -Wert wie folgt ausgegeben:  
  
        ```  
        1997-01-01 00:00:00.000  
        ```  
  
         Wenn BCPODBC auf true festgelegt ist, wird der gleiche **DateTime** -Wert wie folgt ausgegeben:  
  
        ```  
        {ts '1997-01-01 00:00:00.000' }  
        ```  
  
    -   BCPKEEPIDENTITY  
  
         Durch die Festlegung dieser Option auf TRUE wird angegeben, dass Massenkopierfunktionen Datenwerte einfügen, die für Spalten mit einer IDENTITY-Einschränkung bereitgestellt werden. Wenn dies nicht festgelegt ist, werden neue Identitätswerte für die eingefügten Zeilen generiert.  
  
    -   BCPHINTS  
  
         Gibt verschiedene Optimierungen für das Massenkopieren an. Diese Option kann in Version 6.5 und früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht verwendet werden.  
  
    -   BCPFILECP  
  
         Gibt die Codepage für die Datendatei des Massenkopiervorgangs an.  
  
    -   BCPUNICODEFILE  
  
         Gibt an, dass eine Datendatei für das Massenkopieren im Zeichenmodus eine Unicode-Datei ist.  
  
-   Die ODBC- **bcp_colfmt** Funktion unterstützt den *file_type* -Indikator von SQLCHAR nicht, da Sie mit der ODBC SQLCHAR typedef in Konflikt steht. Verwenden Sie stattdessen SQLCHARACTER für **bcp_colfmt**.  
  
-   In den ODBC-Versionen der Funktionen zum Massen kopieren ist das Format für das Arbeiten mit **DateTime** -und **smalldatetime** -Werten in Zeichen folgen das ODBC-Format yyyy-mm-dd hh: mm: SS. sss;. **smalldatetime** -Werte verwenden das ODBC-Format yyyy-mm-dd hh: mm: SS.  
  
     Die DB-Library-Versionen der Funktionen zum Massen kopieren akzeptieren **DateTime** -und **smalldatetime** -Werte in Zeichen folgen unter Verwendung verschiedener Formate:  
  
    -   Das Standardformat ist *mmm DD JJJJ HH: mmxx* , wobei *xx* entweder am oder PM steht.  
  
    -   **DateTime** -und **smalldatetime** -Zeichen folgen in einem beliebigen Format, das von der DB-Library-Funktion **DBConvert** unterstützt wird.  
  
    -   Wenn das Feld **internationale Einstellungen verwenden** auf der Registerkarte DB-Library- **Optionen** des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Netzwerk-Hilfsprogramms aktiviert ist, akzeptieren die DB-Library-Massen Kopierfunktionen auch Datumsangaben in dem regionalen Datumsformat, das für die Gebiets Schema Einstellung der Client Computer Registrierung definiert ist.  
  
     Die DB-Library-Funktionen zum Massen kopieren akzeptieren die ODBC **DateTime** -und **smalldatetime** -Formate nicht.  
  
     Wenn das SQL_SOPT_SS_REGIONALIZE-Anweisungsattribut auf SQL_RE_ON festgelegt wurde, akzeptieren die ODBC-Funktionen zum Massenkopieren auch Datumsangaben in dem regionalen Datumsformat, das für die Einstellung des Gebietsschemas in der Registrierung des Clientcomputers definiert wurde.  
  
-   Beim Ausgeben von **Money** -Werten im Zeichenformat stellen ODBC-Funktionen zum Massen kopieren vier Ziffern der Genauigkeit und keine Komma Trennzeichen bereit. DB-Library-Versionen bieten nur zwei Ziffern der Genauigkeit und enthalten die Komma Trennzeichen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Massen Kopier Vorgängen &#40;ODBC-&#41;](performing-bulk-copy-operations-odbc.md)   
 [Bulk Copy Functions](../native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
