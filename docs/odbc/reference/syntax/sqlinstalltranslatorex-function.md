---
title: SQLInstallTranslatorEx-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 276b8627588bcd3472c12564db1e8c6e6af1ef2b
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53212529"
---
# <a name="sqlinstalltranslatorex-function"></a>SQLInstallTranslatorEx-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLInstallTranslatorEx** im Abschnitt "Odbcinst.ini", der die Systeminformationen (HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST Informationen zu einem Konvertierer hinzugefügt. INI\ODBC Übersetzer Registrierungsschlüssel).  
  
 Die Funktionalität von **SQLInstallTranslatorEx** kann auch mit zugegriffen werden [ODBCCONF. EXE-Datei](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
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
 *lpszTranslator*  
 [Eingabe] Dies muss eine doppelt Null-terminierte-Liste der Schlüsselwort-Wert-Paaren, die Beschreibung des Übersetzers enthalten. Weitere Informationen zur Syntax von Schlüsselwort-Wert-Paar finden Sie unter [Konvertierungsprogrammspezifikationen](../../../odbc/reference/install/translator-specification-subkeys.md).  
  
 Die **Translator** und **Setup** Schlüsselwörter enthalten sein müssen, der *LpszTranslator* Zeichenfolge. Die Übersetzung DLL wird aufgeführt, mit der **Translator** -Schlüsselwort und die Translator-Setup, die DLL wird aufgeführt, mit der **Setup** Schlüsselwort. Jedes Paar wird mit NULL Byte beendet, und die gesamte Liste wird mit einem Byte NULL beendet. (D. h., markieren Sie zwei NULL-Bytes am Ende der Liste.) Das Format der *LpszTranslator* lautet wie folgt:  
  
 \0Translator=*Translator-DLL-Dateiname*\0[Setup=*-Setup-DLL-Dateiname*\0]\0  
  
 *lpszPathIn*  
 [Eingabe] Vollständiger Pfad der, in denen das Konvertierungsprogramm installiert werden oder ein null-Zeiger. Wenn *LpszPath* ist ein null-Zeiger im Systemverzeichnis der Übersetzer installiert werden.  
  
 *lpszPathOut*  
 [Ausgabe] Der Pfad der das Zielverzeichnis, in dem das Konvertierungsprogramm installiert werden soll. Wenn das Konvertierungsprogramm nie installiert war, *LpszPathOut* ist identisch mit *LpszPathIn*. Wenn es vorhanden eine vorherige Installation des konvertierers ist, *LpszPathOut* ist der Pfad der vorherigen Installation.  
  
 *cbPathOutMax*  
 [Eingabe] Länge der *LpszPathOut.*  
  
 *pcbPathOut*  
 [Ausgabe] Gesamtzahl der Bytes, die für die Rückgabe in verfügbar *LpszPathOut*. Wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *CbPathOutMax*, den Ausgabepfad in *LpszPathOut* wird abgeschnitten, um *PcbPathOutMax* minus der NULL-Terminierungszeichen. Die *PcbPathOut* Argument kann ein null-Zeiger sein.  
  
 *Häufigsten*  
 [Eingabe] Typ der Anforderung. *Häufigsten* muss einen der folgenden Werte enthalten:  
  
 ODBC_INSTALL_INQUIRY: Erkundigen Sie sich, ein Übersetzer installiert werden können.  
  
 ODBC_INSTALL_COMPLETE: Die Installationsanforderung zu beenden.  
  
 *lpdwUsageCount*  
 [Ausgabe] Die Verwendungsanzahl des konvertierers, nachdem diese Funktion aufgerufen wurde.  
  
 Anwendungen sollten nicht die Verwendungsanzahl der festlegen. ODBC wird dieser Zähler zu verwalten.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLInstallTranslatorEx** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Die *LpszPathOut* Argument war nicht groß genug, um den Ausgabepfad enthalten. Der Puffer enthält den Pfad abgeschnitten.<br /><br /> Die *CbPathOutMax* Argument wurde 0 (null) und die *häufigsten* Argument war ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung|Die *häufigsten* Argument war keiner der folgenden:<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültiges Schlüsselwort-Wert-Paaren|Die *LpszTranslator* Argument enthalten einen Syntaxfehler.|  
|ODBC_ERROR_INVALID_PATH|Ungültiger-Installationspfad|Die *LpszPathIn* Argument enthalten einen ungültigen Pfad.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Ungültiger Parameter-Sequenz|Die *LpszTranslator* Argument keine Liste der Schlüsselwort-Wert-Paare enthalten.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Konnte nicht inkrementiert oder dekrementiert werden Verwendungszähler für die Registrierung der Komponente|Installerfehler beim Erhöhen der Translator-Verwendungsanzahl.|  
  
## <a name="comments"></a>Kommentare  
 **SQLInstallTranslatorEx** bietet einen Mechanismus, um nur das Konvertierungsprogramm installieren. Diese Funktion ist nicht tatsächlich alle Dateien kopiert werden. Das aufrufende Programm ist verantwortlich für die Translator-Dateien zu kopieren.  
  
 **SQLInstallTranslatorEx** die Verwendungsanzahl der Komponente für das installierte Konvertierungsprogramm um 1 erhöht. Wenn bereits eine Version des konvertierers, aber die Verwendungsanzahl der Komponente für das Konvertierungsprogramm ist nicht vorhanden, wird der neue Komponente Nutzung Count-Wert auf 2 festgelegt.  
  
 Das Setupprogramm für die Anwendung ist für die Translator-Datei physisch zu kopieren, und verwalten die Verwendungsanzahl der Datei verantwortlich. Wenn die Translator-Datei noch nicht installiert wurde, muss das Installationsprogramm der Anwendung kopieren von Dateien und erstellen die Datei(en) Verwendungsanzahl. Wenn die Datei zuvor installiert wurde, erhöht das Setup-Programm einfach die Verwendungsanzahl der Datei.  
  
 Wenn eine ältere Version des Übersetzers zuvor von der Anwendung installiert wurde, sollte der Übersetzer deinstalliert und anschließend erneut installieren, sodass die Verwendungsanzahl der Translator-Komponente gültig ist. **SQLRemoveTranslator** aufgerufen werden, um die verringert der Verwendungsanzahl der Komponente, und klicken Sie dann **SQLInstallTranslatorEx** aufgerufen werden, um die Verwendungsanzahl der Komponente zu erhöhen. Das Installationsprogramm der Anwendung muss die alten-Dateien mit der neuen Datei ersetzen. Die Verwendungsanzahl der Datei bleibt unverändert, und andere Anwendungen, die die ältere Versionsdatei verwendet, verwenden nun die neuere Version.  
  
 Die Länge des Pfads in *LpszPathOut* in **SQLInstallTranslatorEx** ermöglicht ein Prozess mit zwei-Phasen installieren, damit eine Anwendung, was bestimmen kann *CbPathOutMax* sollten werden Sie durch Aufrufen von **SQLInstallTranslatorEx** mit einer *häufigsten* ODBC_INSTALL_INQUIRY-Modus. Dies gibt die Gesamtzahl der Bytes, die zur Verfügung, in der *PcbPathOut* Puffer. **SQLInstallTranslatorEx** kann dann aufgerufen werden, mit einer *häufigsten* von ODBC_INSTALL_COMPLETE und *CbPathOutMax* Argument festgelegt wird, auf den Wert in der *PcbPathOut* Puffer sowie das Zeichen Null-Terminierung vorliegt.  
  
 Wenn Sie nicht verwenden, das Zweiphasen-Modell für **SQLInstallTranslatorEx**, müssen Sie festlegen, *CbPathOutMax*, die definiert die Größe des Speichers für den Pfad des Zielverzeichnisses, um die _MAX_PATH Wert definiert in Stdlib.h, um das Abschneiden zu verhindern.  
  
 Wenn *häufigsten* ist ODBC_INSTALL_COMPLETE, **SQLInstallTranslatorEx** lässt keine *LpszPathOut* gleich NULL sein (oder *CbPathOutMax* 0 ist). Wenn *häufigsten* ODBC_INSTALL_COMPLETE ist, "false" wird zurückgegeben, wenn die Anzahl der Bytes, die für die Rückgabe verfügbar ist, größer als oder gleich *CbPathOutMax*, mit dem Ergebnis, um ein Abschneiden auftritt.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Eine Standardoption für die Übersetzung zurückgeben|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Auswählen der Übersetzer|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Entfernen der Übersetzer|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
