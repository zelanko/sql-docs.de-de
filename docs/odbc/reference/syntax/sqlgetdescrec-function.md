---
title: SQLGetDescRec-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetDescRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDescRec
helpviewer_keywords:
- SQLGetDescRec function [ODBC]
ms.assetid: 325e0907-8e87-44e8-a111-f39e636a9cbc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 87d7b971b379f19f8451e924932a5e699e9b9983
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285485"
---
# <a name="sqlgetdescrec-function"></a>SQLGetDescRec-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetDescRec** gibt die aktuellen Einstellungen oder Werte mehrerer Felder eines Deskriptordatensatzes zurück. Die zurückgegebenen Felder beschreiben den Namen, den Datentyp und die Speicherung von Spalten- oder Parameterdaten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetDescRec(  
      SQLHDESC        DescriptorHandle,  
      SQLSMALLINT     RecNumber,  
      SQLCHAR *       Name,  
      SQLSMALLINT     BufferLength,  
      SQLSMALLINT *   StringLengthPtr,  
      SQLSMALLINT *   TypePtr,  
      SQLSMALLINT *   SubTypePtr,  
      SQLLEN *        LengthPtr,  
      SQLSMALLINT *   PrecisionPtr,  
      SQLSMALLINT *   ScalePtr,  
      SQLSMALLINT *   NullablePtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *DescriptorHandle*  
 [Eingabe] Deskriptor-Handle.  
  
 *RecNumber*  
 [Eingabe] Gibt den Deskriptordatensatz an, aus dem die Anwendung Informationen sucht. Deskriptordatensätze werden von 1 nummeriert, wobei Datensatznummer 0 der Lesezeichendatensatz ist. Das *RecNumber-Argument* muss kleiner oder gleich dem Wert von SQL_DESC_COUNT sein. Wenn *RecNumber* kleiner oder gleich SQL_DESC_COUNT ist, die Zeile jedoch keine Daten für eine Spalte oder einen Parameter enthält, gibt ein Aufruf von **SQLGetDescRec** die Standardwerte der Felder zurück. (Weitere Informationen finden Sie unter "Initialisierung von Deskriptorfeldern" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 *Name*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem das SQL_DESC_NAME Feld für den Deskriptordatensatz zurückgegeben werden soll.  
  
 Wenn *Name* NULL ist, gibt *StringLengthPtr* weiterhin die Gesamtzahl der Zeichen (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten) zurück, die im Puffer zurückgegeben werden können, auf den durch *Name*verwiesen wird.  
  
 *BufferLength*  
 [Eingabe] Länge des **Namenspuffers* in Zeichen.  
  
 *StringLengthPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem die Anzahl der \*Zeichen zurückgegeben werden soll, die im *Name-Puffer* zurückgegeben werden können, mit Ausnahme des Null-Beendigungszeichens. Wenn die Anzahl der Zeichen größer oder gleich *BufferLength*war, werden die Daten in \* *Name* auf *BufferLength* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten und vom Treiber null beendet.  
  
 *TypPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem der Wert des Feldes SQL_DESC_TYPE für den Deskriptordatensatz zurückgegeben werden soll.  
  
 *SubTypePtr*  
 [Ausgabe] Bei Datensätzen, deren Typ SQL_DATETIME oder SQL_INTERVAL ist, ist dies ein Zeiger auf einen Puffer, in dem der Wert des Feldes SQL_DESC_DATETIME_INTERVAL_CODE zurückgegeben werden soll.  
  
 *LengthPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem der Wert des SQL_DESC_OCTET_LENGTH Feldes für den Deskriptordatensatz zurückgegeben werden soll.  
  
 *PrecisionPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem der Wert des SQL_DESC_PRECISION Felds für den Deskriptordatensatz zurückgegeben werden soll.  
  
 *ScalePtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem der Wert des Feldes SQL_DESC_SCALE für den Deskriptordatensatz zurückgegeben werden soll.  
  
 *NullablePtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem der Wert des SQL_DESC_NULLABLE Feldes für den Deskriptordatensatz zurückgegeben werden soll.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA oder SQL_INVALID_HANDLE.  
  
 SQL_NO_DATA wird zurückgegeben, wenn *RecNumber* größer als die aktuelle Anzahl von Deskriptordatensätzen ist.  
  
 SQL_NO_DATA wird zurückgegeben, wenn *DescriptorHandle* ein IRD-Handle ist und sich die Anweisung im vorbereiteten oder ausgeführten Zustand befindet, ihm jedoch kein offener Cursor zugeordnet war.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetDescRec** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DESC und einem *Handle* von *DescriptorHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLGetDescRec** zurückgegeben werden, und es werden die sqlState-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Der \* *Puffername* war nicht groß genug, um das gesamte Deskriptorfeld zurückzugeben. Daher wurde das Feld abgeschnitten. Die Länge des nicht abgeschnittenen Deskriptorfelds wird in **StringLengthPtr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger Deskriptorindex|Das *FieldIdentifier-Argument* war ein Datensatzfeld, das *RecNumber-Argument* wurde auf 0 festgelegt, und das *DescriptorHandle-Argument* war ein IPD-Handle.<br /><br /> (DM) Das *RecNumber-Argument* wurde auf 0 und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_OFF festgelegt, und das *DescriptorHandle-Argument* war ein IRD-Handle.<br /><br /> Das *RecNumber-Argument* war kleiner als 0.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den Speicher nicht zuweisen, der erforderlich ist, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY007|Zugehörige Anweisung ist nicht vorbereitet|*DescriptorHandle* wurde einem IRD zugeordnet, und das zugeordnete Anweisungshandle befand sich nicht im vorbereiteten oder ausgeführten Zustand.|  
|HY010|Funktionssequenzfehler|(DM) *DescriptorHandle* wurde einem *StatementHandle* zugeordnet, für den eine asynchron ausführende Funktion (nicht diese) aufgerufen wurde und noch ausgeführt wurde, als diese Funktion aufgerufen wurde.<br /><br /> (DM) *DescriptorHandle* wurde einem *StatementHandle* zugeordnet, für das **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** aufgerufen und SQL_NEED_DATA zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) Für das Verbindungshandle, das dem *DescriptorHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als **SQLGetDescRec** aufgerufen wurde.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der mit *DescriptorHandle* verknüpfte Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung kann **SQLGetDescRec** aufrufen, um die Werte der folgenden Deskriptorfelder für eine einzelne Spalte oder einen Parameter abzurufen:  
  
