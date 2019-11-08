---
title: bcp_setcolfmt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_setcolfmt
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_setcolfmt function
ms.assetid: afb47987-39e7-4079-ad66-e0abf4d4c72b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7e2942f60e1bb41edfcd2d474619867d35806660
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73782335"
---
# <a name="bcp_setcolfmt"></a>bcp_setcolfmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die **bcp_setcolfmt** -Funktion ersetzt die [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md). Beim Angeben der Spalten Sortierung muss die **bcp_setcolfmt** -Funktion verwendet werden. [bcp_setbulkmode](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md) kann verwendet werden, um mehr als ein Spalten Format anzugeben.  
  
 Diese Funktion bietet einen flexiblen Ansatz für das Angeben des Spaltenformats in einem Massenkopiervorgang. Sie wird verwendet, um einzelne Spaltenformatattribute festzulegen. Jeder **bcp_setcolfmt** -Aufrufsatz legt ein Spalten Format Attribut fest.  
  
 Die **bcp_setcolfmt** -Funktion gibt das Quell-oder Zielformat der Daten in einer Benutzerdatei an. Bei Verwendung als Quellformat gibt **bcp_setcolfmt** das Format einer vorhandenen Datendatei an, die als Datenquelle für Daten in einem Massen Kopiervorgang in eine Tabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird. Bei Verwendung als Zielformat wird die Datendatei mithilfe der mit **bcp_setcolfmt**angegebenen Spalten Formate erstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_setcolfmt (  
        HDBC hdbc,  
        INT field,  
        INT property,  
        void* pValue,  
        INT cbValue);  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *field*  
 Die Spaltenordnungszahl, für die die Eigenschaft festgelegt wird  
  
 *property*  
 Eine der Eigenschaftskonstanten. Eigenschaftskonstanten werden in dieser Tabelle definiert.  
  
