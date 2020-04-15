---
title: SQLRemoveDriver-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303931"
---
# <a name="sqlremovedriver-function"></a>SQLRemoveDriver-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLRemoveDriver** ändert oder entfernt Informationen über den Treiber aus dem Eintrag Odbcinst.ini in den Systeminformationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLRemoveDriver(  
     LPCSTR   lpszDriver,  
     BOOL     fRemoveDSN,  
     LPDWORD  lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszDriver*  
 [Eingabe] Der Name des Treibers, der im Schlüssel Odbcinst.ini der Systeminformationen registriert ist.  
  
 *fRemoveDSN*  
 [Eingabe] Die gültigen Werte sind:  
  
 TRUE: Entfernen Sie DSNs, die dem in *lpszDriver*angegebenen Treiber zugeordnet sind. FALSE: Entfernen Sie keine DSNs, die dem in *lpszDriver*angegebenen Treiber zugeordnet sind.  
  
 *lpdwUsageCount*  
 [Ausgabe] Die Verwendungsanzahl des Treibers, nachdem diese Funktion aufgerufen wurde.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt. Wenn beim Aufruf dieser Funktion kein Eintrag in den Systeminformationen vorhanden ist, gibt die Funktion FALSE zurück.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLRemoveDriver** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Komponente, die in der Registrierung nicht gefunden wurde|Das Installationsprogramm konnte die Treiberinformationen nicht entfernen, da sie entweder nicht in der Registrierung vorhanden waren oder nicht in der Registrierung gefunden wurden.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber- oder Übersetzername|Das *Argument lpszDriver* war ungültig.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Die Anzahl der Komponentenverwendung konnte nicht erhöht oder dekrementiert werden.|Der Installer konnte die Nutzungsanzahl des Treibers nicht dekrementierungsmittel.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Das *fRemoveDSN-Argument* war TRUE; Ein oder mehrere DSNs konnten jedoch nicht entfernt werden. Der Aufruf von **SQLConfigDriver** mit der ODBC_REMOVE_DRIVER-Anforderung ist fehlgeschlagen.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLRemoveDriver** ergänzt die [SQLInstallDriverEx-Funktion](../../../odbc/reference/syntax/sqlinstalldriverex-function.md) und aktualisiert die Verwendungsanzahl der Komponenten in den Systeminformationen. Diese Funktion sollte nur von einer Setupanwendung aufgerufen werden.  
  
 **SQLRemoveDriver** dekrementierung den Wert für die Verwendung der Komponenten um 1. Wenn die Anzahl der Komponentenverwendungen auf 0 geht, tritt Folgendes auf:  
  
1.  Die **SQLConfigDriver-Funktion** mit der Option ODBC_REMOVE_DRIVER wird aufgerufen. Wenn die Option *fRemoveDSN* auf TRUE festgelegt ist, ruft die **ConfigDSN-Funktion** **SQLRemoveDSNFromIni** auf, um alle Datenquellen zu entfernen, die dem in *lpszDriver* angegebenen Treiber zugeordnet sind. Wenn die Option *fRemoveDSN* auf FALSE festgelegt ist, werden die Datenquellen nicht gelöscht.  
  
2.  Der Treibereintrag in den Systeminformationen wird entfernt. Der Treibereintrag befindet sich im folgenden Systeminformationsort unter dem Treibernamen:  
  
     `HKEY_LOCAL_MACHINE`  
  
     `SOFTWARE`  
  
     `ODBC`  
  
     `Odbcinst.ini`  
  
 **SQLRemoveDriver** entfernt keine Dateien. Das aufrufende Programm ist für das Löschen von Dateien und die Aufrechterhaltung der Dateinutzungsanzahl verantwortlich. Erst nachdem sowohl die Anzahl der Komponentenverwendung als auch die Dateinutzungsanzahl Null erreicht haben, wird eine Datei physisch gelöscht. Einige Dateien in einer Komponente können gelöscht und andere nicht gelöscht werden, je nachdem, ob die Dateien von anderen Anwendungen verwendet werden, die die Dateinutzungsanzahl erhöht haben.  
  
 **SQLRemoveDriver** wird auch als Teil eines Aktualisierungsprozesses aufgerufen. Wenn eine Anwendung erkennt, dass sie ein Upgrade durchführen muss, und sie den Treiber zuvor installiert hat, sollte der Treiber entfernt und dann neu installiert werden. **SQLRemoveDriver** sollte zuerst aufgerufen werden, um die Anzahl der Komponentenverwendungen zu reduzieren, und dann sollte **SQLInstallDriverEx** aufgerufen werden, um die Anzahl der Komponentenverwendungen zu erhöhen. Das Anwendungseinrichtungsprogramm muss die alten Dateien durch die neuen Dateien ersetzen. Die Anzahl der Dateiverwendungen bleibt unverändert, und andere Anwendungen, die die älteren Versionsdateien verwenden, verwenden nun die neuere Version.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, Ändern oder Entfernen eines Treibers|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md) (in der Setup-DLL)|  
|Hinzufügen, Ändern oder Entfernen eines Treibers|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Installieren eines Treibers|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|
