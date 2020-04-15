---
title: Datenübertragung von Tabellenwertparametern
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), binding and data transfer
ms.assetid: 0a2ea462-d613-42b6-870f-c7fa086a6b42
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3b7eecfdac3d42b7a3d8d66ffe1f8ac68652230f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304496"
---
# <a name="binding-and-data-transfer-of-table-valued-parameters-and-column-values"></a>Bindung und Datenübertragung von Tabellenwertparametern und Spaltenwerten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Tabellenwertparameter müssen ebenso wie andere Parameter gebunden werden, bevor sie an den Server übergeben werden. Die Anwendung bindet Tabellenwertparameter auf die gleiche Weise, wie sie andere Parameter bindet: durch Verwendung von SQLBindParameter oder gleichwertigen Aufrufen von SQLSetDescField oder SQLSetDescRec. Tabellenwertparameter haben den Serverdatentyp SQL_SS_TABLE. Der C-Typ kann entweder als SQL_C_DEFAULT oder SQL_C_BINARY angegeben werden.  
  
 In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder höher werden nur Eingabe-Tabellenwertparameter unterstützt. Daher resultiert jeder Versuch, SQL_DESC_PARAMETER_TYPE auf einen anderen Wert als SQL_PARAM_INPUT festzulegen, in der Rückgabe von SQL_ERROR mit SQLSTATE = HY105 und der Meldung "Der Parametertyp ist ungültig".  
  
 Gesamten Tabellenwertparameter-Spalten können mit dem Attribut SQL_CA_SS_COL_HAS_DEFAULT_VALUE Standardwerte zugewiesen werden. Einzelne Parameterspaltenwerte mit Tabellenwert können jedoch nicht mit SQL_DEFAULT_PARAM in *StrLen_or_IndPtr* mit SQLBindParameter zugewiesen werden. Tabellenwertparameter als Ganzes können nicht auf einen Standardwert festgelegt werden, indem SQL_DEFAULT_PARAM in *StrLen_or_IndPtr* mit SQLBindParameter verwendet wird. Wenn diese Regeln nicht befolgt werden, geben SQLExecute oder SQLExecDirect SQL_ERROR zurück. Ein Diagnosedatensatz wird mit SQLSTATE=07S01 und der Meldung "Ungültige \<Verwendung des \<Standardparameters für Parameter p>" generiert, wobei p> die Ordnung des TVP in der Abfrageanweisung ist.  
  
 Nachdem die Anwendung den Tabellenwertparameter gebunden hat, muss sie jede einzelne Tabellenwertparameter-Spalte binden. Zu diesem Zeitpunkt ruft die Anwendung zuerst SQLSetStmtAttr auf, um SQL_SOPT_SS_PARAM_FOCUS auf die Ordnung eines Tabellenwertparameters festzulegen. Anschließend bindet die Anwendung die Spalten des Tabellenwertparameters durch Aufrufe an die folgenden Routinen: SQLBindParameter, SQLSetDescRec und SQLSetDescField. Wenn Sie SQL_SOPT_SS_PARAM_FOCUS auf 0 setzen, wird der übliche Effekt von SQLBindParameter, SQLSetDescRec und SQLSetDescField bei der Verwendung von regulären Parametern der obersten Ebene wiederhergestellt.
 
 Hinweis: Bei den Linux- und Mac ODBC-Treibern mit unixODBC 2.3.1 bis 2.3.4 wird unixODBC beim Festlegen des TVP-Namens über SQLSetDescField mit dem SQL_CA_SS_TYPE_NAME-Deskriptorfeld nicht automatisch zwischen ANSI- und Unicode-Zeichenfolgen konvertiert, abhängig von der genauen Funktion (SQLSetDescFieldA / SQLSetDescFieldW). Es ist erforderlich, entweder immer SQLBindParameter oder SQLSetDescFieldW mit einer Unicode-Zeichenfolge (UTF-16) zu verwenden, um den TVP-Namen festzulegen.
  
 Für den Tabellenwertparameter an sich werden keine Daten gesendet oder empfangen, die Daten werden für die einzelnen Spalten, aus denen er sich zusammensetzt, gesendet und empfangen. Da es sich bei dem Parameter "Tabellenwert" um eine Pseudospalte handelt, werden die Parameter für SQLBindParameter verwendet, um auf andere Attribute als andere Datentypen zu verweisen:  
  
