---
title: SQLInstallDriverManager-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17a1539463e56e2795d03fa401b17b7e7d173440
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65536513"
---
# <a name="sqlinstalldrivermanager-function"></a>SQLInstallDriverManager-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 1.0: Veraltetes Feature in Windows XP Service Pack 2, Windows Server 2003 Service Pack 1 und höher  
  
 **Zusammenfassung**  
 **SQLInstallDriverManager** gibt den Pfad des das Zielverzeichnis für die Installation der ODBC-Kernkomponenten. Das aufrufende Programm muss der Treiber-Manager-Dateien tatsächlich in das Zielverzeichnis kopieren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLInstallDriverManager(  
     LPSTR    lpszPath,  
     WORD     cbPathMax,  
     WORD *   pcbPathOut);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszPath*  
 [Ausgabe] Der Pfad des Verzeichnisses Ziel der Installation.  
  
 *cbPathMax*  
 [Eingabe] Länge der *LpszPath*. Dies muss mindestens _MAX_PATH Bytes.  
  
 *pcbPathOut*  
 [Ausgabe] Gesamte Anzahl der Bytes, die (mit Ausnahme der Null-Terminierung Byte) in zurückgegebenen *LpszPath*. Wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *CbPathMax*, den Pfad im *LpszPath* auf abgeschnitten *CbPathMax* minus Null-Terminierung vorliegt Zeichen. Die *PcbPathOut* Argument kann ein null-Zeiger sein.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLInstallDriverManager** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Die *LpszPath* Argument war nicht groß genug, um den Ausgabepfad enthalten. Der Puffer enthält den Pfad abgeschnitten.<br /><br /> Die *CbPathMax* Argument war kleiner als _MAX_PATH.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Konnte nicht inkrementiert oder dekrementiert werden die Verwendungsanzahl der Komponente|Der Installer konnte nicht die Verwendungsanzahl der ODBC-Core-Komponente zu erhöhen.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLInstallDriverManager** wird aufgerufen, um den Pfad zurückgegeben, für die ODBC-Kernkomponenten und erhöhen Sie die Verwendung von Komponenten in den Systeminformationen zählen. Wenn bereits eine Version des Treiber-Managers vorhanden ist, aber die Verwendungsanzahl der Komponente für den Treiber ist nicht vorhanden, wird der neue Komponente Nutzung Count-Wert auf 2 festgelegt.  
  
 Das Setupprogramm für die Anwendung ist verantwortlich für das physisch kopieren die Dateien der Core-Komponenten, und zählt, verwalten die Verwendung der Datei. Wenn Sie eine Komponentendatei Core noch nicht installiert wurde, muss das Installationsprogramm der Anwendung kopieren Sie die Datei, und erstellen die Verwendungsanzahl der Datei. Wenn die Datei zuvor installiert wurde, inkrementiert das Setup-Programm lediglich die Verwendungsanzahl der Datei.  
  
 Wenn eine ältere Version des Treiber-Managers durch das Installationsprogramm der Anwendung bereits installiert wurde, die Kernkomponenten deinstalliert und anschließend erneut installieren, damit an, dass der Verwendungszähler für Core Komponente gültig ist. **SQLRemoveDriverManager** zuerst aufgerufen werden, um die Verwendungsanzahl der Komponente zu verringern. **SQLInstallDriverManager** dann aufgerufen werden, um die Verwendungsanzahl der Komponente zu erhöhen. Das Installationsprogramm der Anwendung muss die alten Kerndateien Komponente durch die neuen Dateien ersetzen. Die Datei Verwendungszähler bleiben unverändert, und Verwenden anderer Anwendungen, die die ältere Version Komponente Kerndateien verwendet nun die Dateien für die neuere Version.  
  
 In einer Neuinstallation der ODBC-Kernkomponenten, Treiber und Übersetzer sollte das Setupprogramm für die Anwendung die folgenden Funktionen in der Sequenz aufrufen: **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLConfigDriver** (mit einem *häufigsten* von ODBC_INSTALL_DRIVER), und klicken Sie dann  **SQLInstallTranslatorEx**. In der Core-Komponenten, Treiber und Übersetzer zu deinstallieren sollte das Setupprogramm für die Anwendung die folgenden Funktionen in der Sequenz aufrufen: **SQLRemoveTranslator**, **SQLRemoveDriver**, und klicken Sie dann **SQLRemoveDriverManager**. Diese Funktionen müssen in dieser Reihenfolge aufgerufen werden. Ein Upgrade aller Komponenten alle Funktionen für die Deinstallation nacheinander aufgerufen werden soll, und klicken Sie dann alle Funktionen für die Installation nacheinander aufgerufen werden soll.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen eines Treibers|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Installieren eines Treibers|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|  
|Installieren einen Übersetzer|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|  
|Entfernen eines Treibers|[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|  
|Entfernen den Treiber-Manager|[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|  
|Entfernen einen Übersetzer|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
