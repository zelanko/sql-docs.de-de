---
description: SQLInstallDriverEx-Funktion
title: Sqlinstalldriverex-Funktion | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2c200615c9d3bc71ccb146d3b898517611b53eed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421184"
---
# <a name="sqlinstalldriverex-function"></a>SQLInstallDriverEx-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0  
  
 **Zusammenfassung**  
 **Sqlinstalldriverex** fügt dem Odbcinst.ini Eintrag in den Systeminformationen Informationen zum Treiber hinzu und erhöht die *usagecount* des Treibers um 1. Wenn jedoch eine Version des Treibers bereits vorhanden ist, der *usagecount* -Wert für den Treiber jedoch nicht vorhanden ist, wird der neue *usagecount* -Wert auf 2 festgelegt.  
  
 Mit dieser Funktion werden keine Dateien kopiert. Es liegt in der Verantwortung des aufrufenden Programms, die Treiberdateien ordnungsgemäß in das Zielverzeichnis zu kopieren.  
  
 Der Zugriff auf die Funktionalität von **sqlinstalldriverex** kann auch mit [ODBCCONF.EXE](../../../odbc/odbcconf-exe.md)erfolgen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
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
 Der Die Treiber Beschreibung (in der Regel der Name des zugeordneten DBMS), der Benutzern anstelle des Namens des physischen Treibers angezeigt wird. Das *lpszDriver* -Argument muss eine doppelt auf NULL endend beendete Liste von Schlüsselwort-Wert-Paaren enthalten, die den Treiber beschreiben. Weitere Informationen zu Schlüsselwort-Wert-Paaren finden Sie [unter "Treiber Spezifikations Unterschlüssel](../../../odbc/reference/install/driver-specification-subkeys.md)". Weitere Informationen zur doppelt auf NULL endenden Zeichenfolge finden Sie unter [ConfigDSN-Funktion](../../../odbc/reference/syntax/configdsn-function.md).  
  
 *lpszpathin*  
 Der Vollständiger Pfad des Zielverzeichnisses der Installation oder ein NULL-Zeiger. Wenn *lpszpathin* ein NULL-Zeiger ist, werden die Treiber im System Verzeichnis installiert.  
  
 *lpszpathout*  
 Ausgeben Der Pfad des Zielverzeichnisses, in dem der Treiber installiert werden soll. Wenn der Treiber nicht bereits installiert wurde, sollte *lpszpathout* mit *lpszpathin*identisch sein. Wenn der Treiber bereits installiert war, ist *lpszpathout* der Pfad der vorherigen Installation.  
  
 *cbpaarwert*  
 Der Länge von *lpszpathout*.  
  
 *pcbpathout*  
 Ausgeben Die Gesamtanzahl der Bytes (mit Ausnahme des NULL-Beendigungs Zeichens), die für die Rückgabe in *lpszpathout*verfügbar ist. Wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *cbpathoutmax*ist, wird der Ausgabepfad in *lpszpathout* auf *cbpathoutmax* abzüglich des NULL-Beendigungs Zeichens gekürzt. Das *pcbpathout* -Argument kann ein NULL-Zeiger sein.  
  
 *fRequest*  
 Der Der Typ der Anforderung. Das *fRequest* -Argument muss einen der folgenden Werte enthalten:  
  
 ODBC_INSTALL_INQUIRY: Fragen Sie, wo ein Treiber installiert werden kann.  
  
 ODBC_INSTALL_COMPLETE: führen Sie die Installations Anforderung aus.  
  
 *lpdwusagecount*  
 Ausgeben Der Verwendungs Zähler des Treibers, nachdem diese Funktion aufgerufen wurde.  
  
 Anwendungen sollten die Verwendungs Anzahl nicht festlegen. Diese Anzahl wird von ODBC beibehalten.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlinstalldriverex** "false" zurückgibt, kann ein zugeordneter " * \* pferrorcode* "-Wert durch Aufrufen von **sqlinstallererror**abgerufen werden. In der folgenden Tabelle sind die " * \* pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Das *lpszpathout* -Argument war nicht groß genug, um den Ausgabepfad zu enthalten. Der Puffer enthält den abgeschnittene Pfad.<br /><br /> Das *cbpthoutmax* -Argument war 0, und *fRequest* war ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung.|Das *fRequest* -Argument war keiner der folgenden:<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültige Schlüsselwort-Wert-Paare|Das *lpszDriver* -Argument enthielt einen Syntax Fehler.|  
|ODBC_ERROR_INVALID_PATH|Ungültiger Installationspfad.|Das *lpszpathin* -Argument enthielt einen ungültigen Pfad.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber-oder Konvertierungs-Setup Bibliothek konnte nicht geladen werden.|Die Treiber Setup Bibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Ungültige Parameter Sequenz.|Das *lpszDriver* -Argument enthielt keine Liste von Schlüsselwort-Wert-Paaren.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Die Anzahl der Komponenten Verwendung konnte nicht erhöht oder verringert werden.|Der Installer konnte die Verwendungs Anzahl des Treibers nicht erhöhen.|  
  
## <a name="comments"></a>Kommentare  
 Das *lpszDriver* -Argument ist eine Liste von Attributen in Form von Schlüsselwort-Wert-Paaren. Jedes Paar wird mit einem NULL-Byte beendet, und die gesamte Liste wird mit einem NULL-Byte beendet. (Das heißt, zwei NULL-Bytes markieren das Ende der Liste.) Das Format dieser Liste lautet wie folgt:  
  
 _Treiber-Entsc_ **\\** 0driver **=** _-Treiber-DLL-Dateiname_ **\\** 0 [Setup **=** _Setup-DLL-filename_ <b>\\</b> 0]  
  
 [_Driver-attr-Schlüsselwort1_ **=** _value1_ <b>\\</b> 0] [_Driver-attr-Schlüsselwort2_ **=** _value2_ <b>\\</b> 0]... <b>\\</b> 1,0  
  
 Dabei ist "\ 0" ein NULL-Byte, und *Driver-attr-keywordn* ist ein beliebiges Treiber Attribut Schlüsselwort. Die Schlüsselwörter müssen in der angegebenen Reihenfolge angezeigt werden. Nehmen Sie beispielsweise an, dass ein Treiber für formatierte Textdateien separate Treiber-und Setup-DLLs aufweist und Dateien mit den Erweiterungen ". txt" und ". csv" verwenden kann. Das *lpszDriver* -Argument für diesen Treiber könnte wie folgt lauten:  
  
```  
Text\0Driver=TEXT.DLL\0Setup=TXTSETUP.DLL\0FileUsage=1\0  
FileExtns=*.txt,*.csv\0\0  
```  
  
 Angenommen, ein Treiber für SQL Server verfügt nicht über eine separate Setup-DLL, die keine Treiber Attribut Schlüsselwörter enthält. Das *lpszDriver* -Argument für diesen Treiber könnte wie folgt lauten:  
  
```  
SQL Server\0Driver=SQLSRVR.DLL\0\0  
```  
  
 Nachdem **sqlinstalldriverex** Informationen über den Treiber aus dem *lpszDriver* -Argument abgerufen hat, wird die Treiber Beschreibung dem Abschnitt [ODBC Drivers] des Odbcinst.ini Eintrags in den Systeminformationen hinzugefügt. Anschließend wird ein Abschnitt mit dem Titel mit der Beschreibung des Treibers erstellt, und es werden die vollständigen Pfade der Treiber-DLL und der Setup-DLL hinzugefügt. Schließlich wird der Pfad des Zielverzeichnisses der Installation zurückgegeben. die Treiberdateien werden jedoch nicht darauf kopiert. Das aufrufende Programm muss die Treiberdateien tatsächlich in das Zielverzeichnis kopieren.  
  
 **Sqlinstalldriverex** erhöht die Anzahl der Komponenten Verwendungs Einheiten für den installierten Treiber um 1. Wenn eine Version des Treibers bereits vorhanden ist, aber die Anzahl der Komponenten Verwendungs Werte für den Treiber nicht vorhanden ist, wird der Wert der neuen Komponenten Verwendungs Anzahl auf 2 festgelegt.  
  
 Das Setup Programm der Anwendung ist für das physische Kopieren der Treiberdatei und das Beibehalten der Datei Verwendungs Anzahl zuständig. Wenn die Treiberdatei zuvor nicht installiert wurde, muss das Setup Programm der Anwendung die Datei im Pfad *lpszpathin* kopieren und die Anzahl der Datei Verwendungs Daten erstellen. Wenn die Datei bereits installiert wurde, erhöht das Setup Programm lediglich die Anzahl der Datei Auslastung und gibt den Pfad der vorherigen Installation im Argument *lpszpathout* zurück.  
  
> [!NOTE]  
>  Weitere Informationen zur Anzahl von Komponenten Verwendungs-und Datei Verwendungs Zahlen finden Sie unter [Verwendungs Zählung](../../../odbc/reference/install/usage-counting.md).  
  
 Wenn eine ältere Version der Treiberdatei zuvor von der Anwendung installiert wurde, sollte der Treiber deinstalliert und dann neu installiert werden, damit die Verwendungs Anzahl der Treiber Komponenten gültig ist. **Sqlconfigdriver** (mit einer *Häufigkeit* von ODBC_REMOVE_DRIVER) sollte zuerst aufgerufen werden, und anschließend sollte **sqlremovedriver** aufgerufen werden, um die Anzahl der Komponenten Verwendungsraten zu verringern. **Sqlinstalldriverex** sollte dann aufgerufen werden, um den Treiber neu zu installieren und die Anzahl der Komponenten Auslastung zu erhöhen. Das Setup Programm der Anwendung muss die alte Datei durch die neue Datei ersetzen. Die Anzahl der Datei Verwendungs Daten bleibt unverändert, und jede andere Anwendung, die die ältere Versionsdatei verwendet hat, verwendet nun die neuere Version.  
  
> [!NOTE]  
>  Wenn der Treiber bereits installiert wurde und **sqlinstalldriverex** aufgerufen wird, um den Treiber in einem anderen Verzeichnis zu installieren, gibt die Funktion true zurück, aber *lpszpathout* enthält das Verzeichnis, in dem der Treiber bereits installiert war. Das Verzeichnis, das im *lpszDriver* -Argument eingegeben wurde, wird nicht eingeschlossen.  
  
 Die Länge des Pfads in " *lpszpathout* " in " **sqlinstalldriverex** " ermöglicht einen zweistufigen Installationsprozess, sodass eine Anwendung ermitteln kann, was " *cbpathoutmax* " sein sollte, indem Sie " **sqlinstalldriverex** " mit dem ODBC_INSTALL_INQUIRY Modus " *fRequest* " aufrufen. Dadurch wird die Gesamtanzahl der Bytes zurückgegeben, die im *pcbpathout* -Puffer verfügbar sind. **Sqlinstalldriverex** kann dann mit einem *fRequest* von ODBC_INSTALL_COMPLETE aufgerufen werden, und das *cbpathoutmax* -Argument ist auf den Wert im *pcbpathout* -Puffer sowie auf das NULL-Beendigungs Zeichen festgelegt.  
  
 Wenn Sie sich dafür entscheiden, das zweistufige Modell für **sqlinstalldriverex**nicht zu verwenden, müssen Sie die Größe des Speichers für den Pfad des Zielverzeichnisses auf den Wert *_MAX_PATH festlegen,* wie in STDLIB. h definiert, um das Abschneiden zu verhindern.  
  
 Wenn *fRequest* ODBC_INSTALL_COMPLETE ist, lässt **sqlinstalldriverex** nicht zu, dass *lpszpathout* NULL ist (oder *cbpathoutmax* muss 0 sein). Wenn *fRequest* ODBC_INSTALL_COMPLETE ist, wird false zurückgegeben, wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *cbpaarwert*ist, wobei das Ergebnis der Kürzung auftritt.  
  
 Nachdem **sqlinstalldriverex** aufgerufen wurde und das Anwendungs Setup Programm die Treiberdatei (falls erforderlich) kopiert hat, muss die Treiber-Setup-DLL **sqlconfigdriver** aufrufen, um die Konfiguration für den Treiber festzulegen.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Installieren des Treiber-Managers|[Sqlinstalldrivermanager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
