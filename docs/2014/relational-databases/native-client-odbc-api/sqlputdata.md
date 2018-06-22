---
title: SQLPutData | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
caps.latest.revision: 49
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: abce5378b6df9bcce36bf6e1a2c9ed884f977824
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148359"
---
# <a name="sqlputdata"></a>SQLPutData
  Die folgenden Einschränkungen gelten beim Senden von mehr als 65.535 Byte Daten mit SQLPutData (für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 4. 21a) oder 400 KB Daten (für SQL Server, Version 6.0 und höher) für eine SQL_LONGVARCHAR (`text`), SQL_WLONGVARCHAR (`ntext`) oder SQL_LONGVARBINARY (`image`) Spalte:  
  
-   Der referenzierte Parameter kann die *Insert_value* in einer INSERT-Anweisung.  
  
-   Der referenzierte Parameter kann eine *Ausdruck* in der SET-Klausel einer UPDATE-Anweisung.  
  
 Das Abbrechen einer Sequenz von SQLPutData aufrufen, aus denen Daten in Blöcken zu einem Server mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bewirkt, dass ein teilweises Update des Spaltenwerts bei Verwendung von Version 6.5 oder früher. Die `text`, `ntext`, oder `image` Spalte, auf die verwiesen wurde, wenn SQLCancel aufgerufen wurde, ein platzhalterzwischenwert festgelegt ist.  
  
> [!NOTE]  
>  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Treiber unterstützt das Herstellen einer Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version 6.5 und niedriger nicht.  
  
## <a name="diagnostics"></a>Diagnose  
 Es ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-spezifischen SQLSTATE für SQLPutData:  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|22026|Zeichenfolgendaten, nicht übereinstimmende Länge|Wenn die Länge der Daten in Bytes, die gesendet werden von einer Anwendung beispielsweise mit SQL_LEN_DATA_AT_EXEC angegeben wurde (*n*), in denen *n* ist größer als 0 ist, die Gesamtanzahl der Bytes, die von der Anwendung über SQLPutData muss mit der angegebene Länge überein.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData und Tabellenwertparameter  
 SQLPutData wird von einer Anwendung verwendet, wenn Variablen zeilenbindung mit Tabellenwertparametern verwenden. Die *StrLen_Or_Ind* Parameter gibt an, dass er für den Treiber zum Sammeln von Daten für die nächste Zeile bzw. Zeilen des Tabellenwertparameter-Daten bereit ist oder keine weiteren Zeilen verfügbar sind:  
  
-   Ein Wert größer als 0 gibt an, dass der nächste Satz von Zeilenwerten verfügbar ist.  
  
-   Der Wert 0 gibt an, dass es keine Zeilen mehr gibt, die gesendet werden sollen.  
  
-   Ein Wert unter 0 zeigt einen Fehler an und führt dazu, dass ein Diagnosedatensatz mit SQLState HY090 aufgezeichnet und die Meldung „Ungültige Zeichenfolge oder Pufferlänge“ ausgegeben wird.  
  
 Die *DataPtr* Parameter wird ignoriert, jedoch muss auf einen Wert ungleich NULL festgelegt werden. Weitere Informationen finden Sie im Abschnitt auf Variablen zeilenbindung in [Bindung und Data Transfer of Table-Valued-Parametern und Spaltenwerte](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Wenn *StrLen_Or_Ind* verfügt über einen anderen Wert als SQL_DEFAULT_PARAM oder eine Zahl zwischen 0 und SQL_PARAMSET_SIZE (d. h. die *ColumnSize* -Parameter von SQLBindParameter), ist ein Fehler auftritt. Dieser Fehler bewirkt, dass SQLPutData SQL_ERROR: SQLSTATE=HY090, "Ungültige Zeichenfolge oder Pufferlänge" zurückgibt.  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>SQLPutData-Unterstützung für verbesserte Funktionen für Datum/Uhrzeit  
 Parameterwerte von Datum-/Uhrzeit-Typen werden konvertiert, wie in beschrieben [Konvertierungen von C-in SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).  
  
 Weitere Informationen finden Sie unter [Datum und Uhrzeit-Verbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>SQLPutData-Unterstützung für große CLR-UDTs  
 `SQLPutData` unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLPutData-Funktion](http://go.microsoft.com/fwlink/?LinkId=59365)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  