|Eigenschaft|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|BCP_FMT_TYPE|BYTE|Der Datentyp dieser Spalte in der Benutzerdatei. Wenn die Daten nicht mit dem Datentyp der entsprechenden Spalte in der Datenbanktabelle übereinstimmen, werden die Daten, wenn möglich, durch das Massenkopieren konvertiert.<br /><br /> Der BCP_FMT_TYPE-Parameter wird von den SQL Server-Datentyptoken in sqlncli.h anstelle der ODBC C-Datentypenumeratoren aufgelistet. Sie können beispielsweise eine Zeichenfolge, ODBC-Typ SQL_C_CHAR, mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischen SQLCHARACTER-Typs angeben.<br /><br /> Um die Standarddatendarstellung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp anzugeben, legen Sie diesen Parameter auf 0 fest.<br /><br /> Wenn die Quell Spalte nicht **Dezimal** oder **numerisch**ist, werden bei einem Massen Kopiervorgang aus SQL Server in eine Datei die Standardgenauigkeit und die Standardskala verwendet, wenn BCP_FMT_TYPE SqlDecimal oder SQLNUMERIC ist. Andernfalls werden die Genauigkeit und die Dezimalstellen der Quell Spalte verwendet, wenn die Quell Spalte **Dezimal** oder **numerisch**ist.|  
|BCP_FMT_INDICATOR_LEN|INT|Die Länge des Indikators (Präfix) in Bytes<br /><br /> Die Länge eines Längen-/NULL-Indikators innerhalb der Spaltendaten in Bytes. Gültige Indikatorlängenwerte sind 0 (wenn kein Indikator verwendet wird), 1, 2 oder 4.<br /><br /> Legen Sie diesen Parameter auf SQL_VARLEN_DATA fest, um die Verwendung eines standardmäßigen Massenkopierindikators anzugeben.<br /><br /> Indikatoren werden im Speicher direkt vor allen anderen Daten angezeigt. In der Datendatei werden sie direkt vor den Daten, auf die sie sich beziehen, angezeigt.<br /><br /> Wird mehr als eine Methode zur Angabe der Länge der Datendateispalte verwendet (z. B. ein Indikator und eine maximale Spaltenlänge oder ein Indikator und eine Abschlusszeichensequenz), wird beim Massenkopieren die Methode ausgewählt, die zu der kleineren zu kopierenden Datenmenge führt.<br /><br /> Datendateien, die durch Massenkopieren generiert wurden, wobei das Datenformat nicht durch Benutzereingriff angepasst wird, enthalten Indikatoren, wenn die Spaltendaten eine unterschiedliche Länge haben oder die Spalte NULL als Wert akzeptieren kann.|  
|BCP_FMT_DATA_LEN|DBINT|Die Länge der Daten (Spaltenlänge) in Bytes<br /><br /> Dies ist die maximale Länge (in Bytes) der Daten dieser Spalte in der Benutzerdatei, ohne die Länge eines Längenindikators oder Abschlusszeichens.<br /><br /> Durch Festlegen von BCP_FMT_DATA_LEN auf SQL_NULL_DATA wird angegeben, dass alle Werte in der Datendateispalte auf NULL festgelegt sind oder sein sollten.<br /><br /> Wird BCP_FMT_DATA_LEN auf SQL_VARLEN_DATA festgelegt, bedeutet dies, dass das System die Länge der Daten für jede Spalte bestimmen soll. Für einige Spalten könnte dies bedeuten, dass ein Längen-/NULL-Indikator generiert wird, der den Daten in einer Kopie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorangestellt wird, oder dass der Indikator in Daten, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kopiert werden, erwartet wird.<br /><br /> BCP_FMT_DATA_LEN kann für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zeichen und Binärdatentypen BCP_LENGTH_VARIABLE, BCP_LENGTH_NULL, 0 oder ein positiver Wert sein. Wenn BCP_FMT_DATA_LEN auf SQL_VARLEN_DATA festgelegt ist, verwendet das System entweder den Längenindikator, sofern vorhanden, oder eine Abschlusszeichensequenz, um die Länge der Daten zu bestimmen. Wenn sowohl ein Längenindikator als auch eine Abschlusszeichensequenz angegeben sind, wird beim Massenkopieren der Wert verwendet, der zu der kleineren zu kopierenden Datenmenge führt. Ist BCP_FMT_DATA_LEN auf SQL_VARLEN_DATA festgelegt, ist der Datentyp ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zeichen oder -Binärtyp. Ist weder ein Längenindikator noch eine Abschlusszeichensequenz angegeben, gibt das System eine Fehlermeldung zurück.<br /><br /> Wenn BCP_FMT_DATA_LEN 0 oder ein positiver Wert ist, verwendet das System BCP_FMT_DATA_LEN als maximale Datenlänge. Wenn jedoch zusätzlich zu einem positiven BCP_FMT_DATA_LEN-Wert ein Längenindikator oder eine Abschlusszeichensequenz angegeben ist, bestimmt das System die Datenlänge mithilfe der Methode, die zu der kleineren zu kopierenden Datenmenge führt.<br /><br /> Der BCP_FMT_DATA_LEN-Wert stellt die Anzahl der Datenbytes dar. Werden Zeichendaten durch Unicode-Zeichen dargestellt, repräsentiert ein positiver BCP_FMT_DATA_LEN-Parameterwert die Anzahl der Zeichen multipliziert mit der Größe (in Bytes) der einzelnen Zeichen.|  
|BCP_FMT_TERMINATOR|LPCBYTE|Zeiger auf die Abschlusszeichensequenz (entweder ANSI oder Unicode), die für diese Spalte verwendet werden soll. Dieser Parameter ist in erster Linie für Zeichendatentypen nützlich, da alle anderen Typen eine feste Länge besitzen oder, im Falle von Binärdaten, einen Indikator für die Länge erfordern, um die Anzahl der vorhandenen Bytes präzise zu erfassen.<br /><br /> Legen Sie diesen Parameter auf NULL fest, um zu vermeiden, dass extrahierte Daten terminiert werden, oder um anzugeben, dass Daten in einer Benutzerdatei nicht terminiert werden.<br /><br /> Wird mehr als eine Methode zur Angabe der Länge der Benutzerdateispalte verwendet (z. B. ein Abschlusszeichen und ein Längenindikator oder ein Abschlusszeichen und eine maximale Spaltenlänge), wird beim Massenkopieren die Methode ausgewählt, die zu der kleineren zu kopierenden Datenmenge führt.<br /><br /> Die API für das Massenkopieren führt nach Bedarf eine Zeichenkonvertierung von Unicode in MBCS aus. Stellen Sie unbedingt sicher, dass sowohl die Bytezeichenfolge des Abschlusszeichens und die Länge der Bytezeichenfolge richtig festgelegt werden.|  
|BCP_FMT_SERVER_COL|INT|Die Position einer Spalte innerhalb der Datenbank|  
|BCP_FMT_COLLATION|LPCSTR|Sortierungsname.|  
  
 *pValue*  
 Der Zeiger auf den Wert, der der *Eigenschaft*zugeordnet werden soll. Er ermöglicht es, jede Spaltenformateigenschaft einzeln festzulegen.  
  
 *cbValue*  
 Die Länge des Puffers der Eigenschaft in Bytes.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion löst die **bcp_colfmt** -Funktion aus. Die gesamte Funktionalität von **bcp_colfmt** wird in **bcp_setcolfmt** Funktion bereitgestellt. Zusätzlich wird auch Unterstützung für Spaltensortierung bereitgestellt. Es wird empfohlen, die folgenden Spaltenformatattribute in der unten gegebenen Reihenfolge festzulegen:  
  
 BCP_FMT_SERVER_COL  
  
 BCP_FMT_DATA_LEN  
  
 BCP_FMT_TYPE  
  
 Mit der **bcp_setcolfmt** -Funktion können Sie das Benutzerdatei Format für Massen Kopien angeben. Für Massenkopieren besteht ein Format aus folgenden Bestandteilen:  
  
