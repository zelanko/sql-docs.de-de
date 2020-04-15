---
title: SQLInstallTranslatorEx-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302091"
---
# <a name="sqlinstalltranslatorex-function"></a>SQLInstallTranslatorEx-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLInstallTranslatorEx** fügt informationen zu einem Übersetzer zum Abschnitt Odbcinst.ini der Systeminformationen hinzu (HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBCINST. Registrierungsschlüssel FÜR INI-ODBC-Übersetzer).  
  
 Auf die Funktionalität von **SQLInstallTranslatorEx** kann auch mit [ODBCCONF zugegriffen werden. EXE](../../../odbc/odbcconf-exe.md).  
  
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
 *lpszÜbersetzer*  
 [Eingabe] Dies muss eine doppelt null-terminierte Liste von Schlüsselwort-Wert-Paaren enthalten, die den Übersetzer beschreiben. Weitere Informationen zur Syntax des Schlüsselwort-Wert-Paars finden Sie unter [Translator Specification Subkeys](../../../odbc/reference/install/translator-specification-subkeys.md).  
  
 Die Schlüsselwörter **Translator** und **Setup** müssen in der *lpszTranslator-Zeichenfolge* enthalten sein. Die Übersetzungs-DLL wird mit dem Schlüsselwort **Translator** und die Übersetzer-Setup-DLL mit dem **Schlüsselwort Setup** aufgelistet. Jedes Paar wird mit einem NULL-Byte beendet, und die gesamte Liste wird mit einem NULL-Byte beendet. (Das heißt, zwei NULL-Bytes markieren das Ende der Liste.) Das Format von *lpszTranslator* ist wie folgt:  
  
 '0Translator=*Translator-DLL-Dateiname*'0[Setup=*Setup-DLL-Dateiname*'0]'0'0  
  
 *lpszPathIn*  
 [Eingabe] Vollständiger Pfad, an dem der Übersetzer installiert werden soll, oder einen Nullzeiger. Wenn *lpszPath* ein Nullzeiger ist, werden die Übersetzer im Systemverzeichnis installiert.  
  
 *lpszPathOut*  
 [Ausgabe] Der Pfad des Zielverzeichnisses, in dem der Übersetzer installiert werden soll. Wenn der Übersetzer noch nie installiert wurde, ist *lpszPathOut* identisch mit *lpszPathIn*. Wenn eine vorherige Installation des Übersetzers vorhanden ist, ist *lpszPathOut* der Pfad der vorherigen Installation.  
  
 *cbPathOutMax*  
 [Eingabe] Länge von *lpszPathOut.*  
  
 *pcbPathOut*  
 [Ausgabe] Gesamtanzahl der bytes, die in *lpszPathOut*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *cbPathOutMax*ist, wird der Ausgabepfad in *lpszPathOut* auf *pcbPathOutMax* abzüglich des Nullbeendigungszeichens abgeschnitten. Das *Argument pcbPathOut* kann ein Nullzeiger sein.  
  
 *fRequest*  
 [Eingabe] Art der Anforderung. *fRequest* muss einen der folgenden Werte enthalten:  
  
 ODBC_INSTALL_INQUIRY: Erkundigen Sie sich, wo ein Übersetzer installiert werden kann.  
  
 ODBC_INSTALL_COMPLETE: Schließen Sie die Installationsanforderung ab.  
  
 *lpdwUsageCount*  
 [Ausgabe] Die Verwendungsanzahl des Übersetzers, nachdem diese Funktion aufgerufen wurde.  
  
 Anwendungen sollten die Verwendungsanzahl nicht festlegen. ODBC behält diese Anzahl bei.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLInstallTranslatorEx** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge|Das Argument *lpszPathOut* war nicht groß genug, um den Ausgabepfad zu enthalten. Der Puffer enthält den abgeschnittenen Pfad.<br /><br /> Das *Argument cbPathOutMax* war 0, und das *argument fRequest* wurde ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Anforderungstyp|Das *fRequest-Argument* war nicht eines der folgenden:<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültige Schlüsselwort-Wert-Paare|Das *Argument lpszTranslator* enthielt einen Syntaxfehler.|  
|ODBC_ERROR_INVALID_PATH|Ungültiger Installationspfad|Das Argument *lpszPathIn* enthielt einen ungültigen Pfad.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Ungültige Parametersequenz|Das Argument *lpszTranslator* enthielt keine Liste von Schlüsselwort-Wert-Paaren.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Die Anzahl der Komponentennutzung der Registrierung konnte nicht erhöht oder dekrementiert werden.|Das Installationsprogramm konnte die Verwendungsanzahl des Übersetzers nicht erhöhen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLInstallTranslatorEx** bietet einen Mechanismus, um nur den Übersetzer zu installieren. Diese Funktion kopiert eigentlich keine Dateien. Das aufrufende Programm ist für das Kopieren der Übersetzerdateien verantwortlich.  
  
 **SQLInstallTranslatorEx** erhöht die Anzahl der Komponentenverwendungen für den installierten Übersetzer um 1. Wenn bereits eine Version des Übersetzers vorhanden ist, aber die Verwendungsanzahl der Komponenten für den Übersetzer nicht vorhanden ist, wird der Wert für die Anzahl der neuen Komponentenverwendungaufwerte auf 2 festgelegt.  
  
 Das Anwendungseinrichtungsprogramm ist für das physische Kopieren der Übersetzerdatei und die Aufrechterhaltung der Dateinutzungsanzahl verantwortlich. Wenn die Übersetzerdatei noch nicht installiert wurde, muss das Anwendungsinstallationsprogramm die Datei oder die Dateien kopieren und die Verwendungsanzahl der Datei oder Dateien erstellen. Wenn die Datei zuvor installiert wurde, erhöht das Setupprogramm einfach die Dateinutzungsanzahl.  
  
 Wenn zuvor eine ältere Version des Übersetzers von der Anwendung installiert wurde, sollte der Übersetzer deinstalliert und dann neu installiert werden, damit die Verwendungsanzahl der Übersetzerkomponenten gültig ist. **SQLRemoveTranslator** sollte aufgerufen werden, um die Anzahl der Komponentenverwendungen zu reduzieren, und dann sollte **SQLInstallTranslatorEx** aufgerufen werden, um die Anzahl der Komponentenverwendungen zu erhöhen. Das Anwendungsinstallationsprogramm muss die alte Datei oder die alten Dateien durch die neue Datei ersetzen. Die Anzahl der Dateiverwendungen bleibt unverändert, und andere Anwendungen, die die ältere Versionsdatei verwendet haben, verwenden nun die neuere Version.  
  
 Die Länge des Pfads in *lpszPathOut* in **SQLInstallTranslatorEx** ermöglicht einen zweiphasigen Installationsprozess, sodass eine Anwendung bestimmen kann, wie *cbPathOutMax* sein sollte, indem **sie SQLInstallTranslatorEx** mit einer *fRequest* ODBC_INSTALL_INQUIRY-Modus aufruft. Dadurch wird die Gesamtzahl der im *pcbPathOut-Puffer* verfügbaren Bytes zurückgegeben. **SQLInstallTranslatorEx** kann dann mit einer *fRequest* von ODBC_INSTALL_COMPLETE aufgerufen werden und das *argument cbPathOutMax* auf den Wert im *pcbPathOut-Puffer* sowie das Null-Beendigungszeichen festgelegt.  
  
 Wenn Sie das Zweiphasenmodell für **SQLInstallTranslatorEx**nicht verwenden möchten, müssen Sie *cbPathOutMax*festlegen, der die Größe des Speichers für den Pfad des Zielverzeichnisses definiert, auf den Wert _MAX_PATH, wie in Stdlib.h definiert, um Abschneiden zu verhindern.  
  
 Wenn *fRequest* ODBC_INSTALL_COMPLETE ist, lässt **SQLInstallTranslatorEx** nicht zu, dass *lpszPathOut* NULL (oder *cbPathOutMax* 0) ist. Wenn *fRequest* ODBC_INSTALL_COMPLETE ist, wird FALSE zurückgegeben, wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *cbPathOutMax*ist, mit dem Ergebnis, dass die Abschneide erfolgt.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben einer Standardübersetzungsoption|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Auswahl von Übersetzern|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Entfernen von Übersetzern|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
