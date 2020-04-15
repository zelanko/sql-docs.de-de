---
title: SQLPutData | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e063d1053d8a6e5e10a1234d33893adf27fbc3ad
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302351"
---
# <a name="sqlputdata"></a>SQLPutData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die folgenden Einschränkungen gelten, wenn Sie SQLPutData verwenden, um mehr [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als 65.535 Byte Daten (für Version 4.21a) oder 400 KB Daten (für SQL Server Version 6.0 und höher) für eine SQL_LONGVARCHAR (**Text**), SQL_WLONGVARCHAR (**ntext**) oder SQL_LONGVARBINARY (**Bild**) Spalte zu senden:  
  
-   Der referenzierte Parameter kann der *insert_value* in einer INSERT-Anweisung sein.  
  
-   Der referenzierte Parameter kann ein *Ausdruck* in der SET-Klausel einer UPDATE-Anweisung sein.  
  
 Das Abbrechen einer Sequenz von SQLPutData-Aufrufen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten in Blöcken für einen ausgeführten Server bereitstellen, führt zu einer teilweisen Aktualisierung des Spaltenwerts bei Verwendung von Version 6.5 oder früher. Die **Text**-, **ntext**- oder **Bildspalte,** auf die beim Aufruf von SQLCancel verwiesen wurde, wird auf einen Zwischenplatzhalterwert festgelegt.  
  
> [!NOTE]  
>  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Treiber unterstützt das Herstellen einer Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version 6.5 und niedriger nicht.  
  
## <a name="diagnostics"></a>Diagnose  
 Es gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine systemeigene clientspezifische SQLSTATE für SQLPutData:  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|22026|Zeichenfolgendaten, nicht übereinstimmende Länge|Wenn die Länge der zu sendenden Daten in Bytes von einer Anwendung angegeben wurde, z. B. mit SQL_LEN_DATA_AT_EXEC(*n*), wobei *n* größer als 0 ist, muss die Gesamtzahl der Bytes, die von der Anwendung über SQLPutData angegeben werden, mit der angegebenen Länge übereinstimmen.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData und Tabellenwertparameter  
 SQLPutData wird von einer Anwendung verwendet, wenn variable Zeilenbindung mit Tabellenwertparametern verwendet wird. Der *Parameter StrLen_Or_Ind* gibt an, dass der Treiber bereit ist, Daten für die nächste Zeile oder Zeilen mit Tabellenwert zu sammeln, oder dass keine weiteren Zeilen verfügbar sind:  
  
-   Ein Wert größer als 0 gibt an, dass der nächste Satz von Zeilenwerten verfügbar ist.  
  
-   Der Wert 0 gibt an, dass es keine Zeilen mehr gibt, die gesendet werden sollen.  
  
-   Ein Wert unter 0 zeigt einen Fehler an und führt dazu, dass ein Diagnosedatensatz mit SQLState HY090 aufgezeichnet und die Meldung „Ungültige Zeichenfolge oder Pufferlänge“ ausgegeben wird.  
  
 Der *DataPtr-Parameter* wird ignoriert, muss jedoch auf einen Nicht-NULL-Wert festgelegt werden. Weitere Informationen finden Sie im Abschnitt variable TVP-Zeilenbindung in [Bindung und Datenübertragung von Tabellenwertparametern und Spaltenwerten](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Wenn *StrLen_Or_Ind* einen anderen Wert als SQL_DEFAULT_PARAM oder eine Zahl zwischen 0 und dem SQL_PARAMSET_SIZE hat (d. h. den *ColumnSize-Parameter* von SQLBindParameter), ist dies ein Fehler. Dieser Fehler bewirkt, dass SQLPutData SQL_ERROR: SQLSTATE=HY090, "Ungültige Zeichenfolge oder Pufferlänge" zurückgibt.  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Tabellenwertparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>SQLPutData-Unterstützung für verbesserte Funktionen für Datum/Uhrzeit  
 Parameterwerte von Datums-/Uhrzeittypen werden wie unter [Konvertierungen von C in SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)beschrieben konvertiert.  
  
 Weitere Informationen finden Sie unter [Datums- und Zeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>SQLPutData-Unterstützung für große CLR-UDTs  
 **SQLPutData** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Große benutzerdefinierte CLR-Typen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLPutData-Funktion](https://go.microsoft.com/fwlink/?LinkId=59365)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