-   Eine Zuordnung von Benutzerdateispalten zu Datenbankspalten  
  
-   Der Datentyp der einzelnen Benutzerdateispalten  
  
-   Die Länge des optionalen Indikators für jede Spalte  
  
-   Die maximale Länge der Daten pro Benutzerdateispalte  
  
-   Die optionale abschließende Bytesequenz für jede Spalte  
  
-   Die Länge der optionalen abschließenden Bytesequenz  
  
 Jeder **bcp_setcolfmt** Aufrufe gibt das Format für eine Benutzerdatei Spalte an. Wenn Sie z. b. die Standardeinstellungen für drei Spalten in einer Benutzer Datendatei mit fünf Spalten ändern möchten, rufen Sie zuerst [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) **(5)** auf, und rufen Sie dann **bcp_setcolfmt** fünfmal auf, wobei drei dieser Aufrufe Ihr benutzerdefiniertes Format festlegen. Legen Sie für die verbleibenden zwei Aufrufe BCP_FMT_TYPE auf 0 fest, und legen Sie BCP_FMT_INDICATOR_LENGTH, BCP_FMT_DATA_LEN und *cbValue* auf 0, SQL_VARLEN_DATA bzw. 0 fest. Mit diesem Verfahren werden alle fünf Spalten kopiert, drei mit dem benutzerdefinierten Format und zwei mit dem Standardformat.  
  
 Die **bcp_columns** -Funktion muss aufgerufen werden, bevor **bcp_setcolfmt**aufgerufen wird.  
  
 Sie müssen **bcp_setcolfmt** einmal für jede Eigenschaft jeder Spalte in der Benutzerdatei abrufen.  
  
 Sie müssen nicht alle Daten in einer Benutzerdatei in eine SQL Server-Tabelle kopieren. Um eine Spalte zu überspringen, geben Sie das Format der Daten für die Spalte an, indem Sie den BCP_FMT_SERVER_COL-Parameter auf 0 festlegen. Wenn Sie eine Spalte überspringen möchten, müssen Sie ihren Typ angeben.  
  
 Die [bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) -Funktion kann verwendet werden, um die Format Spezifikation beizubehalten.  
  
## <a name="bcp_setcolfmt-support-for-enhanced-date-and-time-features"></a>bcp_setcolfmt-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die Typen, die mit der BCP_FMT_TYPE-Eigenschaft für Datums-/Uhrzeittypen verwendet werden, sind wie in [Massen Kopier &#40;Änderungen für verbesserte Datums&#41;-und Uhrzeit Typen OLE DB und ODBC](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)angegeben.  
  
 Weitere Informationen finden Sie unter [Verbesserungen &#40;bei Datum und&#41;Uhrzeit (ODBC](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)).  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
