---
title: Bindung und Datenübertragung von Tabellenwertparametern, Parameter und Spaltenwerte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), binding and data transfer
ms.assetid: 0a2ea462-d613-42b6-870f-c7fa086a6b42
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26bcf31c2d4e0d188e93587dd9bdec1a9ff382e0
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52533982"
---
# <a name="binding-and-data-transfer-of-table-valued-parameters-and-column-values"></a>Bindung und Datenübertragung von Tabellenwertparametern und Spaltenwerten
  Tabellenwertparameter müssen ebenso wie andere Parameter gebunden werden, bevor sie an den Server übergeben werden. Die Anwendung bindet Tabellenwertparameter die gleiche Weise wie andere Parameter: mit SQLBindParameter oder entsprechende Aufrufe SQLSetDescField oder SQLSetDescRec. Tabellenwertparameter haben den Serverdatentyp SQL_SS_TABLE. Der C-Typ kann entweder als SQL_C_DEFAULT oder SQL_C_BINARY angegeben werden.  
  
 In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder höher werden nur Eingabe-Tabellenwertparameter unterstützt. Daher resultiert jeder Versuch, SQL_DESC_PARAMETER_TYPE auf einen anderen Wert als SQL_PARAM_INPUT festzulegen, in der Rückgabe von SQL_ERROR mit SQLSTATE = HY105 und der Meldung "Der Parametertyp ist ungültig".  
  
 Gesamten Tabellenwertparameter-Spalten können mit dem Attribut SQL_CA_SS_COL_HAS_DEFAULT_VALUE Standardwerte zugewiesen werden. Einzelne Tabellenwertparameter-Spaltenwerte, allerdings können keine Standardwerte zugewiesen werden von SQL_DEFAULT_PARAM in *StrLen_or_IndPtr* mit SQLBindParameter. Tabellenwertparameter als Ganzes können nicht auf einen Standardwert festgelegt werden, von SQL_DEFAULT_PARAM in *StrLen_or_IndPtr* mit SQLBindParameter. Wenn diese Regeln nicht befolgt werden, gibt SQLExecute oder SQLExecDirect SQL_ERROR zurück. Generiert ein Diagnosedatensatz mit SQLSTATE = 07S01 und der Meldung "Ungültige Verwendung des Standardparameters für den Parameter \<p >", wobei \<p > die Ordnungszahl des Tabellenwertparameters in der abfrageanweisung.  
  
 Nachdem die Anwendung den Tabellenwertparameter gebunden hat, muss sie jede einzelne Tabellenwertparameter-Spalte binden. Zu diesem Zweck ruft die Anwendung zuerst SQLSetStmtAttr auf, um SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl für einen Tabellenwertparameter festgelegt. Die Anwendung bindet dann die Spalten des Table-valued Parameters, durch Aufrufe der folgenden Routinen: SQLBindParameter SQLSetDescRec und SQLSetDescField. Wenn SQL_SOPT_SS_PARAM_FOCUS auf 0 stellt das übliche Verhalten von SQLBindParameter, SQLSetDescField und SQLSetDescRec auf regulären Parameter von der obersten Ebene.  
  
 Für den Tabellenwertparameter an sich werden keine Daten gesendet oder empfangen, die Daten werden für die einzelnen Spalten, aus denen er sich zusammensetzt, gesendet und empfangen. Da der Tabellenwertparameter eine Pseudospalte ist, werden die Parameter für SQLBindParameter verwendet, um auf andere Attribute als andere Datentypen wie folgt zu verweisen:  
  
