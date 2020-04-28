---
title: Sqlinstalltranslatorex-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallTranslatorEx
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslatorEx
helpviewer_keywords:
- SQLInstallTranslatorEx function [ODBC]
ms.assetid: a0630602-53c1-4db0-98ce-70d160aedf8d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5cf52c26bf9e4a26f13a27a0e763fbaa30bd18ec
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302091"
---
# <a name="sqlinstalltranslatorex-function"></a>SQLInstallTranslatorEx-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0  
  
 **Zusammenfassung**  
 **Sqlinstalltranslatorex** fügt dem Abschnitt "Odbcinst. ini" in den Systeminformationen (HKEY_LOCAL_MACHINE \software\odbc\odbcinst. INI\ODBC-Konvertierungs Registrierungsschlüssel).  
  
 Auf die Funktionalität von **sqlinstalltranslatorex** kann auch mit [odbcconf zugegriffen werden. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLInstallTranslatorEx(  
     LPCSTR    lpszTranslator,  
     LPCSTR    lpszPathIn,  
     LPSTR     lpszPathOut,  
     WORD      cbPathOutMax,  
     WORD *    pcbPathOut,  
     WORD      fRequest,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpsztranslator*  
 Der Diese muss eine doppelt auf NULL endend beendete Liste von Schlüsselwort-Wert-Paaren enthalten, die den Konvertierer beschreiben. Weitere Informationen zur Schlüsselwort-Wert-Paar-Syntax finden Sie [unter Übersetzer-Spezifikations Unterschlüssel](../../../odbc/reference/install/translator-specification-subkeys.md).  
  
 Die Schlüsselwörter **Translator** und **Setup** müssen in der *lpsztranslator* -Zeichenfolge enthalten sein. Die Übersetzungs-DLL wird mit dem Schlüsselwort **Translator** aufgelistet, und die Konvertierungs-Setup-DLL wird mit dem **Setup** -Schlüsselwort aufgelistet. Jedes Paar wird mit einem NULL-Byte beendet, und die gesamte Liste wird mit einem NULL-Byte beendet. (Das heißt, zwei NULL-Bytes markieren das Ende der Liste.) Das Format von *lpsztranslator* lautet wie folgt:  
  
 \0translator =*Translator-dll-Dateiname*\ 0 [Setup =*Setup-DLL-Dateiname*\ 0] \ 0  
  
 *lpszpathin*  
 Der Vollständiger Pfad, in dem der Konvertierer installiert werden soll, oder ein NULL-Zeiger. Wenn *lpszpath* ein NULL-Zeiger ist, werden die Übersetzer im System Verzeichnis installiert.  
  
 *lpszpathout*  
 Ausgeben Der Pfad des Zielverzeichnisses, in dem der Konvertierer installiert werden soll. Wenn der Konvertierer noch nicht installiert wurde, ist *lpszpathout* identisch mit *lpszpathin*. Wenn eine vorherige Installation des Konvertierers vorhanden ist, ist *lpszpathout* der Pfad der vorherigen Installation.  
  
 *cbpaarwert*  
 Der Länge von *lpszpathout.*  
  
 *pcbpathout*  
 Ausgeben Die Gesamtanzahl der Bytes, die in " *lpszpathout*" zurückgegeben werden können. Wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *cbpathoutmax*ist, wird der Ausgabepfad in *lpszpathout* auf *pcbpathoutmax* abzüglich des NULL-Beendigungs Zeichens gekürzt. Das *pcbpathout* -Argument kann ein NULL-Zeiger sein.  
  
 *fRequest*  
 Der Der Typ der Anforderung. *fRequest* muss einen der folgenden Werte enthalten:  
  
 ODBC_INSTALL_INQUIRY: Fragen Sie, wo ein Konvertierer installiert werden kann.  
  
 ODBC_INSTALL_COMPLETE: führen Sie die Installations Anforderung aus.  
  
 *lpdwusagecount*  
 Ausgeben Die Verwendungs Anzahl des Konvertierers, nachdem diese Funktion aufgerufen wurde.  
  
 Anwendungen sollten die Verwendungs Anzahl nicht festlegen. Diese Anzahl wird von ODBC beibehalten.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlinstalltranslatorex** "false" zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von **sqlinstallererror**abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Das *lpszpathout* -Argument war nicht groß genug, um den Ausgabepfad zu enthalten. Der Puffer enthält den abgeschnittene Pfad.<br /><br /> Das *cbpthoutmax* -Argument war 0, und das *fRequest* -Argument wurde ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung.|Das *fRequest* -Argument war keiner der folgenden:<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültige Schlüsselwort-Wert-Paare|Das *lpsztranslator* -Argument enthielt einen Syntax Fehler.|  
|ODBC_ERROR_INVALID_PATH|Ungültiger Installationspfad.|Das *lpszpathin* -Argument enthielt einen ungültigen Pfad.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Ungültige Parameter Sequenz.|Das *lpsztranslator* -Argument enthielt keine Liste von Schlüsselwort-Wert-Paaren.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Die Anzahl der Komponenten Verwendungs Zähler der Registrierung konnte nicht Inkrement oder Dekrement|Der Installer konnte die Verwendungs Anzahl des Konvertierungs Programms nicht erhöhen.|  
  
## <a name="comments"></a>Kommentare  
 **Sqlinstalltranslatorex** stellt einen Mechanismus bereit, um nur den Translator zu installieren. Mit dieser Funktion werden keine Dateien kopiert. Das Aufruf Programm ist dafür verantwortlich, die Konvertierungs Dateien zu kopieren.  
  
 **Sqlinstalltranslatorex** erhöht die Komponenten Verwendungs Anzahl für den installierten Konvertierer um 1. Wenn eine Version des Konvertierers bereits vorhanden ist, die Anzahl der Komponenten Verwendungs Werte für den Konvertierer jedoch nicht vorhanden ist, wird der Wert für die neue Komponenten Verwendungs Anzahl auf 2 festgelegt.  
  
 Das Anwendungs Setup Programm ist dafür verantwortlich, die Konvertierungs Datei physisch zu kopieren und die Anzahl der Datei Verwendung beizubehalten. Wenn die Konvertierungs Datei noch nicht installiert wurde, muss das Setup Programm der Anwendung die Datei oder Dateien kopieren und die Datei-oder Datei Verwendungs Anzahl erstellen. Wenn die Datei bereits installiert wurde, erhöht das Setup Programm einfach die Anzahl der Datei Verwendungs Daten.  
  
 Wenn bereits eine ältere Version des Konvertierungs Programms von der Anwendung installiert wurde, sollte der Konvertierer deinstalliert und dann erneut installiert werden, sodass die Verwendungs Anzahl der Konvertierungs Komponenten gültig ist. **Sqlremovetranslator** sollte aufgerufen werden, um die Anzahl von Komponenten Verwendungsraten zu verringern. Anschließend sollte **sqlinstalltranslatorex** aufgerufen werden, um die Anzahl der Komponenten Auslastung zu erhöhen. Das Setup Programm der Anwendung muss die alten Dateien durch die neue Datei ersetzen. Die Anzahl der Datei Verwendungs Daten bleibt unverändert, und andere Anwendungen, die die ältere Versionsdatei verwendeten, verwenden nun die neuere Version.  
  
 Die Länge des Pfads in " *lpszpathout* " in " **sqlinstalltranslatorex** " ermöglicht einen zweiphasigen Installationsprozess, sodass eine Anwendung ermitteln kann, was " *cbpathoutmax* " sein sollte, indem Sie " **sqlinstalltranslatorex** " mit dem ODBC_INSTALL_INQUIRY Modus " *fRequest* " aufrufen. Dadurch wird die Gesamtanzahl der Bytes zurückgegeben, die im *pcbpathout* -Puffer verfügbar sind. **Sqlinstalltranslatorex** kann dann mit einem *fRequest* von ODBC_INSTALL_COMPLETE aufgerufen werden, und das *cbpathoutmax* -Argument ist auf den Wert im *pcbpathout* -Puffer sowie auf das NULL-Beendigungs Zeichen festgelegt.  
  
 Wenn Sie sich dafür entscheiden, das zweistufige Modell für **sqlinstalltranslatorex**nicht zu verwenden, müssen Sie die Größe des Speichers für den Pfad des Zielverzeichnisses auf den Wert *_MAX_PATH festlegen,* wie in STDLIB. h definiert, um das Abschneiden zu verhindern.  
  
 Wenn *fRequest* ODBC_INSTALL_COMPLETE ist, lässt **sqlinstalltranslatorex** nicht zu, dass *lpszpathout* NULL ist (oder *cbpathoutmax* muss 0 sein). Wenn *fRequest* ODBC_INSTALL_COMPLETE ist, wird false zurückgegeben, wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *cbpaarwert*ist, wobei das Ergebnis der Kürzung auftritt.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Zurückgeben einer Standard Übersetzungs Option|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Auswählen von Übersetzer|[Sqlgettranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Entfernen von Übersetzer|[Sqlremovetranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