-   SQL_DESC_NAME  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (für Datensätze, deren Typ SQL_DATETIME oder SQL_INTERVAL ist)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_NULLABLE  
  
 **SQLGetDescRec** ruft die Werte für Headerfelder nicht ab.  
  
 Eine Anwendung kann die Rückgabe der Feldeinstellung verhindern, indem sie das Argument, das dem Feld entspricht, auf einen Nullzeiger setzt.  
  
 Wenn eine Anwendung **SQLGetDescRec** aufruft, um den Wert eines Felds abzurufen, das für einen bestimmten Deskriptortyp nicht definiert ist, gibt die Funktion SQL_SUCCESS zurück, aber der für das Feld zurückgegebene Wert ist nicht definiert. Wenn Sie z. B. **SQLGetDescRec** für die SQL_DESC_NAME oder SQL_DESC_NULLABLE Feld einer APD oder ARD aufrufen, wird SQL_SUCCESS jedoch ein nicht definierter Wert für das Feld zurückgegeben.  
  
 Wenn eine Anwendung **SQLGetDescRec** aufruft, um den Wert eines Felds abzurufen, das für einen bestimmten Deskriptortyp definiert ist, aber keinen Standardwert hat und noch nicht festgelegt wurde, gibt die Funktion SQL_SUCCESS zurück, aber der für das Feld zurückgegebene Wert ist nicht definiert. Weitere Informationen finden Sie unter "Initialisierung von Deskriptorfeldern" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Die Werte von Feldern können auch einzeln durch einen Aufruf von **SQLGetDescField**abgerufen werden. Eine Beschreibung der Felder in einem Deskriptorheader oder -datensatz finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptoren](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden einer Spalte|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Binden eines Parameters|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Abrufen eines Deskriptorfelds|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Festlegen mehrerer Deskriptorfelder|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
