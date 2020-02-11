---
title: SQLBindParameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cba973be9b4dc2ec0da286b2d01b636f0ca4e2b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067816"
---
# <a name="sqlbindparameter"></a>SQLBindParameter
  `SQLBindParameter`kann die Last der Datenkonvertierung eliminieren, wenn Sie zum Bereitstellen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten für den Native Client-ODBC-Treiber verwendet wird. Dies führt zu erheblichen Leistungssteigerungen für die Client-und Serverkomponenten von Anwendungen. Zu den weiteren Vorteilen gehören geringere Verluste der Genauigkeit, wenn ungefähre numerische Datentypen eingefügt oder aktualisiert werden.  
  
> [!NOTE]  
>  Beim Einfügen von Daten vom Typ `char` und `wchar` in eine &lt;legacyBold&gt;image&lt;/legacyBold&gt;-Spalte wird die Größe verwendet, in der die Daten weitergegeben werden, nicht die Größe der Daten nach der Konvertierung in ein binäres Format.  
  
 Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber einen Fehler in einem einzelnen Arrayelement eines Parameterarrays entdeckt, setzt der Treiber die Ausführung der Anweisung für die verbleibenden Arrayelemente fort. Wenn die Anwendung ein Array mit Parameterstatuselementen für die Anweisung gebunden hat, können die Zeilen der Parameter, die Fehler generieren, aus dem Array ermittelt werden.  
  
 Wenn Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Native Client-ODBC-Treiber verwenden, geben Sie SQL_PARAM_INPUT an, wenn Eingabeparameter gebunden werden. Geben Sie nur SQL_PARAM_OUTPUT oder SQL_PARAM_INPUT_OUTPUT an, wenn mit dem OUTPUT-Schlüsselwort definierte gespeicherte Prozedurparameter gebunden werden.  
  
 [SQLRowCount](sqlrowcount.md) ist mit dem Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client-ODBC-Treiber unzuverlässig, wenn ein Array Element eines gebundenen Parameter Arrays einen Fehler bei der Ausführung der Anweisung verursacht. Das ODBC-Anweisungsattribut SQL_ATTR_PARAMS_PROCESSED_PTR meldet die Anzahl von Zeilen, die vor dem Auftreten des Fehler verarbeitet wurden. Die Anwendung kann dann das Parameterstatusarray durchlaufen, um ggf. die Anzahl erfolgreich verarbeiteter Anweisungen zu ermitteln.  
  
## <a name="binding-parameters-for-sql-character-types"></a>Binden von Parametern für SQL-Zeichentypen  
 Wenn es sich bei dem in der Übergabe des SQL-Datentyps um einen Zeichentyp handelt, ist *ColumnSize* die Größe in Zeichen (nicht Bytes). Wenn die Länge der Daten Zeichenfolge in Bytes größer als 8000 ist, sollte *ColumnSize* auf `SQL_SS_LENGTH_UNLIMITED`festgelegt werden, was bedeutet, dass die Größe des SQL-Typs nicht begrenzt ist.  
  
 Wenn der SQL-Datentyp beispielsweise ist `SQL_WVARCHAR`, sollte *ColumnSize* nicht größer als 4000 sein. Wenn die tatsächliche Daten Länge größer als 4000 ist, sollte *ColumnSize* auf `SQL_SS_LENGTH_UNLIMITED` festgelegt werden, damit `nvarchar(max)` vom-Treiber verwendet wird.  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>SQLBindParameter und Tabellenwertparameter  
 Wie andere Parametertypen werden Tabellenwert Parameter von SQLBindParameter gebunden.  
  
 Nachdem ein Tabellenwertparameter gebunden wurde, werden seine Spalten ebenfalls gebunden. Zum Binden der Spalten aufrufen Sie [SQLSetStmtAttr](sqlsetstmtattr.md) , um SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl des Tabellenwert Parameters festzulegen. Aufrufen Sie dann SQLBindParameter für jede Spalte im Tabellenwert Parameter. Um zu den Parameterbindungen der obersten Ebene zurückzukehren, legen Sie SQL_SOPT_SS_PARAM_FOCUS auf 0 fest.  
  
 Weitere Informationen zum Mapping von Parametern für Deskriptorfelder für Tabellenwert Parameter finden Sie unter [binden und Datenübertragung von Tabellenwert Parametern und Spaltenwerten](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie unter [Tabellenwert Parameter &#40;ODBC-&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>SQLBindParameter-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Parameter Werte von Datums-/Uhrzeittypen werden entsprechend der Beschreibung in [Konvertierungen von C in SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)konvertiert. Beachten Sie, dass für `time` Parameter `datetimeoffset` vom Typ und der *ValueType* `SQL_C_DEFAULT` als `SQL_C_BINARY` oder angegeben werden muss,`SQL_SS_TIME2_STRUCT` Wenn `SQL_SS_TIMESTAMPOFFSET_STRUCT`die entsprechenden Strukturen (und) verwendet werden.  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>SQLBindParameter-Unterstützung für große CLR-UDTs  
 
  `SQLBindParameter` unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Details zur ODBC-API-Implementierung](odbc-api-implementation-details.md)   
 [SQLBindParameter-Funktion](https://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
