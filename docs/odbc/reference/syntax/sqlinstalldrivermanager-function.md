---
title: Sqlinstalldrivermanager-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: 1f1e3ac7f0a76c607fa07d6eb92d069d99ef5e0a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076210"
---
# <a name="sqlinstalldrivermanager-function"></a>SQLInstallDriverManager-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0: veraltet in Windows XP Service Pack 2, Windows Server 2003 Service Pack 1 und höheren Betriebssystemen  
  
 **Zusammenfassung**  
 **Sqlinstalldrivermanager** gibt den Pfad des Zielverzeichnisses für die Installation der ODBC-Kernkomponenten zurück. Das aufrufende Programm muss die Dateien des Treiber-Managers tatsächlich in das Zielverzeichnis kopieren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLInstallDriverManager(  
     LPSTR    lpszPath,  
     WORD     cbPathMax,  
     WORD *   pcbPathOut);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszpath*  
 Ausgeben Der Pfad des Zielverzeichnisses der Installation.  
  
 *cbpathmax*  
 Der Länge von *lpszpath*. Dies muss mindestens _MAX_PATH Byte betragen.  
  
 *pcbpathout*  
 Ausgeben Die Gesamtanzahl der Bytes (mit Ausnahme des NULL-Beendigungs Byte), die in *lpszpath*zurückgegeben wurde. Wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *cbpathmax*ist, wird der Pfad in *lpszpath* auf *cbpathmax* abzüglich des NULL-Beendigungs Zeichens gekürzt. Das *pcbpathout* -Argument kann ein NULL-Zeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlinstalldrivermanager** false zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von " **sqlinstallererror**" abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Das *lpszpath* -Argument war nicht groß genug, um den Ausgabepfad zu enthalten. Der Puffer enthält den abgeschnittene Pfad.<br /><br /> Das *cbpathmax* -Argument war kleiner als _MAX_PATH.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Die Anzahl der Komponenten Verwendung konnte nicht erhöht oder verringert werden.|Der Installer konnte die Verwendungs Anzahl der ODBC-Kernkomponenten nicht erhöhen.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **Sqlinstalldrivermanager** wird aufgerufen, um den Pfad für ODBC-Kernkomponenten zurückzugeben und die Anzahl der Komponenten Verwendung in den Systeminformationen zu erhöhen. Wenn bereits eine Version des Treiber-Managers vorhanden ist, die Anzahl der Komponenten Verwendungs Werte für den Treiber jedoch nicht vorhanden ist, wird der Wert der neuen Komponenten Verwendungs Anzahl auf 2 festgelegt.  
  
 Das Anwendungs Setup Programm ist dafür verantwortlich, die Kernkomponenten Dateien physisch zu kopieren und die Anzahl der Datei Verwendungs Daten beizubehalten. Wenn eine Core-Komponenten Datei noch nicht installiert wurde, muss das Setup Programm der Anwendung die Datei kopieren und die Anzahl der Datei Verwendungs Daten erstellen. Wenn die Datei bereits installiert wurde, erhöht das Setup Programm lediglich die Anzahl der Datei Verwendungs Daten.  
  
 Wenn eine ältere Version des Treiber-Managers zuvor durch das Setup Programm der Anwendung installiert wurde, sollten die Kernkomponenten deinstalliert und dann neu installiert werden, damit die Anzahl der Kernkomponenten Verwendungs Werte gültig ist. **Sqlremovedrivermanager** muss zuerst aufgerufen werden, um die Anzahl von Komponenten Verwendungsraten zu verringern. **Sqlinstalldrivermanager** sollte dann aufgerufen werden, um die Anzahl von Komponenten Verwendungsraten zu erhöhen. Das Setup Programm der Anwendung muss die alten Kernkomponenten Dateien durch die neuen Dateien ersetzen. Die Anzahl von Datei Verwendungs Anzahlen bleibt unverändert, und andere Anwendungen, die die älteren Versions Kernkomponenten Dateien verwendeten, verwenden nun die neueren Versions Dateien.  
  
 Bei einer Neuinstallation der ODBC-Kernkomponenten, Treiber und Konvertierer sollte das Setup Programm der Anwendung die folgenden Funktionen nacheinander aufrufen: **sqlinstalldrivermanager**, **sqlinstalldriverex**, **sqlconfigdriver** (mit einer *Frequenz* von ODBC_INSTALL_DRIVER) und dann **sqlinstalltranslatorex**. Bei einer Deinstallation der Kernkomponenten, Treiber und Konvertierer sollte das Anwendungs Setup Programm die folgenden Funktionen in der folgenden Reihenfolge abrufen: **sqlremovetranslator**, **sqlremovedriver**und dann **sqlremovedrivermanager**. Diese Funktionen müssen in dieser Sequenz aufgerufen werden. Bei einem Upgrade aller Komponenten sollten alle Deinstallations Funktionen nacheinander aufgerufen werden. Anschließend sollten alle Installationsfunktionen nacheinander aufgerufen werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen eines Treibers|[Sqlconfigdriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Installieren eines Treibers|[Sqlinstalldriverex](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|  
|Installieren eines Konvertierers|[Sqlinstalltranslatorex](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|  
|Entfernen eines Treibers|[Sqlremovedriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|  
|Entfernen des Treiber-Managers|[Sqlremovedrivermanager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|  
|Entfernen eines Konvertierers|[Sqlremovetranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