|Parameter|Zugehöriges Attribut für nicht tabellenwertige Parametertypen, einschließlich Spalten|Verknüpftes Attribut für Tabellenwertparameter|  
|---------------|--------------------------------------------------------------------------------|----------------------------------------------------|  
|*InputOutputType*|SQL_DESC_PARAMETER_TYPE in IPD<br /><br /> Für Tabellenwertparameter-Spalten muss diese Angabe der Angabe für den Tabellenwertparameter selbst entsprechen.|SQL_DESC_PARAMETER_TYPE in IPD<br /><br /> Hier muss SQL_PARAM_INPUT angegeben werden.|  
|*Valuetype*|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE in APD|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE in APD<br /><br /> Hier muss SQL_C_DEFAULT oder SQL_C_BINARY angegeben werden.|  
|*ParameterType*|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE in IPD|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE in IPD<br /><br /> Hier muss SQL_SS_TABLE angegeben werden.|  
|*ColumnSize*|SQL_DESC_LENGTH oder SQL_DESC_PRECISION in IPD<br /><br /> Dies hängt vom Wert von *ParameterType ab.*|SQL_DESC_ARRAY_SIZE<br /><br /> Kann auch mit SQL_ATTR_PARAM_SET_SIZE festgelegt werden, wenn der Parameterfokus auf den Tabellenwertparameter festgelegt wurde.<br /><br /> Bei einem Tabellenwertparameter ist dies die Anzahl von Zeilen in den Tabellenwertparameter-Spaltenpuffern.|  
|*DecimalDigits*|SQL_DESC_PRECISION oder SQL_DESC_SCALE in IPD|Nicht verwendet. Diese Angabe muss 0 sein.<br /><br /> Wenn dieser Parameter nicht 0 ist, gibt SQLBindParameter SQL_ERROR zurück, und ein Diagnosedatensatz wird mit SQLSTATE= HY104 und der Meldung "Ungültige Genauigkeit oder Skalierung" generiert.|  
|*ParameterValuePtr*|SQL_DESC_DATA_PTR in APD|SQL_CA_SS_TYPE_NAME<br /><br /> Dies ist ein optionales Attribut für gespeicherte Prozeduren, und NULL kann angegeben werden, wenn es nicht erforderlich ist. Es muss für SQL-Anweisungen angegeben werden, die keine Prozeduraufrufe sind.<br /><br /> Dieser Parameter dient als eindeutiger Wert, anhand dessen die Anwendung den betreffenden Tabellenwertparameter bei Verwendung einer variablen Zeilenbindung identifizieren kann. Weitere Informationen finden Sie im Abschnitt "Variable Tabellenwertparameter-Zeilenbindung" weiter unten in diesem Thema.<br /><br /> Wenn ein Tabellenwertparametertypname für einen Aufruf von SQLBindParameter angegeben wird, muss er als Unicode-Wert angegeben werden, auch in Anwendungen, die als ANSI-Anwendungen erstellt werden. Der für den Parameter *StrLen_or_IndPtr* verwendete Wert sollte entweder SQL_NTS oder die Zeichenfolgenlänge des Namens multipliziert mit sizeof(WCHAR) sein.|  
|*BufferLength*|SQL_DESC_OCTET_LENGTH in APD|Die Länge des Typnamens des Tabellenwertparameters in Byte<br /><br /> Kann SQL_NTS sein, wenn der Typname NULL-termininiert ist, oder 0, wenn der Typname des Tabellenwertparameters nicht erforderlich ist.|  
|*StrLen_or_IndPtr*|SQL_DESC_OCTET_LENGTH_PTR in APD|SQL_DESC_OCTET_LENGTH_PTR in APD<br /><br /> Für Tabellenwertparameter wird hier die Zeilenanzahl statt die Datenlänge angegeben.|  
||||

 Zwei Datenübertragungsmodi werden für Tabellenwertparameter unterstützt: feste Zeilenbindung und variable Zeilenbindung.  
  
## <a name="fixed-table-valued-parameter-row-binding"></a>Feste Tabellenwertparameter-Zeilenbindung  
 Bei der festen Zeilenbindung ordnet die Anwendung Puffer (oder Pufferarrays) zu, die groß genug sind, um alle Eingabespaltenwerte aufnehmen zu können. Die Anwendung führt die folgenden Schritte aus:  
  
