---
title: SQLBindParameter | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 74122d531eba1f714e16c168838ee1653a8f1293
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302681"
---
# <a name="sqlbindparameter"></a>SQLBindParameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SQLBindParameter** kann die Last der Datenkonvertierung eliminieren, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wenn es zur Bereitstellung von Daten für den nativen Client-ODBC-Treiber verwendet wird, was zu erheblichen Leistungssteigerungen sowohl für die Client- als auch für die Serverkomponenten von Anwendungen führt. Zu den weiteren Vorteilen gehören geringere Verluste der Genauigkeit, wenn ungefähre numerische Datentypen eingefügt oder aktualisiert werden.  
  
> [!NOTE]  
>  Beim Einfügen von **Char-** und **Wchar-Typdaten** in eine Bildspalte wird die Größe der übergebenen Daten verwendet, im Gegensatz zur Größe der Daten nach der Konvertierung in ein binäres Format.  
  
 Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber einen Fehler in einem einzelnen Arrayelement eines Parameterarrays entdeckt, setzt der Treiber die Ausführung der Anweisung für die verbleibenden Arrayelemente fort. Wenn die Anwendung ein Array mit Parameterstatuselementen für die Anweisung gebunden hat, können die Zeilen der Parameter, die Fehler generieren, aus dem Array ermittelt werden.  
  
 Wenn Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Native Client-ODBC-Treiber verwenden, geben Sie SQL_PARAM_INPUT an, wenn Eingabeparameter gebunden werden. Geben Sie nur SQL_PARAM_OUTPUT oder SQL_PARAM_INPUT_OUTPUT an, wenn mit dem OUTPUT-Schlüsselwort definierte gespeicherte Prozedurparameter gebunden werden.  
  
 [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md) ist mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Native Client ODBC-Treiber unzuverlässig, wenn ein Arrayelement eines array-Parameter-Arrays einen Fehler bei der Anweisungsausführung verursacht. Das ODBC-Anweisungsattribut SQL_ATTR_PARAMS_PROCESSED_PTR meldet die Anzahl von Zeilen, die vor dem Auftreten des Fehler verarbeitet wurden. Die Anwendung kann dann das Parameterstatusarray durchlaufen, um ggf. die Anzahl erfolgreich verarbeiteter Anweisungen zu ermitteln.  
  
## <a name="binding-parameters-for-sql-character-types"></a>Binden von Parametern für SQL-Zeichentypen  
 Wenn es sich bei dem übergebenen SQL-Datentyp um einen Zeichentyp handelt, ist *ColumnSize* die Größe in Zeichen (nicht Bytes). Wenn die Länge der Datenzeichenfolge in Bytes größer als 8000 ist, sollte *ColumnSize* auf **SQL_SS_LENGTH_UNLIMITED**festgelegt werden, was darauf hinweist, dass die Größe des SQL-Typs nicht begrenzt ist.  
  
 Wenn der SQL-Datentyp z. B. **SQL_WVARCHAR**ist, sollte *ColumnSize* nicht größer als 4000 sein. Wenn die tatsächliche Datenlänge größer als 4000 ist, sollte *ColumnSize* auf **SQL_SS_LENGTH_UNLIMITED** festgelegt werden, damit **nvarchar(max)** vom Treiber verwendet wird.  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>SQLBindParameter und Tabellenwertparameter  
 Wie andere Parametertypen sind Tabellenwertparameter an SQLBindParameter gebunden.  
  
 Nachdem ein Tabellenwertparameter gebunden wurde, werden seine Spalten ebenfalls gebunden. Um die Spalten zu binden, rufen Sie [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) auf, um SQL_SOPT_SS_PARAM_FOCUS auf die Ordnung des Parameters "Tabellenwert" festzulegen. Rufen Sie dann SQLBindParameter für jede Spalte im Tabellenwertparameter auf. Um zu den Parameterbindungen der obersten Ebene zurückzukehren, legen Sie SQL_SOPT_SS_PARAM_FOCUS auf 0 fest.  
  
 Informationen zum Zuordnen von Parametern zu Deskriptorfeldern für Tabellenwertparameter finden Sie unter [Bindung und Datenübertragung von Tabellenwertparametern und Spaltenwerten](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Tabellenwertparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>SQLBindParameter-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Parameterwerte von Datums-/Uhrzeittypen werden wie unter [Konvertierungen von C in SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)beschrieben konvertiert. Beachten Sie, dass in Parametern vom Typ **Time** und **datetimeoffset** *ValueType* als **SQL_C_DEFAULT** oder **SQL_C_BINARY** angegeben werden muss, wenn die entsprechenden Strukturen (**SQL_SS_TIME2_STRUCT** und **SQL_SS_TIMESTAMPOFFSET_STRUCT**) verwendet werden.  
  
 Weitere Informationen finden Sie unter [Datums- und Zeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>SQLBindParameter-Unterstützung für große CLR-UDTs  
 **SQLBindParameter** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Große benutzerdefinierte CLR-Typen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SQLBindParameter-Funktion](https://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
