---
title: SQLGetTranslator-Funktion | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 948fc36da520777812c02e6e5d52a423eb9cc288
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536552"
---
# <a name="sqlgettranslator-function"></a>SQLGetTranslator-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 2.0  
  
 **Zusammenfassung**  
 **SQLGetTranslator** zeigt ein Dialogfeld, in dem ein Benutzer einen Übersetzer auswählen kann.  
  
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
 [Eingabe] Handle des übergeordneten Fensters.  
  
 *Wert*  
 [Eingabe/Ausgabe] Der Name des Übersetzers aus der Systeminformationen.  
  
 *cbNameMax*  
 [Eingabe] Maximale Länge von der *Wert* Puffer.  
  
 *pcbNameOut*  
 [Eingabe/Ausgabe] Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierung Byte) übergeben oder im zurückgegebenen *Wert*. Wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *CbNameMax*, der Translator-Name in *Wert* auf abgeschnitten *CbNameMax* minus der NULL-Terminierungszeichen. Die *PcbNameOut* Argument kann ein null-Zeiger sein.  
  
 *lpszPath*  
 [Ausgabe] Vollständiger Pfad des Konvertierungs-DLL.  
  
 *cbPathMax*  
 [Eingabe] Maximale Länge von der *LpszPath* Puffer.  
  
 *pcbPathOut*  
 [Ausgabe] Gesamte Anzahl der Bytes, die (mit Ausnahme der Null-Terminierung Byte) in zurückgegebenen *LpszPath*. Wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *CbPathMax*, der Translation-DLL-Pfad in *LpszPath* auf abgeschnitten *CbPathMax* minus der NULL-Terminierungszeichen. Die *PcbPathOut* Argument kann ein null-Zeiger sein.  
  
 *pvOption*  
 [Ausgabe] Übersetzung von 32-Bit-Option.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" zurück, wenn er erfolgreich ist, FALSE, wenn ein Fehler auftritt oder wenn der Benutzer das Dialogfeld abbricht.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetTranslator** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Die *CbNameMax* oder *CbPathMax* Argument war kleiner als oder gleich 0.|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster-handle|Die *HwndParent* Argument war ungültig oder NULL.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Name für Treiber oder das Konvertierungsprogramm|Die *Wert* Argument war ungültig. Es konnte nicht in der Registrierung gefunden werden.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber oder Translator-Setup-Bibliothek konnte nicht geladen werden.|Die Translator-Bibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_INVALID_OPTION|Ungültige Transaktion-option|Die *PvOption* Argument enthielt einen ungültigen Wert.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 Wenn *HwndParent* null ist oder wenn *Wert*, *LpszPath*, oder *PvOption* ist ein null-Zeiger **SQLGetTranslator** gibt FALSE zurück. Andernfalls wird die Liste der installierten Übersetzer im folgenden Dialogfeld.  
  
 ![Select Konvertierer (Dialogfeld)](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 Wenn *Wert* enthält den Namen eines gültigen Konvertierer, diese Option ausgewählt ist. Andernfalls \<keine Translator > aktiviert ist.  
  
 Wenn der Benutzer \<keine Translator >, den Inhalt der *Wert*, *LpszPath*, und *PvOption* werden nicht berührt. **SQLGetTranslator** legt *PcbNameOut* und *PcbPathOut* auf 0 und gibt TRUE zurück.  
  
 Wenn der Benutzer einen Übersetzer, **SQLGetTranslator** Aufrufe **ConfigTranslator** in die Translator-Setup-DLL. Wenn **ConfigTranslator** gibt FALSE zurück, **SQLGetTranslator** gibt zurück, um das Dialogfeld. Wenn **ConfigTranslator** gibt TRUE zurück, **SQLGetTranslator** gibt TRUE zurück, zusammen mit der ausgewählten Translator Name und Pfad Translation-Option.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Konfigurieren einen Übersetzer|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Ein Attribut für die Übersetzung abrufen|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Wenn eine Übersetzung-Attribut|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
