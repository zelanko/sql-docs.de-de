---
title: SQLDataSources-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDataSources
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDataSources
helpviewer_keywords:
- SQLDataSources function [ODBC]
ms.assetid: 3f63b1b4-e70e-44cd-96c6-6878d50d0117
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b56a6c25e54897e67beaf39d3b7797ac45391d7b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301180"
---
# <a name="sqldatasources-function"></a>SQLDataSources-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLDataSources** gibt Informationen zu einer Datenquelle zurück. Diese Funktion wird nur vom Treiber-Manager implementiert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLDataSources(  
     SQLHENV          EnvironmentHandle,  
     SQLUSMALLINT     Direction,  
     SQLCHAR *        ServerName,  
     SQLSMALLINT      BufferLength1,  
     SQLSMALLINT *    NameLength1Ptr,  
     SQLCHAR *        Description,  
     SQLSMALLINT      BufferLength2,  
     SQLSMALLINT *    NameLength2Ptr);  
```  
  
## <a name="arguments"></a>Argumente  
 *EnvironmentHandle*  
 [Eingabe] Umgebungshandle.  
  
 *Richtung*  
 [Eingabe] Bestimmt, für welche Datenquelle der Treiber-Manager Informationen zurückgibt. Mögliche Werte sind:  
  
 SQL_FETCH_NEXT (um den nächsten Datenquellennamen in der Liste abzurufen), SQL_FETCH_FIRST (vom Anfang der Liste abzurufen), SQL_FETCH_FIRST_USER (um den ersten Benutzer-DSN abzurufen) oder SQL_FETCH_FIRST_SYSTEM (um den ersten System-DSN abzurufen).  
  
 Wenn *Direction* auf SQL_FETCH_FIRST festgelegt ist, geben nachfolgende Aufrufe von **SQLDataSources** mit *Direction* so SQL_FETCH_NEXT geben sowohl Benutzer- als auch System-DSNs zurück. Wenn *Direction* auf SQL_FETCH_FIRST_USER festgelegt ist, geben alle nachfolgenden Aufrufe von **SQLDataSources** mit *Direction* auf SQL_FETCH_NEXT nur Benutzer-DSNs zurück. Wenn *Direction* auf SQL_FETCH_FIRST_SYSTEM festgelegt ist, geben alle nachfolgenden Aufrufe von **SQLDataSources** mit *Direction* auf SQL_FETCH_NEXT nur System-DSNs zurück.  
  
 *ServerName*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem der Datenquellenname zurückgegeben werden soll.  
  
 Wenn *ServerName* NULL ist, gibt *NameLength1Ptr* weiterhin die Gesamtzahl der Zeichen zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), auf die im Puffer verwiesen wird, auf den *ServerName*zeigt.  
  
 *BufferLength1*  
 [Eingabe] Länge des **ServerName-Puffers* in Zeichen; Dies muss nicht länger als SQL_MAX_DSN_LENGTH plus dem Null-Beendigungszeichen sein.  
  
 *NameLength1Ptr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (mit Ausnahme \*des Null-Beendigungszeichens) zurückgegeben werden soll, die in *ServerName*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Zeichen größer oder gleich *BufferLength1* \*ist, wird der Datenquellenname in *ServerName* auf *BufferLength1* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten.  
  
 *Beschreibung*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Beschreibung des Treibers zurückgegeben werden soll, der der Datenquelle zugeordnet ist. Beispiel: dBASE oder SQL Server.  
  
 Wenn *Beschreibung* NULL ist, gibt *NameLength2Ptr* weiterhin die Gesamtzahl der Zeichen zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), auf die im Puffer mit *Beschreibung*verwiesen wird.  
  
 *BufferLength2*  
 [Eingabe] Länge in Zeichen*Description* des * Beschreibungspuffers.  
  
 *NameLength2Ptr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (mit Ausnahme \*des Null-Beendigungszeichens) zurückgegeben werden soll, die in *Description*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Zeichen größer oder gleich *BufferLength2*ist, wird die Treiberbeschreibung in \* *Description* auf *BufferLength2* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDataSources** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_ENV und einem *Handle* von *EnvironmentHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLDataSources** zurückgegeben werden, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|(DM) Treiber-Manager-spezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|(DM) Der \*Puffer *ServerName* war nicht groß genug, um den vollständigen Datenquellennamen zurückzugeben. Daher wurde der Name abgeschnitten. Die Länge des gesamten Datenquellennamens \*wird in *NameLength1Ptr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> (DM) Die \* *Pufferbeschreibung* war nicht groß genug, um die vollständige Treiberbeschreibung zurückzugeben. Daher wurde die Beschreibung abgeschnitten. Die Länge der nicht abgeschnittenen Datenquellenbeschreibung wird in **NameLength2Ptr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|(DM) Es ist ein Fehler aufgetreten, für den es keine spezifische SQLSTATE gab und für den kein implementierungsspezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|(DM) Der Treiber-Manager konnte keinen Speicher zuweisen, der zur Unterstützung der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY010|Funktionssequenzfehler|(DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der für das Argument *BufferLength1* angegebene Wert war kleiner als 0.<br /><br /> (DM) Der für das Argument *BufferLength2* angegebene Wert war kleiner als 0.|  
|HY103|Ungültiger Abrufcode|(DM) Der für das Argument *Direction* angegebene Wert entsprach nicht SQL_FETCH_FIRST, SQL_FETCH_FIRST_USER, SQL_FETCH_FIRST_SYSTEM oder SQL_FETCH_NEXT.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Kommentare  
 Da **SQLDataSources** im Treiber-Manager implementiert ist, wird es für alle Treiber unterstützt, unabhängig von der Standardkonformität eines bestimmten Treibers.  
  
 Eine Anwendung kann **SQLDataSources** mehrmals aufrufen, um alle Datenquellennamen abzurufen. Der Treiber-Manager ruft diese Informationen aus den Systeminformationen ab. Wenn keine Datenquellennamen mehr vorhanden sind, gibt der Treiber-Manager SQL_NO_DATA zurück. Wenn **SQLDataSources** mit SQL_FETCH_NEXT sofort aufgerufen wird, nachdem es SQL_NO_DATA zurückgegeben hat, wird der erste Datenquellenname zurückgegeben. Informationen dazu, wie eine Anwendung die von **SQLDataSources**zurückgegebenen Informationen verwendet, finden Sie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Wenn SQL_FETCH_NEXT beim ersten Aufruf an **SQLDataSources** übergeben wird, wird der erste Datenquellenname zurückgegeben.  
  
 Der Treiber bestimmt, wie Datenquellennamen tatsächlichen Datenquellen zugeordnet werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Ermitteln und Auflisten von Werten, die zum Herstellen einer Verbindung mit einer Datenquelle erforderlich sind|[SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle über eine Verbindungszeichenfolge oder ein Dialogfeld|[SQLDriveConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Zurückgeben von Treiberbeschreibungen und -attributen|[SQLDrivers-Funktion](../../../odbc/reference/syntax/sqldrivers-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
