---
title: SQLInstallDriverManager-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallDriverManager
helpviewer_keywords:
- SQLInstallDriverManager function [ODBC]
ms.assetid: aebc439b-fffd-4d98-907a-0163f79aee8d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0788de0493439a360c0446733b31606a02e12422
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302111"
---
# <a name="sqlinstalldrivermanager-function"></a>SQLInstallDriverManager-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0: Veraltet in Windows XP Service Pack 2, Windows Server 2003 Service Pack 1 und neueren Betriebssystemen  
  
 **Zusammenfassung**  
 **SQLInstallDriverManager** gibt den Pfad des Zielverzeichnisses für die Installation der ODBC-Kernkomponenten zurück. Das aufrufende Programm muss die Dateien des Treiber-Managers tatsächlich in das Zielverzeichnis kopieren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLInstallDriverManager(  
     LPSTR    lpszPath,  
     WORD     cbPathMax,  
     WORD *   pcbPathOut);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszPath*  
 [Ausgabe] Pfad des Zielverzeichnisses der Installation.  
  
 *cbPathMax*  
 [Eingabe] Länge von *lpszPath*. Dies muss mindestens _MAX_PATH Bytes sein.  
  
 *pcbPathOut*  
 [Ausgabe] Gesamtanzahl der Bytes (mit Ausnahme des Null-Beendigungsbytes), die in *lpszPath*zurückgegeben werden. Wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *cbPathMax*ist, wird der Pfad in *lpszPath* auf *cbPathMax* abzüglich des Nullbeendigungszeichens abgeschnitten. Das *Argument pcbPathOut* kann ein Nullzeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLInstallDriverManager** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge|Das *Argument lpszPath* war nicht groß genug, um den Ausgabepfad zu enthalten. Der Puffer enthält den abgeschnittenen Pfad.<br /><br /> Das *Argument cbPathMax* war kleiner als _MAX_PATH.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Die Anzahl der Komponentenverwendung konnte nicht erhöht oder dekrementiert werden.|Das Installationsprogramm konnte die Anzahl der ODBC-Kernkomponentennichterhöht erausführen.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLInstallDriverManager** wird aufgerufen, um den Pfad für ODBC-Kernkomponenten zurückzugeben und die Anzahl der Komponentenverwendungen in den Systeminformationen zu erhöhen. Wenn bereits eine Version des Treiber-Managers vorhanden ist, aber die Verwendungsanzahl der Komponenten für den Treiber nicht vorhanden ist, wird der Wert für die Anzahl der neuen Komponentenverwendungaufwerte auf 2 festgelegt.  
  
 Das Anwendungseinrichtungsprogramm ist für das physische Kopieren der Kernkomponentendateien und die Aufrechterhaltung der Dateinutzungsanzahl verantwortlich. Wenn eine Kernkomponentendatei noch nicht installiert wurde, muss das Anwendungsinstallationsprogramm die Datei kopieren und die Dateinutzungsanzahl erstellen. Wenn die Datei zuvor installiert wurde, erhöht das Setupprogramm lediglich die Anzahl der Dateinutzung.  
  
 Wenn zuvor eine ältere Version des Treiber-Managers vom Anwendungsinstallationsprogramm installiert wurde, sollten die Kernkomponenten deinstalliert und dann neu installiert werden, damit die Anzahl der Verwendungszahlen für Kernkomponenten gültig ist. **SQLRemoveDriverManager** sollte zuerst aufgerufen werden, um die Anzahl der Komponentenverwendungen zu reduzieren. **SQLInstallDriverManager** sollte dann aufgerufen werden, um die Anzahl der Komponentenverwendungen zu erhöhen. Das Anwendungseinrichtungsprogramm muss die alten Kernkomponentendateien durch die neuen Dateien ersetzen. Die Anzahl der Dateiverwendungen bleibt unverändert, und andere Anwendungen, die die älteren Versionskernkomponentendateien verwendet haben, verwenden nun die neueren Versionsdateien.  
  
 Bei einer Neuinstallation der ODBC-Kernkomponenten, Treiber und Übersetzer sollte das Anwendungsinstallationsprogramm die folgenden Funktionen nacheinander aufrufen: **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLConfigDriver** (mit einer *fRequest* von ODBC_INSTALL_DRIVER) und dann **SQLInstallTranslatorEx**. Bei einer Deinstallation der Kernkomponenten, Treiber und Übersetzer sollte das Anwendungseinrichtungsprogramm die folgenden Funktionen nacheinander aufrufen: **SQLRemoveTranslator**, **SQLRemoveDriver**und dann **SQLRemoveDriverManager**. Diese Funktionen müssen in dieser Reihenfolge aufgerufen werden. Bei einem Upgrade aller Komponenten sollten alle Deinstallationsfunktionen nacheinander aufgerufen werden und dann alle Installationsfunktionen nacheinander aufgerufen werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, Ändern oder Entfernen eines Treibers|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Installieren eines Treibers|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|  
|Installieren eines Übersetzers|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|  
|Entfernen eines Treibers|[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|  
|Entfernen des Treiber-Managers|[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|  
|Entfernen eines Übersetzers|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