1.  Bindet alle Parameter mithilfe von SQLBindParameter-, SQLSetDescRec- oder SQLSetDescField-Aufrufen.  
  
    1.  Sie legt SQL_DESC_ARRAY_SIZE auf die maximale Anzahl von Zeilen fest, die für jeden Tabellenwertparameter übertragen werden können. Dies kann im SQLBindParameter-Aufruf erfolgen.  
  
2.  Ruft SQLSetStmtAttr auf, um SQL_SOPT_SS_PARAM_FOCUS auf die Ordnung jedes Tabellenwertparameters festzulegen.  
  
    1.  Bindet für jeden Tabellenwertparameter Parameterspalten mit Tabellenwert mithilfe von SQLBindParameter-, SQLSetDescRec- oder SQLSetDescField-Aufrufen.  
  
    2.  Ruft SQLSetDescField für jede Parameterspalte mit Tabellenwert auf, die Überstandardwerte haben soll, um SQL_CA_SS_COL_HAS_DEFAULT_VALUE auf 1 festzulegen.  
  
3.  Ruft SQLSetStmtAttr auf, um SQL_SOPT_SS_PARAM_FOCUS auf 0 festzulegen. Dies muss geschehen, bevor SQLExecute oder SQLExecDirect aufgerufen werden. Andernfalls wird SQL_ERROR zurückgegeben, und es wird ein Diagnosedatensatz mit SQLSTATE=HY024 und der Meldung "Ungültiger Attributwert, SQL_SOPT_SS_PARAM_FOCUS (muss zur Laufzeit Null sein)" generiert.  
  
4.  Legt *StrLen_or_IndPtr* oder SQL_DESC_OCTET_LENGTH_PTR fest, SQL_DEFAULT_PARAM für einen Tabellenwertparameter ohne Zeilen oder die Anzahl der Zeilen, die beim nächsten Aufruf von SQLExecute oder SQLExecDirect übertragen werden sollen, wenn der Tabellenwertparameter Zeilen enthält. *StrLen_or_IndPtr* oder SQL_DESC_OCTET_LENGTH_PTR kann nicht auf SQL_NULL_DATA für einen Tabellenwertparameter festgelegt werden, da Tabellenwertparameter nicht nullierbar sind (obwohl Tabellenwertparameter-Komponentenspalten möglicherweise nullsind). Wenn dies auf einen ungültigen Wert festgelegt ist, gibt SQLExecute oder SQLExecDirect SQL_ERROR zurück, und ein Diagnosedatensatz wird mit \<SQLSTATE=HY090 und der Meldung "Ungültige Zeichenfolge oder Pufferlänge für Parameter p>" generiert, wobei p die Parameternummer ist.  
  
5.  Ruft SQLExecute oder SQLExecDirect auf.  
  
 Die Parameterspaltenwerte der Eingabetabelle können in Stücke übergeben werden, wenn *StrLen_or_IndPtr* auf*SQL_LEN_DATA_AT_EXEC(Länge*) oder SQL_DATA_AT_EXEC für die Spalte festgelegt ist. Dies gleicht der Übergabe einzelner Werte bei Verwendung von Parameterarrays. Wie bei allen Parametern für die Ausführung von Daten bei der Ausführung gibt SQLParamData nicht an, für welche Zeile des Arrays der Treiber Daten anfordert. die Anwendung muss sich darum kümmern. Die Anwendung kann keine Annahmen über die Reihenfolge treffen, in der der Treiber Werte anfordert.  
  
## <a name="variable-table-valued-parameter-row-binding"></a>Variable Tabellenwertparameter-Zeilenbindung  
 Bei einer variablen Zeilenbildung werden die Zeilen zur Laufzeit in Batches übertragen, und die Anwendung übergibt die Zeilen bei Bedarf dem Treiber. Dies ähnelt der Übergabe einzelner Werte für Data-at-Execution-Parameter zur Laufzeit. Bei einer variablen Zeilenbindung geht die Anwendung wie folgt vor:  
  
1.  Sie bindet Parameter und Tabellenwertparameter-Spalten wie in den Schritten 1 bis 3 im vorigen Abschnitt mit dem Titel "Feste Tabellenwertparameter-Zeilenbindung" beschrieben.  
  
