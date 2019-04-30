---
title: SQLRemoveDriver-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ef98000391ec6c39012603795b7f11a34c68183
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63185992"
---
# <a name="sqlremovedriver-function"></a>SQLRemoveDriver-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLRemoveDriver** ändert oder Informationen über den Treiber aus dem Eintrag "Odbcinst.ini" in den Systeminformationen entfernt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL SQLRemoveDriver(  
     LPCSTR   lpszDriver,  
     BOOL     fRemoveDSN,  
     LPDWORD  lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszDriver*  
 [Eingabe] Der Name des Treibers, der die Systeminformationen im Schlüssel "Odbcinst.ini" registriert.  
  
 *fRemoveDSN*  
 [Eingabe] Gültige Werte sind:  
  
 "TRUE": Entfernen DSNs im Zusammenhang mit dem Treiber, die im angegebenen *LpszDriver*. "FALSE": Entfernen nicht verknüpft ist, mit dem Treiber, die im angegebenen DSNs *LpszDriver*.  
  
 *lpdwUsageCount*  
 [Ausgabe] Die Verwendungsanzahl des Treibers nach dieser Funktion aufgerufen wurde.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt. Wenn kein Eintrag in den Systeminformationen ist vorhanden, wenn diese Funktion aufgerufen wird, gibt die Funktion "false".  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLRemoveDriver** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Komponente wurde in der Registrierung nicht gefunden.|Der Installer konnte nicht die Treiberinformationen entfernt, da sie in der Registrierung nicht vorhanden noch oder nicht in der Registrierung gefunden werden konnte.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Name für Treiber oder das Konvertierungsprogramm|Die *LpszDriver* Argument war ungültig.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Konnte nicht inkrementiert oder dekrementiert werden die Verwendungsanzahl der Komponente|Fehler des Installationsprogramms, um die Verwendungsanzahl des Treibers zu verringern.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Die *fRemoveDSN* Argument "true", jedoch eine oder mehrere DSNs konnte nicht entfernt werden. Der Aufruf von **SQLConfigDriver** ODBC_REMOVE_DRIVER Anforderung aufgetreten ist.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLRemoveDriver** ergänzt die [SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md) -Funktion und Updates zählen die Verwendung von Komponenten in den Systeminformationen. Diese Funktion sollte nur von einem Setup-Anwendung aufgerufen werden.  
  
 **SQLRemoveDriver** wird der Wert für die Komponente Verwendung um 1 verringert. Wenn die Anzahl der Zugriffe auf 0 zurückgeht, geschieht Folgendes:  
  
1.  Die **SQLConfigDriver** Funktion mit der Option ODBC_REMOVE_DRIVER aufgerufen. Wenn die *fRemoveDSN* Option auf "true" gesetzt ist die **ConfigDSN** Funktionsaufrufe **SQLRemoveDSNFromIni** So entfernen Sie alle Datenquellen in angegebenen Treibers zugeordnet *LpszDriver.* Wenn die *fRemoveDSN* Option auf "false" festgelegt ist, die Datenquellen werden nicht gelöscht werden.  
  
2.  Der Eintrag Driver in den Systeminformationen werden entfernt. Der Eintrag Driver ist in der folgenden Informationen Systemspeicherort, unter dem Treibernamen:  
  
     `HKEY_LOCAL_MACHINE`  
  
     `SOFTWARE`  
  
     `ODBC`  
  
     `Odbcinst.ini`  
  
 **SQLRemoveDriver** Dateien wird nicht tatsächlich entfernt. Das aufrufende Programm ist verantwortlich für das Löschen von Dateien, und verwalten die Verwendungsanzahl der Datei. Nur nachdem, sowohl die Verwendungsanzahl der Komponente als auch die Verwendungsanzahl der Datei erreicht haben 0 (null) eine Datei physisch gelöscht ist. Einige Dateien in einer Komponente können gelöscht werden, und andere nicht gelöscht, je nachdem, ob die Dateien von anderen Anwendungen verwendet werden, die die Anzahl der Dateien Nutzung erhöht haben.  
  
 **SQLRemoveDriver** wird auch als Teil eines Upgradevorgangs bezeichnet. Wenn eine Anwendung erkennt, dass sie ein Upgrade durchführen und den Treiber wurde bereits installierte, sollte der Treiber entfernt und anschließend neu installiert werden. **SQLRemoveDriver** zuerst aufgerufen werden, um verringern die Verwendungsanzahl der Komponente, und klicken Sie dann **SQLInstallDriverEx** aufgerufen werden, um die Verwendungsanzahl der Komponente zu erhöhen. Das Installationsprogramm der Anwendung muss die alten Dateien durch die neuen Dateien ersetzen. Die Verwendungsanzahl der Datei bleibt unverändert, und andere Anwendungen, die die älteren Versionsdateien verwenden jetzt die neuere Version verwenden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen eines Treibers|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md) (in der Setup-DLL)|  
|Hinzufügen, ändern oder Entfernen eines Treibers|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Installieren eines Treibers|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|