|Parameter|Verknüpftes Attribut für nicht-Tabellenwertparameter-Typen, einschließlich Spalten|Verknüpftes Attribut für Tabellenwertparameter|  
|---------------|--------------------------------------------------------------------------------|----------------------------------------------------|  
|*InputOutputType*|SQL_DESC_PARAMETER_TYPE in IPD<br /><br /> Für Tabellenwertparameter-Spalten muss diese Angabe der Angabe für den Tabellenwertparameter selbst entsprechen.|SQL_DESC_PARAMETER_TYPE in IPD<br /><br /> Hier muss SQL_PARAM_INPUT angegeben werden.|  
|*ValueType*|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE in APD|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE in APD<br /><br /> Hier muss SQL_C_DEFAULT oder SQL_C_BINARY angegeben werden.|  
|*ParameterType*|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE in IPD|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE in IPD<br /><br /> Hier muss SQL_SS_TABLE angegeben werden.|  
|*ColumnSize*|SQL_DESC_LENGTH oder SQL_DESC_PRECISION in IPD<br /><br /> Dies hängt vom Wert der *ParameterType*.|SQL_DESC_ARRAY_SIZE<br /><br /> Kann auch mit SQL_ATTR_PARAM_SET_SIZE festgelegt werden, wenn der Parameterfokus auf den Tabellenwertparameter festgelegt wurde.<br /><br /> Bei einem Tabellenwertparameter ist dies die Anzahl von Zeilen in den Tabellenwertparameter-Spaltenpuffern.|  
|*DecimalDigits*|SQL_DESC_PRECISION oder SQL_DESC_SCALE in IPD|Nicht verwendet. Diese Angabe muss 0 sein.<br /><br /> Wenn dieser Parameter ist nicht 0, SQLBindParameter wird die Rückgabe von SQL_ERROR und ein Diagnosedatensatz mit SQLSTATE generiert wird = HY104 und der Meldung "Ungültige Genauigkeit oder Dezimalstellenanzahl".|  
|*ParameterValuePtr*|SQL_DESC_DATA_PTR in APD|SQL_CA_SS_TYPE_NAME<br /><br /> Dies ist ein optionales Attribut für gespeicherte Prozeduren, und NULL kann angegeben werden, wenn es nicht erforderlich ist. Es muss für SQL-Anweisungen angegeben werden, die keine Prozeduraufrufe sind.<br /><br /> Dieser Parameter dient als eindeutiger Wert, anhand dessen die Anwendung den betreffenden Tabellenwertparameter bei Verwendung einer variablen Zeilenbindung identifizieren kann. Weitere Informationen finden Sie im Abschnitt "Variable Tabellenwertparameter-Zeilenbindung" weiter unten in diesem Thema.<br /><br /> Wenn ein Typname des Tabellenwertparameters bei einem Aufruf von SQLBindParameter angegeben ist, muss es als Unicode-Wert, auch bei Anwendungen angegeben werden, die als ANSI-Anwendungen erstellt werden. Der Wert für den Parameter *StrLen_or_IndPtr* sollte entweder SQL_NTS oder die Länge der Zeichenfolge mit dem Namen, multipliziert mit sizeof(WCHAR) sein.|  
|*BufferLength*|SQL_DESC_OCTET_LENGTH in APD|Die Länge des Typnamens des Tabellenwertparameters in Byte<br /><br /> Kann SQL_NTS sein, wenn der Typname NULL-termininiert ist, oder 0, wenn der Typname des Tabellenwertparameters nicht erforderlich ist.|  
|*StrLen_or_IndPtr*|SQL_DESC_OCTET_LENGTH_PTR in APD|SQL_DESC_OCTET_LENGTH_PTR in APD<br /><br /> Für Tabellenwertparameter wird hier die Zeilenanzahl statt die Datenlänge angegeben.|  
  
 Zwei Datenübertragungsmodi werden für Tabellenwertparameter unterstützt: feste Zeilenbindung und variable Zeilenbindung.  
  
## <a name="fixed-table-valued-parameter-row-binding"></a>Feste Tabellenwertparameter-Zeilenbindung  
 Bei der festen Zeilenbindung ordnet die Anwendung Puffer (oder Pufferarrays) zu, die groß genug sind, um alle Eingabespaltenwerte aufnehmen zu können. Die Anwendung führt Folgendes aus:  
  
