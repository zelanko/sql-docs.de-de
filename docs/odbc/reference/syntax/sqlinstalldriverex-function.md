---
title: SQLInstallDriverEx-Funktion | Microsoft Docs
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
ms.openlocfilehash: 054e8b6b9eae26bd5f973f3d46d7ef37363a8e79
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302122"
---
# <a name="sqlinstalldriverex-function"></a>SQLInstallDriverEx-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLInstallDriverEx** fügt dem Eintrag Odbcinst.ini Informationen über den Treiber in den Systeminformationen hinzu und erhöht die *UsageCount* des Treibers um 1. Wenn jedoch bereits eine Version des Treibers vorhanden ist, aber der *UsageCount-Wert* für den Treiber nicht vorhanden ist, wird der neue *UsageCount-Wert* auf 2 festgelegt.  
  
 Diese Funktion kopiert eigentlich keine Dateien. Es liegt in der Verantwortung des aufrufenden Programms, die Dateien des Treibers ordnungsgemäß in das Zielverzeichnis zu kopieren.  
  
 Auf die Funktionalität von **SQLInstallDriverEx** kann auch mit [ODBCCONF zugegriffen werden. EXE](../../../odbc/odbcconf-exe.md).  
  
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
 [Eingabe] Die Treiberbeschreibung (in der Regel der Name des zugehörigen DBMS), die den Benutzern anstelle des physischen Treibernamens angezeigt wird. Das *argument lpszDriver* muss eine doppelt null-terminierte Liste von Schlüsselwort-Wert-Paaren enthalten, die den Treiber beschreiben. Weitere Informationen zu Keyword-Wert-Paaren finden Sie unter [Driver Specification Subkeys](../../../odbc/reference/install/driver-specification-subkeys.md). Weitere Informationen zur doppelt null-terminierten Zeichenfolge finden Sie unter [ConfigDSN-Funktion](../../../odbc/reference/syntax/configdsn-function.md).  
  
 *lpszPathIn*  
 [Eingabe] Vollständiger Pfad des Zielverzeichnisses der Installation oder eines Nullzeigers. Wenn *lpszPathIn* ein Nullzeiger ist, werden die Treiber im Systemverzeichnis installiert.  
  
 *lpszPathOut*  
 [Ausgabe] Pfad des Zielverzeichnisses, in dem der Treiber installiert werden soll. Wenn der Treiber noch nicht installiert wurde, sollte *lpszPathOut* mit *lpszPathIn*identisch sein. Wenn der Treiber zuvor installiert wurde, ist *lpszPathOut* der Pfad der vorherigen Installation.  
  
 *cbPathOutMax*  
 [Eingabe] Länge von *lpszPathOut*.  
  
 *pcbPathOut*  
 [Ausgabe] Gesamtanzahl der Bytes (mit Ausnahme des Null-Beendigungszeichens), die in *lpszPathOut*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *cbPathOutMax*ist, wird der Ausgabepfad in *lpszPathOut* auf *cbPathOutMax* abzüglich des Nullbeendigungszeichens abgeschnitten. Das *Argument pcbPathOut* kann ein Nullzeiger sein.  
  
 *fRequest*  
 [Eingabe] Art der Anforderung. Das *fRequest-Argument* muss einen der folgenden Werte enthalten:  
  
 ODBC_INSTALL_INQUIRY: Erkundigen Sie sich, wo ein Treiber installiert werden kann.  
  
 ODBC_INSTALL_COMPLETE: Schließen Sie die Installationsanforderung ab.  
  
 *lpdwUsageCount*  
 [Ausgabe] Die Verwendungsanzahl des Treibers, nachdem diese Funktion aufgerufen wurde.  
  
 Anwendungen sollten die Verwendungsanzahl nicht festlegen. ODBC behält diese Anzahl bei.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLInstallDriverEx** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge|Das Argument *lpszPathOut* war nicht groß genug, um den Ausgabepfad zu enthalten. Der Puffer enthält den abgeschnittenen Pfad.<br /><br /> Das Argument *cbPathOutMax* war 0, und *fRequest* wurde ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Anforderungstyp|Das *fRequest-Argument* war nicht eines der folgenden:<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültige Schlüsselwort-Wert-Paare|Das *Argument lpszDriver* enthielt einen Syntaxfehler.|  
