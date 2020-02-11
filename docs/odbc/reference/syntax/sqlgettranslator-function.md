---
title: Sqlgettranslator-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f769d3c5b2dcfe5d2aa8a431695cb18a52893b91
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68030651"
---
# <a name="sqlgettranslator-function"></a>SQLGetTranslator-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 2,0  
  
 **Zusammenfassung**  
 **Sqlgettranslator** zeigt ein Dialogfeld an, in dem ein Benutzer einen Übersetzer auswählen kann.  
  
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
 Der Handle des übergeordneten Fensters.  
  
 *lpszname*  
 [Eingabe/Ausgabe] Der Name des Konvertierers aus den Systeminformationen.  
  
 *cbnamemax*  
 Der Maximale Länge des *lpszname* -Puffers.  
  
 *pcbnameout*  
 [Eingabe/Ausgabe] Die Gesamtanzahl der Bytes (mit Ausnahme des NULL-Terminierungs Byte), die in *lpszname*übergeben oder zurückgegeben wurde. Wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *cbnamemax*ist, wird der Konvertierungs Name in *lpszname* auf *cbnamemax* abzüglich des NULL-Beendigungs Zeichens gekürzt. Das *pcbnameout* -Argument kann ein NULL-Zeiger sein.  
  
 *lpszpath*  
 Ausgeben Vollständiger Pfad der Übersetzungs-DLL.  
  
 *cbpathmax*  
 Der Maximale Länge des *lpszpath* -Puffers.  
  
 *pcbpathout*  
 Ausgeben Die Gesamtanzahl der Bytes (mit Ausnahme des NULL-Beendigungs Byte), die in *lpszpath*zurückgegeben wurde. Wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *cbpathmax*ist, wird der Übersetzungs-DLL-Pfad in *lpszpath* auf *cbpathmax* abzüglich des NULL-Beendigungs Zeichens gekürzt. Das *pcbpathout* -Argument kann ein NULL-Zeiger sein.  
  
 *pvoption*  
 [Output] 32-Bit-Übersetzungs Option.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, false, wenn Sie fehlschlägt oder wenn der Benutzer das Dialogfeld abbricht.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlgettranslator** "false" zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von **sqlinstallererror**abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Das *cbnamemax* -oder *cbpathmax* -Argument war kleiner oder gleich 0 (null).|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster handle.|Das *hwndParent* -Argument war ungültig oder NULL.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber-oder Konvertierungs Name|Das *lpszname* -Argument war ungültig. Sie konnte nicht in der Registrierung gefunden werden.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber-oder Konvertierungs-Setup Bibliothek konnte nicht geladen werden.|Die Konvertierungs Bibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_INVALID_OPTION|Ungültige Transaktions Option|Das *pvoption* -Argument enthielt einen ungültigen Wert.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 Wenn *hwndParent* NULL ist oder wenn *lpszname*, *lpszpath*oder *pvoption* ein NULL-Zeiger ist, gibt **sqlgettranslator** den Wert false zurück. Andernfalls wird die Liste der installierten Konvertierer im folgenden Dialogfeld angezeigt.  
  
 ![Dialogfeld "Konvertierungsprogramm auswählen"](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 Wenn " *lpszname* " einen gültigen Übersetzungs Namen enthält, wird dieser ausgewählt. Andernfalls wird \<kein Konvertierungs> ausgewählt.  
  
 Wenn der Benutzer keine \<Konvertierungs> auswählt, wird der Inhalt von *lpszname*, *lpszpath*und *pvoption* nicht berührt. **Sqlgettranslator** legt *pcbnameout* und *pcbpathout* auf 0 fest und gibt true zurück.  
  
 Wenn der Benutzer einen Übersetzer auswählt, ruft **sqlgettranslator** **ConfigTranslator** in der Setup-DLL des Konvertierungs Programms auf. Wenn **ConfigTranslator** false zurückgibt, kehrt **sqlgettranslator** in das zugehörige Dialogfeld zurück. Wenn **ConfigTranslator** true zurückgibt, gibt **sqlgettranslator** den Wert true zusammen mit dem ausgewählten Übersetzungs Namen, dem Pfad und der Übersetzungs Option zurück.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Konfigurieren eines Konvertierers|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Erhalten eines Translation-Attributs|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Festlegen eines Translation-Attributs|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