1.  Bindet alle Parameter mithilfe von SQLBindParameter SQLSetDescRec oder SQLSetDescField aufrufen.  
  
    1.  Sie legt SQL_DESC_ARRAY_SIZE auf die maximale Anzahl von Zeilen fest, die für jeden Tabellenwertparameter übertragen werden können. Dies kann erfolgen in der SQLBindParameter-Aufruf.  
  
2.  Ruft die SQLSetStmtAttr auf, um SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl der einzelnen Tabellenwertparameter festzulegen.  
  
    1.  Für jeden Tabellenwertparameter werden Tabellenwertparameter-Spalten mithilfe von SQLBindParameter, SQLSetDescRec oder SQLSetDescField Aufrufe gebunden.  
  
    2.  Für jede Tabellenwertparameter-Spalte, die Standardwerte festgelegt wurden, ruft SQLSetDescField um SQL_CA_SS_COL_HAS_DEFAULT_VALUE auf 1 festgelegt.  
  
3.  Ruft die SQLSetStmtAttr auf, um SQL_SOPT_SS_PARAM_FOCUS auf 0 festgelegt. Dies muss vor dem SQLExecute durchgeführt werden, oder SQLExecDirect aufgerufen wird. Andernfalls wird SQL_ERROR zurückgegeben, und es wird ein Diagnosedatensatz mit SQLSTATE=HY024 und der Meldung "Ungültiger Attributwert, SQL_SOPT_SS_PARAM_FOCUS (muss zur Laufzeit Null sein)" generiert.  
  
4.  Legt *StrLen_or_IndPtr* oder SQL_DESC_OCTET_LENGTH_PTR auf SQL_DEFAULT_PARAM und für einen Tabellenwertparameter mit keine Zeilen oder die Anzahl der Zeilen beim nächsten Aufruf von SQLExecute oder SQLExecDirect übertragen werden, wenn der Tabellenwertparameter der Parameter hat Zeilen. *StrLen_or_IndPtr* oder SQL_DESC_OCTET_LENGTH_PTR kann nicht auf SQL_NULL_DATA festgelegt werden für einen Tabellenwertparameter als Tabellenwertparameter nicht auf NULL festlegbar sind (auch wenn die einzelnen Tabellenwertparameter-Spalten NULL sein können). Wenn dies auf einen ungültigen Wert festgelegt ist, SQLExecute oder SQLExecDirect SQL_ERROR zurück gibt und ein Diagnosedatensatz mit SQLSTATE generiert = HY090 und der Meldung "Ungültige Zeichenfolgen- oder Pufferlänge für Parameter \<p >", wobei p der Parameternummer.  
  
5.  SQLExecute oder SQLExecDirect aufruft.  
  
 Eingabe-Tabellenwertparameter-Spaltenwerte können übergeben werden, wenn *StrLen_or_IndPtr* nastaven NA hodnotu SQL_LEN_DATA_AT_EXEC (*Länge*) oder SQL_DATA_AT_EXEC für die Spalte. Dies gleicht der Übergabe einzelner Werte bei Verwendung von Parameterarrays. Wie der SQLParamData mit allen Data-at-Execution-Parametern, nicht die Zeile des Arrays angegeben anfordert der Treiber Daten; die Anwendung muss diese Probleme zu umgehen. Die Anwendung kann keine Annahmen über die Reihenfolge treffen, in der der Treiber Werte anfordert.  
  
## <a name="variable-table-valued-parameter-row-binding"></a>Variable Tabellenwertparameter-Zeilenbindung  
 Bei einer variablen Zeilenbildung werden die Zeilen zur Laufzeit in Batches übertragen, und die Anwendung übergibt die Zeilen bei Bedarf dem Treiber. Dies ähnelt der Übergabe einzelner Werte für Data-at-Execution-Parameter zur Laufzeit. Bei einer variablen Zeilenbindung geht die Anwendung wie folgt vor:  
  
1.  Sie bindet Parameter und Tabellenwertparameter-Spalten wie in den Schritten 1 bis 3 im vorigen Abschnitt mit dem Titel "Feste Tabellenwertparameter-Zeilenbindung" beschrieben.  
  
