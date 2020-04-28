---
title: SQLDrivers-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDrivers
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDrivers
helpviewer_keywords:
- SQLDrivers function [ODBC]
ms.assetid: 6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2496e7cd5f2abe0831c72484bed374d7aa1513ce
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302761"
---
# <a name="sqldrivers-function"></a>SQLDrivers-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 2,0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLDrivers** listet Treiber Beschreibungen und Treiber Attribut Schlüsselwörter auf. Diese Funktion wird nur vom Treiber-Manager implementiert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLDrivers(  
     SQLHENV         EnvironmentHandle,  
     SQLUSMALLINT    Direction,  
     SQLCHAR *       DriverDescription,  
     SQLSMALLINT     BufferLength1,  
     SQLSMALLINT *   DescriptionLengthPtr,  
     SQLCHAR *       DriverAttributes,  
     SQLSMALLINT     BufferLength2,  
     SQLSMALLINT *   AttributesLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *Environment-THandle*  
 Der Umgebungs Handle.  
  
 *Richtung*  
 Der Bestimmt, ob der Treiber-Manager die nächste Treiber Beschreibung in der Liste (SQL_FETCH_NEXT) abruft oder ob die Suche am Anfang der Liste beginnt (SQL_FETCH_FIRST).  
  
 *Driverdescription*  
 Ausgeben Zeiger auf einen Puffer, in den die Treiber Beschreibung zurückgegeben werden soll.  
  
 Wenn *driverdescription* auf NULL festgelegt ist, gibt *descriptionlängen PTR* weiterhin die Gesamtzahl der Zeichen (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten) zurück, die im Puffer zurückgegeben werden können, auf den von *driverdescription*verwiesen wird.  
  
 *BufferLength1*  
 Der Länge des **driverdescription* -Puffers in Zeichen.  
  
 *Deskriptionverlängert*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (ausgenommen des NULL-Beendigungs Zeichens) zurückgegeben werden \*soll, die in *driverdescription*zurückgegeben werden können. Wenn die Anzahl der zurück zugebende Zeichen größer als oder gleich *BufferLength1*ist, wird die Treiber Beschreibung in \* *driverdescription* auf *BufferLength1* abzüglich der Länge eines NULL-Beendigungs Zeichens gekürzt.  
  
 *Driverattribute*  
 Ausgeben Ein Zeiger auf einen Puffer, in den die Liste der Wert Paare für Treiber Attribute zurückgegeben werden soll (siehe "comments").  
  
 Wenn *driverattribute* gleich NULL ist, gibt *attributeslängen PTR* weiterhin die Gesamtzahl der Bytes (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten) zurück, die im Puffer zurückgegeben werden können, auf den *driverattribute*zeigt.  
  
 *BufferLength2*  
 Der Länge des \* *driverattribute* -Puffers in Zeichen. Wenn der * \*driverdescription* -Wert eine Unicode-Zeichenfolge ist (beim Aufrufen von **sqldriversw**), muss das *BufferLength* -Argument eine gerade Zahl sein.  
  
 *Attributesverlänptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes (mit Ausnahme des NULL-Beendigungs Bytes) zurückgegeben \*werden soll, die in *driverattribute*zurückgegeben werden können. Wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder *gleich BufferLength2*ist, wird die Liste der Attribut \*Wert Paare in *driverattribute* auf *BufferLength2* abzüglich der Länge des NULL-Beendigungs Zeichens gekürzt.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDrivers** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_ENV und einem *handle* von *environmenthandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **SQLDrivers** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|(DM) Treiber-Manager-spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|(DM) der Puffer \*" *driverdescription* " war nicht groß genug, um die komplette Treiber Beschreibung zurückzugeben. Daher wurde die Beschreibung abgeschnitten. Die Länge der Beschreibung des kompletten Treibers wird in \* *descriptionlängen PTR*zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> (DM) der Puffer \*" *driverattribute* " war nicht groß genug, um die gesamte Liste der Attribut Wert Paare zurückzugeben. Daher wurde die Liste abgeschnitten. Die Länge der nicht abgeschnittene Liste von Attribut Wert Paaren wird in **attributeslängen PTR*zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|(DM) der Treiber-Manager konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY010|Funktions Sequenz Fehler|(DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der für das Argument *BufferLength1* angegebene Wert war kleiner als 0 (null).<br /><br /> (DM) der für das Argument *BufferLength2* angegebene Wert war kleiner als 0 (null) oder gleich 1.|  
|HY103|Ungültiger Abruf Code|(DM) der für die Argument *Richtung* angegebene Wert war nicht gleich SQL_FETCH_FIRST oder SQL_FETCH_NEXT.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Kommentare  
 **SQLDrivers** gibt die Treiber Beschreibung im \* *driverdescription* -Puffer zurück. Sie gibt zusätzliche Informationen über den Treiber im \* *driverattribute* -Puffer als Liste von Schlüsselwort-Wert-Paaren zurück. Alle in den Systeminformationen für Treiber aufgeführten Schlüsselwörter werden für alle Treiber zurückgegeben, mit Ausnahme von " **upatedsn**", die zum Anfordern der Erstellung von Datenquellen verwendet wird und daher optional ist. Jedes Paar wird mit einem NULL-Byte beendet, und die gesamte Liste wird mit einem NULL-Byte beendet (d. h., zwei NULL-Bytes markieren das Ende der Liste). Ein Datei basierter Treiber, der die C-Syntax verwendet, könnte z. b. die folgende Liste von Attributen zurückgeben ("\ 0" steht für ein NULL-Zeichen):  
  
```  
FileUsage=1\0FileExtns=*.dbf\0\0  
```  
  
 Wenn \*" *driverattribute* " nicht groß genug ist, um die gesamte Liste aufzunehmen, wird die Liste abgeschnitten, **SQLDrivers** gibt SQLSTATE 01004 (abgeschnittene Daten) zurück, und die Länge der Liste (mit Ausnahme des endgültigen NULL-Beendigungs Bytes) wird in **attributeslängen PTR*zurückgegeben.  
  
 Treiber Attribut Schlüsselwörter werden aus den Systeminformationen hinzugefügt, wenn der Treiber installiert wird. Weitere Informationen finden Sie unter [Installieren von ODBC-Komponenten](../../../odbc/reference/install/installing-odbc-components.md).  
  
 Eine Anwendung kann **SQLDrivers** mehrmals aufrufen, um alle Treiber Beschreibungen abzurufen. Der Treiber-Manager ruft diese Informationen aus den Systeminformationen ab. Wenn keine Treiber Beschreibungen mehr vorhanden sind, gibt **SQLDrivers** SQL_NO_DATA zurück. Wenn **SQLDrivers** mit SQL_FETCH_NEXT unmittelbar nach dem zurückkehren SQL_NO_DATA aufgerufen wird, wird die erste Treiber Beschreibung zurückgegeben. Informationen dazu, wie eine Anwendung die von **SQLDrivers**zurückgegebenen Informationen verwendet, finden Sie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Wenn SQL_FETCH_NEXT zum ersten Mal an **SQLDrivers** weitergegeben wird, gibt **SQLDrivers** den ersten Datenquellen Namen zurück.  
  
 Da **SQLDrivers** im Treiber-Manager implementiert ist, wird es für alle Treiber unabhängig von der Standards-Konformität eines bestimmten Treibers unterstützt.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Ermitteln und Auflisten von Werten, die für die Verbindung mit einer Datenquelle erforderlich sind|[SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Zurückgeben von Datenquellen Namen|[SQLDataSources-Funktion](../../../odbc/reference/syntax/sqldatasources-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle über eine Verbindungs Zeichenfolge oder ein Dialogfeld|[SQLDriveConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
