---
title: Sqlremovedriver-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriver
helpviewer_keywords:
- SQLRemoveDriver function [ODBC]
ms.assetid: 9a3b4f8b-982b-44b9-ade6-754ff026dc90
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 205c5b46e5f6cea195094f7a50e81d7509927d1a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303931"
---
# <a name="sqlremovedriver-function"></a>SQLRemoveDriver-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0  
  
 **Zusammenfassung**  
 **Sqlremovedriver** ändert oder entfernt Informationen zum Treiber aus dem Eintrag "Odbcinst. ini" in den Systeminformationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLRemoveDriver(  
     LPCSTR   lpszDriver,  
     BOOL     fRemoveDSN,  
     LPDWORD  lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszDriver*  
 Der Der Name des Treibers, der im Schlüssel "Odbcinst. ini" der Systeminformationen registriert ist.  
  
 *fremuvedsn*  
 Der Gültige Werte sind:  
  
 TRUE: Entfernen Sie DSNs, die dem in *lpszDriver*angegebenen Treiber zugeordnet sind. FALSE: Entfernen Sie keine DSNs, die dem in *lpszDriver*angegebenen Treiber zugeordnet sind.  
  
 *lpdwusagecount*  
 Ausgeben Der Verwendungs Zähler des Treibers, nachdem diese Funktion aufgerufen wurde.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false. Wenn in den Systeminformationen kein Eintrag vorhanden ist, wenn diese Funktion aufgerufen wird, gibt die Funktion false zurück.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlremovedriver** "false" zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von **sqlinstallererror**abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Komponente wurde in der Registrierung nicht gefunden.|Der Installer konnte die Treiber Informationen nicht entfernen, weil er entweder nicht in der Registrierung vorhanden war oder in der Registrierung nicht gefunden wurde.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber-oder Konvertierungs Name|Das *lpszDriver* -Argument war ungültig.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Die Anzahl der Komponenten Verwendung konnte nicht erhöht oder verringert werden.|Der Installer konnte die Verwendungs Anzahl des Treibers nicht Dekrementen.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Das *fremuvedsn* -Argument war ' true '. mindestens ein DSNs konnte jedoch nicht entfernt werden. Der **sqlconfigdriver** -Befehl mit der ODBC_REMOVE_DRIVER Anforderung konnte nicht ausgeführt werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **Sqlremovedriver** ergänzt die [sqlinstalldriverex](../../../odbc/reference/syntax/sqlinstalldriverex-function.md) -Funktion und aktualisiert die Anzahl der Komponenten Verwendung in den Systeminformationen. Diese Funktion sollte nur von einer Setup Anwendung aufgerufen werden.  
  
 **Sqlremovedriver** dekretet den Wert für die Anzahl der Komponenten Verwendung um 1. Wenn die Anzahl der Komponenten Verwendungs Zeit auf 0 (null) sinkt, geschieht Folgendes:  
  
1.  Die **sqlconfigdriver** -Funktion mit der ODBC_REMOVE_DRIVER-Option wird aufgerufen. Wenn die *frefivedsn* -Option auf true festgelegt ist, ruft die **ConfigDSN** -Funktion **sqlremovedsnfromini** auf, um alle Datenquellen zu entfernen, die dem in *lpszDriver* angegebenen Treiber zugeordnet sind. Wenn die *fremuvedsn* -Option auf false festgelegt ist, werden die Datenquellen nicht gelöscht.  
  
2.  Der Treiber Eintrag in den Systeminformationen wird entfernt. Der Treiber Eintrag befindet sich am folgenden Speicherort der Systeminformationen unter dem Namen des Treibers:  
  
     `HKEY_LOCAL_MACHINE`  
  
     `SOFTWARE`  
  
     `ODBC`  
  
     `Odbcinst.ini`  
  
 **Sqlremovedriver** entfernt tatsächlich keine Dateien. Das aufrufende Programm ist für das Löschen von Dateien und das Beibehalten der Datei Verwendungs Anzahl zuständig. Nur nachdem die Anzahl der Komponenten Verwendung und die Anzahl der Datei Verwendung erreicht ist, wird eine Datei physisch gelöscht. Einige Dateien in einer Komponente können gelöscht und andere nicht gelöscht werden. Dies hängt davon ab, ob die Dateien von anderen Anwendungen verwendet werden, die die Anzahl der Datei Auslastung erhöht haben.  
  
 **Sqlremovedriver** wird auch als Teil eines Upgradevorgangs aufgerufen. Wenn eine Anwendung erkennt, dass ein Upgrade ausgeführt werden muss, und der Treiber bereits installiert wurde, sollte der Treiber entfernt und dann neu installiert werden. **Sqlremovedriver** sollte zuerst aufgerufen werden, um die Anzahl von Komponenten Verwendungsraten zu verringern. Anschließend sollte **sqlinstalldriverex** aufgerufen werden, um die Anzahl der Komponenten Auslastung zu erhöhen. Das Setup Programm der Anwendung muss die alten Dateien durch die neuen Dateien ersetzen. Die Anzahl der Datei Verwendungs Daten bleibt unverändert, und andere Anwendungen, die die älteren Versions Dateien verwenden, verwenden nun die neuere Version.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen eines Treibers|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md) (in der Setup-DLL)|  
|Hinzufügen, ändern oder Entfernen eines Treibers|[Sqlconfigdriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Installieren eines Treibers|[Sqlinstalldriverex](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|
