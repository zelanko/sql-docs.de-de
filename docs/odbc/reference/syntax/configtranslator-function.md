---
title: ConfigTranslator-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fb2f26f87854d74a217885010014633963472787
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306031"
---
# <a name="configtranslator-function"></a>ConfigTranslator-Funktion
**Konformität**  
 Eingeführte Version: ODBC 2.0  
  
 **Zusammenfassung**  
 **ConfigTranslator** gibt eine Standardübersetzungsoption für einen Übersetzer zurück. Sie kann sich in der Übersetzer-DLL oder in einer separaten Setup-DLL befinden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>Argumente  
 *hwndParent*  
 [Eingabe] Übergeordnetes Fensterhandle. Die Funktion zeigt keine Dialogfelder an, wenn das Handle null ist.  
  
 *pvOption*  
 [Ausgabe] Eine 32-Bit-Übersetzungsoption.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **ConfigTranslator** FALSE zurückgibt, wird ein zugeordneter * \*pfErrorCode-Wert* durch einen Aufruf von **SQLPostInstallerError** an den Installer-Fehlerpuffer gesendet und kann durch Aufrufen von **SQLInstallerError**abgerufen werden. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fensterhandle|Das *Argument hwndParent* war ungültig oder NULL.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Treiber- oder Übersetzerspezifischer Fehler|Ein treiberspezifischer Fehler, für den kein definierter ODBC-Installationsfehler vorliegt. Das *SzError-Argument* in einem Aufruf der **SQLPostInstallerError-Funktion** sollte die treiberspezifische Fehlermeldung enthalten.|  
|ODBC_ERROR_INVALID_OPTION|Ungültige Übersetzungsoption|Das *argument pvOption* enthielt einen ungültigen Wert.|  
  
## <a name="comments"></a>Kommentare  
 Wenn der Übersetzer nur eine einzige Übersetzungsoption unterstützt, gibt **ConfigTranslator** TRUE zurück und setzt *pvOption* auf die 32-Bit-Option. Andernfalls wird die zu verwendende Standardübersetzungsoption bestimmt. **ConfigTranslator** kann ein Dialogfeld anzeigen, mit dem ein Benutzer eine Standardübersetzungsoption auswählt.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abrufen einer Übersetzungsoption|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Auswählen eines Übersetzers|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Festlegen einer Übersetzungsoption|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
