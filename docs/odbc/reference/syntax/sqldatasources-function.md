---
description: SQLDataSources-Funktion
title: SQLDataSources-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: bcf57779916b7a9d3189a5ce37b8603e5da5cb74
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461182"
---
# <a name="sqldatasources-function"></a>SQLDataSources-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
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
 *Environment-THandle*  
 Der Umgebungs Handle.  
  
 *Richtung*  
 Der Bestimmt, welche Datenquelle der Treiber-Manager Informationen zurückgibt. Mögliche Werte sind:  
  
 SQL_FETCH_NEXT (um den nächsten Datenquellen Namen in der Liste abzurufen), SQL_FETCH_FIRST (um vom Anfang der Liste abzurufen), SQL_FETCH_FIRST_USER (zum Abrufen des ersten Benutzer-DSN) oder SQL_FETCH_FIRST_SYSTEM (zum Abrufen des ersten System-DSN).  
  
 Wenn *Direction* auf SQL_FETCH_FIRST festgelegt ist, werden bei nachfolgenden Aufrufen von **SQLDataSources** mit *Richtung* auf SQL_FETCH_NEXT sowohl Benutzer-als auch System-DSNs zurückgegeben. Wenn *Direction* auf SQL_FETCH_FIRST_USER festgelegt ist, werden bei allen nachfolgenden Aufrufen von **SQLDataSources** mit *Richtung* auf SQL_FETCH_NEXT nur Benutzer-DSNs zurückgegeben. Wenn *Direction* auf SQL_FETCH_FIRST_SYSTEM festgelegt ist, werden bei allen nachfolgenden Aufrufen von **SQLDataSources** mit der *Richtung* auf SQL_FETCH_NEXT nur System-DSNs zurückgegeben.  
  
 *ServerName*  
 Ausgeben Zeiger auf einen Puffer, in den der Datenquellen Name zurückgegeben werden soll.  
  
 Wenn *Servername* NULL ist, gibt *NameLength1Ptr* weiterhin die Gesamtzahl der Zeichen zurück (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten), die im Puffer zurückgegeben werden können, auf den *Servername*zeigt.  
  
 *BufferLength1*  
 Der Länge des **Servername* -Puffers in Zeichen; Dies muss nicht länger als SQL_MAX_DSN_LENGTH plus das NULL-Terminierungs Zeichen sein.  
  
 *NameLength1Ptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (mit Ausnahme des NULL-Beendigungs Zeichens) zurückgegeben werden soll, die in \* *Servername*zurückgegeben werden soll. Wenn die Anzahl der zurück zugebende Zeichen größer als oder gleich *BufferLength1*ist, wird der Datenquellen Name in \* *Servername* auf *BufferLength1* abzüglich der Länge eines NULL-Beendigungs Zeichens gekürzt.  
  
 *Beschreibung*  
 Ausgeben Zeiger auf einen Puffer, in den die Beschreibung des Treibers zurückgegeben werden soll, der der Datenquelle zugeordnet ist. Beispielsweise dBASE oder SQL Server.  
  
 Wenn *Description* den Wert NULL hat, gibt *NameLength2Ptr* weiterhin die Gesamtzahl der Zeichen zurück (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten), die im Puffer zurückgegeben werden können, auf den die *Beschreibung*zeigt.  
  
 *BufferLength2*  
 Der Länge in Zeichen des **Description* -Puffers.  
  
 *NameLength2Ptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (ausgenommen des NULL-Beendigungs Zeichens) zurückgegeben werden soll, die in der Beschreibung zurückgegeben werden können \* *Description*. Wenn die Anzahl der zurück zugebende Zeichen größer als oder gleich *BufferLength2*ist, wird die Beschreibung des Treibers in \* *Description* auf *BufferLength2* abzüglich der Länge eines NULL-Beendigungs Zeichens gekürzt.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDataSources** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_ENV und einem *handle* von *environmenthandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **SQLDataSources** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|(DM) Treiber-Manager-spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|(DM) der Puffer \* *Server* Name war nicht groß genug, um den Namen der kompletten Datenquelle zurückzugeben. Daher wurde der Name abgeschnitten. Die Länge des gesamten Datenquellen namens wird in \* *NameLength1Ptr*zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> (DM) die Puffer \* *Beschreibung* war nicht groß genug, um die komplette Treiber Beschreibung zurückzugeben. Daher wurde die Beschreibung abgeschnitten. Die Länge der den ungekürzten anzuzeigen-Datenquellen Beschreibung wird in **NameLength2Ptr*zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|(DM) ein Fehler ist aufgetreten, für den kein bestimmter SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|(DM) der Treiber-Manager konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY010|Funktions Sequenz Fehler|(DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der für das Argument *BufferLength1* angegebene Wert war kleiner als 0 (null).<br /><br /> (DM) der für das Argument *BufferLength2* angegebene Wert war kleiner als 0 (null).|  
|HY103|Ungültiger Abruf Code|(DM) der für die Argument *Richtung* angegebene Wert war nicht gleich SQL_FETCH_FIRST, SQL_FETCH_FIRST_USER, SQL_FETCH_FIRST_SYSTEM oder SQL_FETCH_NEXT.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Kommentare  
 Da **SQLDataSources** im Treiber-Manager implementiert ist, wird es für alle Treiber unabhängig von der Standards-Konformität eines bestimmten Treibers unterstützt.  
  
 Eine Anwendung kann **SQLDataSources** mehrmals aufrufen, um alle Datenquellen Namen abzurufen. Der Treiber-Manager ruft diese Informationen aus den Systeminformationen ab. Wenn keine weiteren Datenquellen Namen vorhanden sind, gibt der Treiber-Manager SQL_NO_DATA zurück. Wenn **SQLDataSources** mit SQL_FETCH_NEXT unmittelbar nach der Rückgabe SQL_NO_DATA aufgerufen wird, wird der erste Datenquellen Name zurückgegeben. Informationen dazu, wie eine Anwendung die von **SQLDataSources**zurückgegebenen Informationen verwendet, finden Sie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Wenn SQL_FETCH_NEXT an **SQLDataSources** übergeben wird, wenn er zum ersten Mal aufgerufen wird, wird der erste Datenquellen Name zurückgegeben.  
  
 Der Treiber bestimmt, wie Datenquellen Namen tatsächlichen Datenquellen zugeordnet werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Ermitteln und Auflisten von Werten, die für die Verbindung mit einer Datenquelle erforderlich sind|[SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle über eine Verbindungs Zeichenfolge oder ein Dialogfeld|[SQLDriverConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Zurückgeben von Treiber Beschreibungen und-Attributen|[SQLDrivers-Funktion](../../../odbc/reference/syntax/sqldrivers-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
