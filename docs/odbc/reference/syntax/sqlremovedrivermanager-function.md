---
title: SQLRemoveDriverManager-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriverManager
helpviewer_keywords:
- SQLRemoveDriverManager function function [ODBC]
ms.assetid: 3a41511f-6603-4b81-a815-7883874023c4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 27b32c1c4e0f3f4d5359af287ba07d40b033af00
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301811"
---
# <a name="sqlremovedrivermanager-function"></a>SQLRemoveDriverManager-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0: Veraltet in Windows XP Service Pack 2, Windows Server 2003 Service Pack 1 und neueren Betriebssystemen.  
  
 **Zusammenfassung**  
 **SQLRemoveDriverManager** ändert oder entfernt Informationen zu den ODBC-Kernkomponenten aus dem Eintrag Odbcinst.ini in den Systeminformationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLRemoveDriverManager(  
     LPDWORD     pdwUsageCount);  
```  
  
## <a name="arguments"></a>Argumente  
 *pdwUsageCount*  
 [Ausgabe] Die Verwendungsanzahl des Treiber-Managers, nachdem diese Funktion aufgerufen wurde.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt. Wenn beim Aufruf dieser Funktion kein Eintrag in den Systeminformationen vorhanden ist, gibt die Funktion FALSE zurück.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLRemoveDriverManager** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Komponente, die in der Registrierung nicht gefunden wurde|Das Installationsprogramm konnte die Driver Manager-Informationen nicht entfernen, da sie entweder nicht in der Registrierung vorhanden waren oder nicht in der Registrierung gefunden wurden.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Die Anzahl der Komponentenverwendung konnte nicht erhöht oder dekrementiert werden.|Das Installationsprogramm konnte die Nutzungsanzahl des Treiber-Managers nicht dekrementierung.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLRemoveDriverManager** ergänzt die **SQLInstallDriverManager-Funktion** und aktualisiert die Verwendungsanzahl der Komponenten in den Systeminformationen. Diese Funktion sollte nur von einer Setupanwendung aufgerufen werden.  
  
 **SQLRemoveDriverManager** dekrementierung der Anzahl der Kernkomponentennutzung um 1. Wenn die Anzahl der Komponentenverwendungen auf 0 geht, werden die Eintragssysteminformationen entfernt. Der Kernkomponenteneintrag befindet sich an folgender Stelle in den Systeminformationen unter dem Titel "ODBC Core":  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
> [!CAUTION]  
>  Eine Anwendung sollte Driver Manager-Dateien nicht physisch entfernen, wenn die Anzahl der Komponentenverwendung und die Anzahl der Dateiverwendungen Null erreichen.  
  
 **SQLRemoveDriverManager** entfernt keine Dateien. Das aufrufende Programm ist für das Löschen von Dateien und die Aufrechterhaltung der Dateinutzungsanzahl verantwortlich. Treiber-Manager-Dateien sollten jedoch nicht entfernt werden, wenn sowohl die Anzahl der Komponentenverwendung als auch die Dateinutzungsanzahl Null erreicht haben, da diese Dateien möglicherweise von anderen Anwendungen verwendet werden, die die Anzahl der Dateiverwendungen nicht erhöht haben.  
  
 **SQLRemoveDriverManager** wird als Teil des Deinstallationsvorgangs aufgerufen. ODBC-Kernkomponenten (einschließlich Treiber-Manager, Cursorbibliothek, Installer, Sprachbibliothek, Administrator, Thunking-Dateien usw.) werden als Ganzes deinstalliert. Die folgenden Dateien werden nicht entfernt, wenn **SQLRemoveDriverManager** als Teil des Deinstallationsvorgangs aufgerufen wird:  
  
|||  
|-|-|  
|ODBC32DLL|ODBCCP32. Dll|  
|ODBCCR32. Dll|ODBC16GT. Dll|  
|ODBCCU32. Dll|ODBC32GT. Dll|  
|ODBCINT. Dll|DS16GT. Dll|  
|ODBCTRAC. Dll|DS32GT. Dll|  
|MSVCRT40. Dll|ODBCAD32. EXE|  
|ODBCCP32. Cpl||  
  
 **SQLRemoveDriverManager** wird auch als Teil eines Aktualisierungsprozesses aufgerufen. Wenn eine Anwendung erkennt, dass sie ein Upgrade durchführen muss, und sie den Treiber zuvor installiert hat, sollte der Treiber entfernt und dann neu installiert werden.  
  
 **SQLRemoveDriverManager** sollte zuerst aufgerufen werden, um die Anzahl der Komponentenverwendungen zu reduzieren. **SQLInstallDriverEx** sollte dann aufgerufen werden, um die Anzahl der Komponentenverwendungen zu erhöhen. Das Anwendungseinrichtungsprogramm muss die alten Kernkomponentendateien durch die neuen Dateien ersetzen. Die Anzahl der Dateiverwendungen bleibt unverändert, und andere Anwendungen, die die älteren Versionskernkomponentendateien verwenden, verwenden nun die neueren Versionsdateien.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Installieren eines Treiber-Managers|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
