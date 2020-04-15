---
title: SQLRemoveTranslator-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301787"
---
# <a name="sqlremovetranslator-function"></a>SQLRemoveTranslator-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLRemoveTranslator** entfernt Informationen über einen Übersetzer aus dem Abschnitt Odbcinst.ini der Systeminformationen und dekrementiert die Anzahl der Komponenten des Übersetzers um 1.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLRemoveTranslator(  
     LPCSTR    lpszTranslator,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszÜbersetzer*  
 [Eingabe] Der Name des Übersetzers, der im Schlüssel Odbcinst.ini der Systeminformationen registriert ist.  
  
 *lpdwUsageCount*  
 [Ausgabe] Die Verwendungsanzahl des Übersetzers, nachdem diese Funktion aufgerufen wurde.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt. Wenn beim Aufruf dieser Funktion kein Eintrag in den Systeminformationen vorhanden ist, gibt die Funktion FALSE zurück.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLRemoveTranslator** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Komponente, die in der Registrierung nicht gefunden wurde|Das Installationsprogramm konnte die Übersetzerinformationen nicht entfernen, da sie entweder nicht in der Registrierung vorhanden waren oder nicht in der Registrierung gefunden wurden.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber- oder Übersetzername|Das Argument *lpszTranslator* war ungültig.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Die Anzahl der Komponentenverwendung konnte nicht erhöht oder dekrementiert werden.|Der Installer konnte die Nutzungsanzahl des Treibers nicht dekrementierungsmittel.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLRemoveTranslator** ergänzt die [SQLInstallTranslatorEx-Funktion](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md) und aktualisiert die Verwendungsanzahl der Komponenten in den Systeminformationen. Diese Funktion sollte nur von einer Setupanwendung aufgerufen werden.  
  
 **SQLRemoveTranslator** dekrementierung die Anzahl der Komponentenverwendungumschreibungen um 1. Wenn die Anzahl der Komponentenverwendungen auf 0 geht, wird der Übersetzereintrag in den Systeminformationen entfernt. Der Übersetzereintrag befindet sich an folgender Stelle in den Systeminformationen unter dem Namen des Übersetzers:  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
 **SQLRemoveTranslator** entfernt keine Dateien. Das aufrufende Programm ist für das Löschen von Dateien und die Aufrechterhaltung der Dateinutzungsanzahl verantwortlich. Erst nachdem sowohl die Anzahl der Komponentenverwendung als auch die Dateinutzungsanzahl Null erreicht haben, wird eine Datei physisch gelöscht. Einige Dateien in einer Komponente können gelöscht und andere nicht gelöscht werden, je nachdem, ob die Dateien von anderen Anwendungen verwendet werden, die die Dateinutzungsanzahl erhöht haben.  
  
 **SQLRemoveTranslator** wird auch als Teil eines Aktualisierungsprozesses aufgerufen. Wenn eine Anwendung erkennt, dass sie ein Upgrade durchführen muss, und sie den Treiber zuvor installiert hat, sollte der Treiber entfernt und dann neu installiert werden. **SQLRemoveTranslator** sollte zuerst aufgerufen werden, um die Anzahl der Komponentenverwendungen zu reduzieren, und dann sollte **SQLInstallTranslatorEx** aufgerufen werden, um die Anzahl der Komponentenverwendungen zu erhöhen. Das Anwendungseinrichtungsprogramm muss die alten Dateien physisch durch die neuen Dateien ersetzen. Die Anzahl der Dateiverwendungen bleibt unverändert, und andere Anwendungen, die die älteren Versionsdateien verwenden, verwenden nun die neuere Version.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Installieren eines Übersetzers|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|