2.  Legt *StrLen_or_IndPtr* oder SQL_DESC_OCTET_LENGTH_PTR für alle Tabellenwertparameter-Parameter, die zum Zeitpunkt der Ausführung auf SQL_DATA_AT_EXEC übergeben werden sollen. Wenn keiner dieser beiden Zeiger festgelegt wird, wird der Parameter wie im vorherigen Abschnitt beschrieben verarbeitet.  
  
3.  SQLExecute oder SQLExecDirect aufruft. Dieser Aufruf gibt SQL_NEED_DATA zurück, falls SQL_PARAM_INPUT- oder SQL_PARAM_INPUT_OUTPUT-Parameter als Data-at-Execution-Parameter behandelt werden sollen. In diesem Fall geht die Anwendung wie folgt vor:  
  
    -   Ruft die SQLParamData. Dies gibt die *ParameterValuePtr* Wert für ein Data-at-Execution-Parameter und den Rückgabecode SQL_NEED_DATA zurück. Wenn alle Parameterdaten an den Treiber übergeben wurde, gibt der SQLParamData zurück, SQL_SUCCESS, SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurück. Bei Data-at-Execution-Parametern *ParameterValuePtr*, die identisch mit dem Deskriptor Deskriptorfeld sql_desc_data_ptr entspricht, kann als ein Token für den Parameter eindeutig identifiziert, für die ist ein Wert erforderlich, betrachtet werden. Dieses "Token" wird beim Binden von der Anwendung an den Treiber übergeben und während der Ausführung dann wieder an die Anwendung übergeben.  
  
4.  Zum Senden von Zeilendaten für Tabellenwertparameter für null-Tabellenwertparameter, wenn der Tabellenwertparameter keine Zeilen enthält, eine Anwendung ruft SQLPutData mit *StrLen_or_Ind* auf SQL_DEFAULT_PARAM festgelegt ist.  
  
     Bei Tabellenwertparametern, die nicht NULL sind, geht die Anwendung wie folgt vor:  
  
    -   Legt *Str_Len_or_Ind* für alle Tabellenwertparameter-Spalten auf die geeigneten Werte und füllt die Datenpuffer für Tabellenwertparameter-Spalten, die nicht zu Data-at-Execution-Parameter. Tabellenwertparameter-Spalten können Daten zur Laufzeit auf ähnliche Weise übergeben werden wie dem Treiber gewöhnliche Parameter schrittweise übergeben werden.  
  
    -   Ruft die SQLPutData mit *Str_Len_or_Ind* auf die Anzahl der Zeilen festgelegt, um an den Server gesendet werden. Werte, die nicht im Bereich von 0 bis SQL_DESC_ARRAY_SIZE oder SQL_DEFAULT_PARAM liegen, sind ungültig und bewirken die Rückgabe von SQLSTATE HY090 und der Meldung "Ungültige Zeichenfolgen- oder Pufferlänge". Mit 0 wird angegeben, dass alle Zeilen übermittelt wurden und dass keine weiteren Daten für einen Tabellenwertparameter vorliegen (wie im zweiten Aufzählungspunkt dieser Auflistung beschrieben). SQL_DEFAULT_PARAM kann nur verwendet werden, wenn der Treiber zum ersten Mal Daten für einen Tabellenwertparameter anfordert (wie im ersten Aufzählungspunkt dieser Auflistung beschrieben).  
  
5.  Wenn alle Zeilen gesendet wurden, ruft Sie SQLPutData, für den Tabellenwertparameter mit einem *Str_Len_or_Ind* Wert von 0, und fährt dann mit Schritt 3a oben.  
  
6.  SQLParamData erneut aufgerufen. Wenn Data-at-Execution-Parameter auf die Tabellenwertparameter-Spalten vorhanden sind, werden diese durch den Wert identifiziert *ValuePtrPtr* von der SQLParamData zurückgegeben. Wenn alle Spaltenwerte verfügbar sind, wird erneut SQLParamData Zurückgeben der *ParameterValuePtr* Wert für den Tabellenwertparameter und die Anwendung erneut gestartet.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
