---
title: SQLDrivers-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302761"
---
# <a name="sqldrivers-function"></a>SQLDrivers-Funktion
**Konformität**  
 Eingeführte Version: ODBC 2.0-Normkonformität: ODBC  
  
 **Zusammenfassung**  
 **SQLDrivers** listet Treiberbeschreibungen und Schlüsselwörter für Treiberattribute auf. Diese Funktion wird nur vom Treiber-Manager implementiert.  
  
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
 *EnvironmentHandle*  
 [Eingabe] Umgebungshandle.  
  
 *Richtung*  
 [Eingabe] Bestimmt, ob der Treiber-Manager die nächste Treiberbeschreibung in der Liste abruft (SQL_FETCH_NEXT) oder ob die Suche am Anfang der Liste beginnt (SQL_FETCH_FIRST).  
  
 *DriverDescription*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem die Treiberbeschreibung zurückgegeben werden soll.  
  
 Wenn *DriverDescription* NULL ist, gibt *DescriptionLengthPtr* weiterhin die Gesamtzahl der Zeichen (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten) zurück, die im Puffer zurückgegeben werden können, auf den *DriverDescription*zeigt.  
  
 *BufferLength1*  
 [Eingabe] Länge des **DriverDescription-Puffers* in Zeichen.  
  
 *BeschreibungLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (mit Ausnahme \*des Null-Beendigungszeichens) zurückgegeben werden soll, die in *DriverDescription*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Zeichen größer oder gleich *BufferLength1*ist, wird die Treiberbeschreibung in \* *DriverDescription* auf *BufferLength1* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten.  
  
 *DriverAttributes*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem die Liste der Treiberattributwertpaare zurückgegeben werden soll (siehe "Kommentare").  
  
 Wenn DriverAttributes NULL ist, gibt *AttributesLengthPtr* weiterhin die Gesamtzahl der Bytes zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), auf die im Puffer von *DriverAttributes*verwiesen wird. *DriverAttributes*  
  
 *BufferLength2*  
 [Eingabe] Länge des \* *DriverAttributes-Puffers* in Zeichen. Wenn der * \*DriverDescription-Wert* eine Unicode-Zeichenfolge ist (beim Aufrufen von **SQLDriversW**), muss das *BufferLength-Argument* eine gerade Zahl sein.  
  
 *AttributeLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes (mit Ausnahme des \*NULL-Beendigungsbytes) zurückgegeben werden soll, die in *DriverAttributes*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *BufferLength2*ist, \*wird die Liste der Attributwertpaare in *DriverAttributes* auf *BufferLength2* abzüglich der Länge des Nullbeendigungszeichens abgeschnitten.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDrivers** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_ENV und einem *Handle* von *EnvironmentHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von SQLDrivers zurückgegeben werden, und es werden die **SQLSTATE-Werte** im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|(DM) Treiber-Manager-spezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|(DM) Der \*Puffer *DriverDescription* war nicht groß genug, um die vollständige Treiberbeschreibung zurückzugeben. Daher wurde die Beschreibung abgeschnitten. Die Länge der vollständigen Treiberbeschreibung \*wird in *DescriptionLengthPtr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> (DM) Der \*Puffer *DriverAttributes* war nicht groß genug, um die vollständige Liste der Attributwertpaare zurückzugeben. Daher wurde die Liste abgeschnitten. Die Länge der nicht abgeschnittenen Liste der Attributwertpaare wird in **AttributesLengthPtr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|(DM) Der Treiber-Manager konnte keinen Speicher zuweisen, der zur Unterstützung der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY010|Funktionssequenzfehler|(DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der für das Argument *BufferLength1* angegebene Wert war kleiner als 0.<br /><br /> (DM) Der für das Argument *BufferLength2* angegebene Wert war kleiner als 0 oder gleich 1.|  
|HY103|Ungültiger Abrufcode|(DM) Der für das Argument *Direction* angegebene Wert entsprach nicht SQL_FETCH_FIRST oder SQL_FETCH_NEXT.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Kommentare  
 **SQLDrivers** gibt die Treiberbeschreibung im \* *DriverDescription-Puffer* zurück. Es gibt zusätzliche Informationen über \*den Treiber im *DriverAttributes-Puffer* als Liste von Schlüsselwort-Wert-Paaren zurück. Alle Schlüsselwörter, die in den Systeminformationen für Treiber aufgeführt sind, werden für alle Treiber zurückgegeben, mit Ausnahme von **CreateDSN**, das zum Anfordern der Erstellung von Datenquellen verwendet wird und daher optional ist. Jedes Paar wird mit einem NULL-Byte beendet, und die vollständige Liste wird mit einem NULL-Byte beendet (d. h., zwei Nullbytes markieren das Ende der Liste). Beispielsweise kann ein dateibasierter Treiber mit C-Syntax die folgende Liste von Attributen zurückgeben ("-0" stellt ein Nullzeichen dar):  
  
```  
FileUsage=1\0FileExtns=*.dbf\0\0  
```  
  
 Wenn \* *DriverAttributes* nicht groß genug ist, um die gesamte Liste aufzunehmen, wird die Liste abgeschnitten, **SQLDrivers** gibt SQLSTATE 01004 zurück (Daten abgeschnitten), und die Länge der Liste (mit Ausnahme des endgültigen Null-Beendigungsbytes) wird in **AttributesLengthPtr*zurückgegeben.  
  
 Schlüsselwörter für Treiberattribute werden aus den Systeminformationen hinzugefügt, wenn der Treiber installiert wird. Weitere Informationen finden Sie unter [Installieren von ODBC-Komponenten](../../../odbc/reference/install/installing-odbc-components.md).  
  
 Eine Anwendung kann **SQLDrivers** mehrmals aufrufen, um alle Treiberbeschreibungen abzurufen. Der Treiber-Manager ruft diese Informationen aus den Systeminformationen ab. Wenn keine Treiberbeschreibungen mehr vorhanden sind, gibt **SQLDrivers** SQL_NO_DATA zurück. Wenn **SQLDrivers** mit SQL_FETCH_NEXT sofort aufgerufen wird, nachdem es SQL_NO_DATA zurückgegeben hat, gibt es die erste Treiberbeschreibung zurück. Informationen dazu, wie eine Anwendung die von **SQLDrivers**zurückgegebenen Informationen verwendet, finden Sie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Wenn SQL_FETCH_NEXT beim ersten Aufruf an **SQLDrivers** übergeben wird, gibt **SQLDrivers** den ersten Datenquellennamen zurück.  
  
 Da **SQLDrivers** im Treiber-Manager implementiert ist, wird es für alle Treiber unterstützt, unabhängig von der Einhaltung der Standards eines bestimmten Treibers.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Ermitteln und Auflisten von Werten, die zum Herstellen einer Verbindung mit einer Datenquelle erforderlich sind|[SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Zurückgeben von Datenquellennamen|[SQLDataSources-Funktion](../../../odbc/reference/syntax/sqldatasources-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle über eine Verbindungszeichenfolge oder ein Dialogfeld|[SQLDriveConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
