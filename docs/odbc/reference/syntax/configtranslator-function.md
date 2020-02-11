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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68016698"
---
# <a name="configtranslator-function"></a>ConfigTranslator-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 2,0  
  
 **Zusammenfassung**  
 **ConfigTranslator** gibt eine Standard Übersetzungs Option für einen Übersetzer zurück. Sie kann sich in der Konvertierungs-DLL oder einer separaten Setup-DLL befinden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>Argumente  
 *hwndParent*  
 Der Handle des übergeordneten Fensters. Die Funktion zeigt keine Dialogfelder an, wenn das Handle NULL ist.  
  
 *pvoption*  
 Ausgeben Eine 32-Bit-Übersetzungs Option.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **ConfigTranslator** "false" zurückgibt, wird ein zugeordneter " * \*pferrorcode* "-Wert durch einen Aufruf von " **sqlpostinstallererror** " an den Installer-Fehler Puffer gesendet und kann durch Aufrufen von **sqlinstallererror**abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster handle.|Das *hwndParent* -Argument war ungültig oder NULL.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Treiber-oder Konvertierungs spezifischer Fehler|Ein Treiber spezifischer Fehler, für den kein ODBC-Installationsprogramm Fehler definiert wurde. Das *szerror* -Argument in einem aufzurufenden Befehl der **sqlpostinstallererror** -Funktion sollte die Treiber spezifische Fehlermeldung enthalten.|  
|ODBC_ERROR_INVALID_OPTION|Ungültige Übersetzungs Option|Das *pvoption* -Argument enthielt einen ungültigen Wert.|  
  
## <a name="comments"></a>Kommentare  
 Wenn der Konvertierer nur eine einzige Übersetzungs Option unterstützt, gibt **ConfigTranslator** true zurück und legt *pvoption* auf die 32-Bit-Option fest. Andernfalls wird die zu verwendende Standard Übersetzungs Option festgelegt. **ConfigTranslator** kann ein Dialogfeld anzeigen, mit dem ein Benutzer eine Standard Übersetzungs Option auswählt.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Aktivieren einer Übersetzungs Option|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Auswählen eines Konvertierers|[Sqlgettranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Festlegen einer Übersetzungs Option|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
