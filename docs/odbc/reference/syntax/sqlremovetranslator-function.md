---
title: Sqlremovetranslator-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveTranslator
helpviewer_keywords:
- SQLRemoveTranslator function [ODBC]
ms.assetid: c6feda49-0359-4224-8de9-77125cf2397b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 348d2c5da0731ba88ccd4dd6406d3754890f7906
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301787"
---
# <a name="sqlremovetranslator-function"></a>SQLRemoveTranslator-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0  
  
 **Zusammenfassung**  
 **Sqlremovetranslator** entfernt Informationen zu einem Konvertierer aus dem Abschnitt "Odbcinst. ini" der Systeminformationen und dekretet die Anzahl der Komponenten der Übersetzer um 1.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLRemoveTranslator(  
     LPCSTR    lpszTranslator,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpsztranslator*  
 Der Der Name des Konvertierers, der im Schlüssel "Odbcinst. ini" der Systeminformationen registriert ist.  
  
 *lpdwusagecount*  
 Ausgeben Die Verwendungs Anzahl des Konvertierers, nachdem diese Funktion aufgerufen wurde.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false. Wenn in den Systeminformationen kein Eintrag vorhanden ist, wenn diese Funktion aufgerufen wird, gibt die Funktion false zurück.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlremovetranslator** "false" zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von **sqlinstallererror**abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Komponente wurde in der Registrierung nicht gefunden.|Der Installer konnte die Konvertierungs Informationen nicht entfernen, weil er entweder nicht in der Registrierung vorhanden war oder in der Registrierung nicht gefunden wurde.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber-oder Konvertierungs Name|Das *lpsztranslator* -Argument war ungültig.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Die Anzahl der Komponenten Verwendung konnte nicht erhöht oder verringert werden.|Der Installer konnte die Verwendungs Anzahl des Treibers nicht Dekrementen.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **Sqlremovetranslator** ergänzt die [sqlinstalltranslatorex](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md) -Funktion und aktualisiert die Anzahl der Komponenten Verwendung in den Systeminformationen. Diese Funktion sollte nur von einer Setup Anwendung aufgerufen werden.  
  
 **Sqlremovetranslator** dekretet die Anzahl von Komponenten Verwendungsraten um 1. Wenn die Anzahl der Komponenten Verwendungs Daten auf 0 (null) sinkt, wird der Konvertierungs Eintrag in den Systeminformationen entfernt. Der Konvertierer Eintrag befindet sich an folgendem Speicherort in den Systeminformationen unter dem Namen des Konvertierers:  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
 **Sqlremovetranslator** entfernt tatsächlich keine Dateien. Das aufrufende Programm ist für das Löschen von Dateien und das Beibehalten der Datei Verwendungs Anzahl zuständig. Nur nachdem die Anzahl der Komponenten Verwendung und die Anzahl der Datei Verwendung erreicht ist, wird eine Datei physisch gelöscht. Einige Dateien in einer Komponente können gelöscht und andere nicht gelöscht werden. Dies hängt davon ab, ob die Dateien von anderen Anwendungen verwendet werden, die die Anzahl der Datei Auslastung erhöht haben.  
  
 **Sqlremovetranslator** wird auch als Teil eines Upgradevorgangs aufgerufen. Wenn eine Anwendung erkennt, dass ein Upgrade ausgeführt werden muss, und der Treiber bereits installiert wurde, sollte der Treiber entfernt und dann neu installiert werden. **Sqlremovetranslator** sollte zuerst aufgerufen werden, um die Anzahl von Komponenten Verwendungsraten zu verringern. Anschließend sollte **sqlinstalltranslatorex** aufgerufen werden, um die Anzahl der Komponenten Verwendungsraten zu erhöhen. Das Anwendungs Setup Programm muss die alten Dateien physisch durch die neuen Dateien ersetzen. Die Anzahl der Datei Verwendungs Daten bleibt unverändert, und andere Anwendungen, die die älteren Versions Dateien verwenden, verwenden nun die neuere Version.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Installieren eines Konvertierers|[Sqlinstalltranslatorex](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|