|ODBC_ERROR_INVALID_PATH|Ungültiger Installationspfad|Das Argument *lpszPathIn* enthielt einen ungültigen Pfad.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber- oder Übersetzereinrichtungsbibliothek konnte nicht geladen werden.|Die Treibereinrichtungsbibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Ungültige Parametersequenz|Das *Argument lpszDriver* enthielt keine Liste von Schlüsselwort-Wert-Paaren.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Die Anzahl der Komponentenverwendung konnte nicht erhöht oder dekrementiert werden.|Das Installationsprogramm konnte die Verwendungsanzahl des Treibers nicht erhöhen.|  
  
## <a name="comments"></a>Kommentare  
 Das *Argument lpszDriver* ist eine Liste von Attributen in Form von Schlüsselwort-Wert-Paaren. Jedes Paar wird mit einem NULL-Byte beendet, und die gesamte Liste wird mit einem NULL-Byte beendet. (Das heißt, zwei Nullbytes markieren das Ende der Liste.) Das Format dieser Liste ist wie folgt:  
  
 _driver-desc_ **\\**0Driver**=**_driver-DLL-filename_**\\****=** 0[Setup_Setup-DLL-filename_<b>\\</b>0]  
  
 [_driver-attr-keyword1_**=**_wert1_<b>\\</b>0] [_driver-attr-keyword2_**=**_wert2_<b>\\</b>0]... <b>\\</b>0  
  
 wobei ''0'0'' ein NULL-Byte ist und *driver-attr-keywordn* ein beliebiges Schlüsselwort für treiberattribut ist. Die Schlüsselwörter müssen in der angegebenen Reihenfolge angezeigt werden. Angenommen, ein Treiber für formatierte Textdateien verfügt über separate Treiber- und Setup-DLLs und kann Dateien mit den Erweiterungen .txt und .csv verwenden. Das *argument lpszDriver* für diesen Treiber könnte wie folgt lauten:  
  
```  
Text\0Driver=TEXT.DLL\0Setup=TXTSETUP.DLL\0FileUsage=1\0  
FileExtns=*.txt,*.csv\0\0  
```  
  
 Angenommen, ein Treiber für SQL Server verfügt nicht über eine separate Setup-DLL und keine Schlüsselwörter für Treiberattribute. Das *argument lpszDriver* für diesen Treiber könnte wie folgt lauten:  
  
```  
SQL Server\0Driver=SQLSRVR.DLL\0\0  
```  
  
 Nachdem **SQLInstallDriverEx** Informationen über den Treiber aus dem *Argument lpszDriver* abgerufen hat, fügt es die Treiberbeschreibung zum Abschnitt [ODBC Drivers] des Eintrags Odbcinst.ini in den Systeminformationen hinzu. Anschließend wird ein Abschnitt mit der Beschreibung des Treibers erstellt und die vollständigen Pfade der Treiber-DLL und der Setup-DLL hinzugefügt. Schließlich gibt er den Pfad des Zielverzeichnisses der Installation zurück, kopiert jedoch nicht die Treiberdateien. Das aufrufende Programm muss die Treiberdateien tatsächlich in das Zielverzeichnis kopieren.  
  
 **SQLInstallDriverEx** erhöht die Anzahl der Komponentenverwendungen für den installierten Treiber um 1. Wenn bereits eine Version des Treibers vorhanden ist, aber die Komponentennutzungsanzahl für den Treiber nicht vorhanden ist, wird der Wert für die Anzahl der neuen Komponentenverwendungaufwerte auf 2 festgelegt.  
  
 Das Anwendungseinrichtungsprogramm ist für das physische Kopieren der Treiberdatei und die Aufrechterhaltung der Dateinutzungsanzahl verantwortlich. Wenn die Treiberdatei noch nicht installiert wurde, muss das Anwendungsinstallationsprogramm die Datei im *Pfad lpszPathIn* kopieren und die Dateinutzungsanzahl erstellen. Wenn die Datei zuvor installiert wurde, erhöht das Setupprogramm lediglich die Dateinutzungsanzahl und gibt den Pfad der vorherigen Installation im Argument *lpszPathOut* zurück.  
  