2.  Legt *StrLen_or_IndPtr* oder SQL_DESC_OCTET_LENGTH_PTR für parameter mit Tabellenwert fest, die zur Ausführungszeit an SQL_DATA_AT_EXEC übergeben werden sollen. Wenn keiner dieser beiden Zeiger festgelegt wird, wird der Parameter wie im vorherigen Abschnitt beschrieben verarbeitet.  
  
3.  Ruft SQLExecute oder SQLExecDirect auf. Dieser Aufruf gibt SQL_NEED_DATA zurück, falls SQL_PARAM_INPUT- oder SQL_PARAM_INPUT_OUTPUT-Parameter als Data-at-Execution-Parameter behandelt werden sollen. In diesem Fall geht die Anwendung wie folgt vor:  
  
    -   Ruft SQLParamData auf. Dadurch wird der *ParameterValuePtr-Wert* für einen Data-at-Execution-Parameter und ein Rückgabecode von SQL_NEED_DATA zurückgegeben. Wenn alle Parameterdaten an den Treiber übergeben wurden, gibt SQLParamData SQL_SUCCESS, SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurück. *ParameterValuePtr*, der mit dem Deskriptorfeld SQL_DESC_DATA_PTR identisch ist, kann bei Parametern bei der Ausführung als Token betrachtet werden, um einen Parameter eindeutig zu identifizieren, für den ein Wert erforderlich ist. Dieses "Token" wird beim Binden von der Anwendung an den Treiber übergeben und während der Ausführung dann wieder an die Anwendung übergeben.  
  
4.  Um Tabellenwertparameterzeilendaten für Nulltabellenwertparameter zu senden, ruft eine Anwendung SQLPutData auf, wobei *StrLen_or_Ind* auf SQL_DEFAULT_PARAM festgelegt ist, wenn der Parameter "Tabelle-Wert" keine Zeilen enthält.  
  
     Bei Tabellenwertparametern, die nicht NULL sind, geht die Anwendung wie folgt vor:  
  
    -   Legt *Str_Len_or_Ind* für alle Parameterspalten mit Tabellenwert auf geeignete Werte fest und füllt Datenpuffer für Parameterspalten mit Tabellenwert aus, die keine Parameter mit Data-at-Execution-Werten sein sollen. Tabellenwertparameter-Spalten können Daten zur Laufzeit auf ähnliche Weise übergeben werden wie dem Treiber gewöhnliche Parameter schrittweise übergeben werden.  
  
    -   Ruft SQLPutData *auf, wobei Str_Len_or_Ind* auf die Anzahl der Zeilen festgelegt ist, die an den Server gesendet werden sollen. Werte, die nicht im Bereich von 0 bis SQL_DESC_ARRAY_SIZE oder SQL_DEFAULT_PARAM liegen, sind ungültig und bewirken die Rückgabe von SQLSTATE HY090 und der Meldung "Ungültige Zeichenfolgen- oder Pufferlänge". Mit 0 wird angegeben, dass alle Zeilen übermittelt wurden und dass keine weiteren Daten für einen Tabellenwertparameter vorliegen (wie im zweiten Aufzählungspunkt dieser Auflistung beschrieben). SQL_DEFAULT_PARAM kann nur verwendet werden, wenn der Treiber zum ersten Mal Daten für einen Tabellenwertparameter anfordert (wie im ersten Aufzählungspunkt dieser Auflistung beschrieben).  
  
5.  Wenn alle Zeilen gesendet wurden, ruft SQLPutData für den Parameter "Tabelle- wert" mit einem *Str_Len_or_Ind* Wert von 0 auf und fährt dann mit Schritt 3a oben fort.  
  
6.  Ruft SQLParamData erneut auf. Wenn sich Daten-at-Execution-Parameter in den Tabellenwert-Parameterspalten befinden, werden diese durch den von SQLParamData zurückgegebenen Wert *ValuePtrPtr* identifiziert. Wenn alle Spaltenwerte verfügbar sind, gibt SQLParamData erneut den *ParameterValuePtr-Wert* für den Parameter "Tabellenwert" zurück, und die Anwendung beginnt erneut.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenbewertete Parameter &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
