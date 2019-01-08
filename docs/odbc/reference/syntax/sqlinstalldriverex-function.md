---
title: SQLInstallDriverEx-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallDriverEx
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallDriverEx
helpviewer_keywords:
- SQLInstallDriverEx function [ODBC]
ms.assetid: 1dd74544-f4e9-46e1-9b5f-c11d84fdab4c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0ec40b97f8953f114081292ac82069fd4a81692a
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53208635"
---
# <a name="sqlinstalldriverex-function"></a>SQLInstallDriverEx-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLInstallDriverEx** Fügt Informationen über den Treiber auf den Eintrag "Odbcinst.ini" in den Systeminformationen und erhöht die Fahrers *UsageCount* um 1. Jedoch, wenn eine Version der Treiber ist bereits vorhanden, aber die *UsageCount* Wert für der Treiber nicht vorhanden ist, die neue *UsageCount* Wert auf 2 festgelegt ist.  
  
 Diese Funktion ist nicht tatsächlich alle Dateien kopiert werden. Es ist die Verantwortung für das aufrufende Programm des Treibers Dateien ordnungsgemäß in das Zielverzeichnis kopiert.  
  
 Die Funktionalität von **SQLInstallDriverEx** kann auch mit zugegriffen werden [ODBCCONF. EXE-Datei](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL SQLInstallDriverEx(  
     LPCSTR    lpszDriver,  
     LPCSTR    lpszPathIn,  
     LPSTR     lpszPathOut,  
     WORD      cbPathOutMax,  
     WORD *    pcbPathOut,  
     WORD      fRequest,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszDriver*  
 [Eingabe] Um die treiberbeschreibung (in der Regel der Name des zugeordneten DBMS) für Benutzer anstelle des Namens des physischen Treiber angezeigt werden. Die *LpszDriver* Argument muss eine doppelt Null-terminierte-Liste der Schlüsselwort-Wert-Paaren, die Beschreibung des Treibers enthalten. Weitere Informationen zum Schlüsselwort-Wert-Paare, finden Sie unter [Treiberspezifikationen](../../../odbc/reference/install/driver-specification-subkeys.md). Weitere Informationen, die doppelt Null-terminierte Zeichenfolge, finden Sie unter [ConfigDSN-Funktion](../../../odbc/reference/syntax/configdsn-function.md).  
  
 *lpszPathIn*  
 [Eingabe] Vollständiger Pfad des Zielverzeichnisses der Installation oder ein null-Zeiger. Wenn *LpszPathIn* ist ein null-Zeiger im Systemverzeichnis der Treiber installiert werden.  
  
 *lpszPathOut*  
 [Ausgabe] Pfad der das Zielverzeichnis, in dem der Treiber installiert werden soll. Wenn der Treiber noch nicht installiert wurde, *LpszPathOut* sollten identisch sein *LpszPathIn*. Wenn der Treiber bereits installiert wurde, *LpszPathOut* ist der Pfad der vorherigen Installation.  
  
 *cbPathOutMax*  
 [Eingabe] Länge der *LpszPathOut*.  
  
 *pcbPathOut*  
 [Ausgabe] Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen) zur Verfügung, die in zurückgegeben *LpszPathOut*. Wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *CbPathOutMax*, den Ausgabepfad in *LpszPathOut* wird abgeschnitten, um *CbPathOutMax* minus der NULL-Terminierungszeichen. Die *PcbPathOut* Argument kann ein null-Zeiger sein.  
  
 *Häufigsten*  
 [Eingabe] Typ der Anforderung. Die *häufigsten* Argument muss einen der folgenden Werte enthalten:  
  
 ODBC_INSTALL_INQUIRY: Erkundigen Sie sich, ein Treiber installiert werden können.  
  
 ODBC_INSTALL_COMPLETE: Die Installationsanforderung zu beenden.  
  
 *lpdwUsageCount*  
 [Ausgabe] Die Verwendungsanzahl des Treibers nach dieser Funktion aufgerufen wurde.  
  
 Anwendungen sollten nicht die Verwendungsanzahl der festlegen. ODBC wird dieser Zähler zu verwalten.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLInstallDriverEx** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Die *LpszPathOut* Argument war nicht groß genug, um den Ausgabepfad enthalten. Der Puffer enthält den Pfad abgeschnitten.<br /><br /> Die *CbPathOutMax* Argument wurde 0 (null) und *häufigsten* ODBC_INSTALL_COMPLETE wurde.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung|Die *häufigsten* Argument war keiner der folgenden:<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültiges Schlüsselwort-Wert-Paaren|Die *LpszDriver* Argument enthalten einen Syntaxfehler.|  
|ODBC_ERROR_INVALID_PATH|Ungültiger-Installationspfad|Die *LpszPathIn* Argument enthalten einen ungültigen Pfad.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber oder Translator-Setup-Bibliothek konnte nicht geladen werden.|Der Setup-Treiberbibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Ungültiger Parameter-Sequenz|Die *LpszDriver* Argument keine Liste der Schlüsselwort-Wert-Paare enthalten.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Konnte nicht inkrementiert oder dekrementiert werden die Verwendungsanzahl der Komponente|Installerfehler beim Verwendungsanzahl des Treibers zu erhöhen.|  
  
## <a name="comments"></a>Kommentare  
 Die *LpszDriver* Argument ist eine Liste von Attributen in Form von Schlüsselwort-Wert-Paaren. Jedes Paar wird mit null Byte beendet, und die gesamte Liste wird mit null Byte beendet. (D. h., markieren Sie zwei null-Bytes am Ende der Liste.) Das Format dieser Liste ist wie folgt aus:  
  
 _Treiber-Desc_ **\\**0Driver**=**_-Treiber-DLL-Dateiname_ **\\**0 [Setup**=**_-Setup-DLL-Dateiname_<b>\\</b>0]  
  
 [_-Treiber-Attr-Schlüsselwort1_**=**_value1_<b>\\</b>0] [_-Treiber-Attr-Schlüsselwort2_  **=** _value2_<b>\\</b>0]... <b> \\ </b>0  
  
 \0 ist, in dem ein null-Byte und *-Treiber-Attr-Keywordn* wird jedem Attribut-Driver-Schlüsselwort. Die Schlüsselwörter müssen in der angegebenen Reihenfolge angezeigt werden. Beispielsweise nehmen wir an, dass ein Treiber für formatierten Text-Dateien separate Treiber und -Setup-DLLs verfügt, und mit den Erweiterungen ".txt" und CSV verwenden Sie-Dateien. Die *LpszDriver* Argument für diesen Treiber möglicherweise wie folgt:  
  
```  
Text\0Driver=TEXT.DLL\0Setup=TXTSETUP.DLL\0FileUsage=1\0  
FileExtns=*.txt,*.csv\0\0  
```  
  
 Nehmen wir an, dass ein Treiber für SQL Server verfügt nicht über eine separate Setup-DLL und verfügt nicht über keine Schlüsselwörter der Treiber-Attribut. Die *LpszDriver* Argument für diesen Treiber möglicherweise wie folgt:  
  
```  
SQL Server\0Driver=SQLSRVR.DLL\0\0  
```  
  
 Nach dem **SQLInstallDriverEx** Ruft Informationen über den Treiber aus den *LpszDriver* -Argument, um die treiberbeschreibung Abschnitt [ODBC Drivers] des Eintrags "Odbcinst.ini" im System hinzugefügt Informationen. Anschließend erstellt einen Abschnitt mit der Treiber die Beschreibung und fügt die vollständigen Pfade der Treiber-DLL und die Setup-DLL hinzu. Schließlich gibt den Pfad des Zielverzeichnisses der Installation zurück, doch Treiberdateien abzurufen, werden nicht kopiert wird. Das aufrufende Programm muss die Treiberdateien tatsächlich in das Zielverzeichnis kopieren.  
  
 **SQLInstallDriverEx** die Verwendungsanzahl der Komponente für die installierte Treiber wird um 1 erhöht. Wenn eine Version des Treibers ist bereits vorhanden, aber die Verwendungsanzahl der Komponente für den Treiber ist nicht vorhanden, wird der neue Komponente Nutzung Count-Wert auf 2 festgelegt.  
  
 Das Setupprogramm für die Anwendung ist für physisch kopieren die Treiberdatei, und verwalten die Anzahl der Dateien Verwendung verantwortlich. Die Treiberdatei noch nicht installiert wurde, muss die Installationsprogramm der Anwendung kopieren der Datei in die *LpszPathIn* Pfad und den Verwendungszähler für die Datei zu erstellen. Wenn die Datei zuvor installiert wurde, das Setup-Programm lediglich erhöht die Verwendungsanzahl der Datei und gibt den Pfad der vorherigen Installation in der *LpszPathOut* Argument.  
  
> [!NOTE]  
>  Weitere Informationen zu Verwendungszähler für die Komponente und Verwendungszähler für die Datei, finden Sie unter [zählen der Verwendung](../../../odbc/reference/install/usage-counting.md).  
  
 Wenn eine ältere Version der Treiberdatei zuvor von der Anwendung installiert wurde, sollte der Treiber deinstalliert und anschließend erneut installieren, so dass der Verwendungszähler für Treiber Komponente gültig ist. **SQLConfigDriver** (mit einem *häufigsten* von ODBC_REMOVE_DRIVER) zuerst aufgerufen werden soll, und klicken Sie dann **SQLRemoveDriver** aufgerufen werden soll, um die Verwendungsanzahl der Komponente zu verringern. **SQLInstallDriverEx** dann aufgerufen werden, um den Treiber, erhöhen die Verwendungsanzahl der Komponente zu installieren. Das Installationsprogramm der Anwendung muss die alte Datei mit der neuen Datei ersetzen. Die Verwendungsanzahl der Datei bleibt unverändert, und Verwenden einer anderen Anwendung, die Datei mit der älteren Version verwendet nun die neuere Version.  
  
> [!NOTE]  
>  Wenn der Treiber zuvor installiert war und **SQLInstallDriverEx** wird aufgerufen, um den Treiber in einem anderen Verzeichnis zu installieren, die Funktion gibt "true", aber *LpszPathOut* enthält das Verzeichnis in dem der Treiber bereits installiert wurde. Es umfasst nicht das Verzeichnis, die in eingegebenen der *LpszDriver* Argument.  
  
 Die Länge des Pfads in *LpszPathOut* in **SQLInstallDriverEx** ermöglicht ein Prozess mit zwei-Phasen installieren, damit eine Anwendung, was bestimmen kann *CbPathOutMax* sollte sein. Aufrufen von **SQLInstallDriverEx** mit einer *häufigsten* ODBC_INSTALL_INQUIRY-Modus. Dies gibt die Gesamtzahl der Bytes, die zur Verfügung, in der *PcbPathOut* Puffer. **SQLInstallDriverEx** kann dann aufgerufen werden, mit einer *häufigsten* von ODBC_INSTALL_COMPLETE und *CbPathOutMax* Argument festgelegt wird, auf den Wert in der *PcbPathOut*Puffer sowie das Zeichen Null-Terminierung vorliegt.  
  
 Wenn Sie nicht verwenden, das Zweiphasen-Modell für **SQLInstallDriverEx**, müssen Sie festlegen, *CbPathOutMax*, die definiert die Größe des Speichers für den Pfad des Zielverzeichnisses, um die _MAX_PATH Wert definiert in Stdlib.h, um das Abschneiden zu verhindern.  
  
 Wenn *häufigsten* ist ODBC_INSTALL_COMPLETE, **SQLInstallDriverEx** lässt keine *LpszPathOut* gleich NULL sein (oder *CbPathOutMax* sein (0). Wenn *häufigsten* ODBC_INSTALL_COMPLETE ist, "false" wird zurückgegeben, wenn die Anzahl der Bytes, die für die Rückgabe verfügbar ist, größer als oder gleich *CbPathOutMax*, mit dem Ergebnis, um ein Abschneiden auftritt.  
  
 Nach dem **SQLInstallDriverEx** aufgerufen wurde und die Anwendungsinstallation wurde die Treiberdatei kopiert, (falls erforderlich), der Setup-Treiber, die DLL aufrufen muss **SQLConfigDriver** , legen Sie die Konfiguration für die Treiber.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Installieren des Treiber-Managers|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