> [!NOTE]  
>  Weitere Informationen zu der Anzahl der Komponentenverwendungen und der Dateiverwendung finden Sie unter [Verwendungszählung](../../../odbc/reference/install/usage-counting.md).  
  
 Wenn zuvor eine ältere Version der Treiberdatei von der Anwendung installiert wurde, sollte der Treiber deinstalliert und dann neu installiert werden, damit die Verwendungsanzahl der Treiberkomponenten gültig ist. **SQLConfigDriver** (mit einer *fRequest* von ODBC_REMOVE_DRIVER) sollte zuerst aufgerufen werden, und dann sollte **SQLRemoveDriver** aufgerufen werden, um die Anzahl der Komponentenverwendungen zu reduzieren. **SQLInstallDriverEx** sollte dann aufgerufen werden, um den Treiber neu zu installieren, wodurch die Anzahl der Komponentenverwendungen erhöht wird. Das Anwendungseinrichtungsprogramm muss die alte Datei durch die neue Datei ersetzen. Die Anzahl der Dateiverwendungen bleibt unverändert, und jede andere Anwendung, die die ältere Versionsdatei verwendet hat, verwendet nun die neuere Version.  
  
> [!NOTE]  
>  Wenn der Treiber zuvor installiert wurde und **SQLInstallDriverEx** aufgerufen wird, den Treiber in einem anderen Verzeichnis zu installieren, gibt die Funktion TRUE zurück, aber *lpszPathOut* enthält das Verzeichnis, in dem der Treiber bereits installiert war. Das verzeichnis, das im *Argument lpszDriver* eingegeben wurde, wird nicht enthalten.  
  
 Die Länge des Pfads in *lpszPathOut* in **SQLInstallDriverEx** ermöglicht einen zweiphasigen Installationsprozess, sodass eine Anwendung bestimmen kann, was *cbPathOutMax* sein sollte, indem **sie SQLInstallDriverEx** mit einer *fRequest* ODBC_INSTALL_INQUIRY-Modus aufruft. Dadurch wird die Gesamtzahl der im *pcbPathOut-Puffer* verfügbaren Bytes zurückgegeben. **SQLInstallDriverEx** kann dann mit einer *fRequest* von ODBC_INSTALL_COMPLETE aufgerufen werden und das *argument cbPathOutMax* auf den Wert im *pcbPathOut-Puffer* sowie das Null-Beendigungszeichen festgelegt.  
  
 Wenn Sie das Zweiphasenmodell für **SQLInstallDriverEx**nicht verwenden möchten, müssen Sie *cbPathOutMax*festlegen, der die Größe des Speichers für den Pfad des Zielverzeichnisses definiert, auf den Wert _MAX_PATH, wie in Stdlib.h definiert, um Abschneiden zu verhindern.  
  
 Wenn *fRequest* ODBC_INSTALL_COMPLETE ist, lässt **SQLInstallDriverEx** nicht zu, dass *lpszPathOut* NULL (oder *cbPathOutMax* 0) ist. Wenn *fRequest* ODBC_INSTALL_COMPLETE ist, wird FALSE zurückgegeben, wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *cbPathOutMax*ist, mit dem Ergebnis, dass die Abschneide erfolgt.  
  
 Nachdem **SQLInstallDriverEx** aufgerufen wurde und das Anwendungsinstallationsprogramm die Treiberdatei kopiert hat (falls erforderlich), muss die Treibereinrichtungs-DLL **SQLConfigDriver** aufrufen, um die Konfiguration für den Treiber festzulegen.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Installieren des Treiber-Managers|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
