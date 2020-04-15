---
title: SQLGetTranslator-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetTranslator
helpviewer_keywords:
- SQLGetTranslator function [ODBC]
ms.assetid: 33879db3-5ef9-4585-9be5-69376157e017
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bcd5aeebab8539b8b94db56ff30892f4a7dbbac1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303271"
---
# <a name="sqlgettranslator-function"></a>SQLGetTranslator-Funktion
**Konformität**  
 Eingeführte Version: ODBC 2.0  
  
 **Zusammenfassung**  
 **SQLGetTranslator** zeigt ein Dialogfeld an, aus dem ein Benutzer einen Übersetzer auswählen kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLGetTranslator(  
     HWND      hwndParent,  
     LPSTR     lpszName,  
     WORD      cbNameMax,  
     WORD *    pcbNameOut,  
     LPSTR     lpszPath,  
     WORD      cbPathMax,  
     WORD *    pcbPathOut,  
     DWORD *   pvOption);  
```  
  
## <a name="arguments"></a>Argumente  
 *hwndParent*  
 [Eingabe] Übergeordnetes Fensterhandle.  
  
 *lpszName*  
 [Eingang/Ausgang] Name des Übersetzers aus den Systeminformationen.  
  
 *cbNameMax*  
 [Eingabe] Maximale Länge des *lpszName-Puffers.*  
  
 *pcbNameOut*  
 [Eingang/Ausgang] Gesamtanzahl der Bytes (mit Ausnahme des Null-Beendigungsbytes), die in *lpszName*übergeben oder zurückgegeben wurden. Wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *cbNameMax*ist, wird der Übersetzername in *lpszName* auf *cbNameMax* abzüglich des Null-Beendigungszeichens abgeschnitten. Das *Argument pcbNameOut* kann ein Nullzeiger sein.  
  
 *lpszPath*  
 [Ausgabe] Vollständiger Pfad der Übersetzungs-DLL.  
  
 *cbPathMax*  
 [Eingabe] Maximale Länge des *lpszPath-Puffers.*  
  
 *pcbPathOut*  
 [Ausgabe] Gesamtanzahl der Bytes (mit Ausnahme des Null-Beendigungsbytes), die in *lpszPath*zurückgegeben werden. Wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *cbPathMax*ist, wird der Übersetzungs-DLL-Pfad in *lpszPath* auf *cbPathMax* abzüglich des Nullbeendigungszeichens abgeschnitten. Das *Argument pcbPathOut* kann ein Nullzeiger sein.  
  
 *pvOption*  
 [Ausgabe] 32-Bit-Übersetzungsoption.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt oder wenn der Benutzer das Dialogfeld abbricht.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetTranslator** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge|Das Argument *cbNameMax* oder *cbPathMax* war kleiner oder gleich 0.|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fensterhandle|Das *Argument hwndParent* war ungültig oder NULL.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber- oder Übersetzername|Das *Argument lpszName* war ungültig. Sie konnte in der Registrierung nicht gefunden werden.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber- oder Übersetzereinrichtungsbibliothek konnte nicht geladen werden.|Die Übersetzerbibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_INVALID_OPTION|Ungültige Transaktionsoption|Das *argument pvOption* enthielt einen ungültigen Wert.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 Wenn *hwndParent* null ist oder wenn *lpszName*, *lpszPath*oder *pvOption* ein Nullzeiger ist, gibt **SQLGetTranslator** FALSE zurück. Andernfalls wird die Liste der installierten Übersetzer im folgenden Dialogfeld angezeigt.  
  
 ![Dialogfeld "Konvertierungsprogramm auswählen"](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 Wenn *lpszName* einen gültigen Übersetzernamen enthält, wird dieser ausgewählt. Andernfalls \<wird kein> ausgewählt.  
  
 Wenn der Benutzer \<Keine Übersetzer-> wählt, werden die Inhalte von *lpszName*, *lpszPath*und *pvOption* nicht berührt. **SQLGetTranslator** setzt *pcbNameOut* und *pcbPathOut* auf 0 und gibt TRUE zurück.  
  
 Wenn der Benutzer einen Übersetzer wählt, ruft **SQLGetTranslator** **ConfigTranslator** in der Setup-DLL des Übersetzers auf. Wenn **ConfigTranslator** FALSE zurückgibt, kehrt **SQLGetTranslator** zu seinem Dialogfeld zurück. Wenn **ConfigTranslator** TRUE zurückgibt, gibt **SQLGetTranslator** TRUE zusammen mit dem ausgewählten Übersetzernamen, Pfad und der Übersetzungsoption zurück.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Konfigurieren eines Übersetzers|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Abrufen eines Übersetzungsattributs|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Festlegen eines Übersetzungsattributs|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
