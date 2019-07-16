---
title: ConfigTranslator-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- ConfigTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigTranslator
helpviewer_keywords:
- ConfigTranslator [ODBC]
ms.assetid: 7c22f07e-36de-425b-aa67-e32a84afae92
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 18bf7e3f66140ef92b520ea7c86b616ea7067b16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016698"
---
# <a name="configtranslator-function"></a>ConfigTranslator-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 2.0  
  
 **Zusammenfassung**  
 **ConfigTranslator** eine Standardoption für die Übersetzung für einen Übersetzer zurückgegeben. Es kann in die Translator-DLL oder eine separate Setup-DLL sein.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>Argumente  
 *hwndParent*  
 [Eingabe] Handle des übergeordneten Fensters. Die Funktion wird keine Dialogfelder angezeigt, wenn das Handle null ist.  
  
 *pvOption*  
 [Ausgabe] Eine für 32-Bit-Übersetzungsoption.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **ConfigTranslator** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert an den Installer Fehler Puffer gesendet wird, durch einen Aufruf von **SQLPostInstallerError**und erhalten Sie durch Aufrufen von **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster-handle|Die *HwndParent* Argument war ungültig oder NULL.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Oder Translator-treiberspezifischen Fehler|Ein Treiber-spezifische Fehler, für die kein definierten ODBC-Installer-Fehler vorliegt. Die *SzError* Argument in einem Aufruf der **SQLPostInstallerError** Funktion sollte die treiberspezifische Fehlermeldung enthalten.|  
|ODBC_ERROR_INVALID_OPTION|Ungültige Translation-option|Die *PvOption* Argument enthielt einen ungültigen Wert.|  
  
## <a name="comments"></a>Kommentare  
 Wenn das Konvertierungsprogramm nur eine einzelnen Übersetzungsoption unterstützt **ConfigTranslator** "true" zurück und legt fest *PvOption* der 32-Bit-Option. Andernfalls wird die Standardoption für die Übersetzung mit bestimmt. **ConfigTranslator** kann ein Dialogfeld mit dem ein Benutzer wählt eine Standardoption für die Übersetzung aus anzeigen.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Eine Übersetzungsoption abrufen|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Wählen einen Übersetzer|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Festlegen einer Übersetzungsoption|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
