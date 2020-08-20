---
description: SQLPostInstallerError-Funktion
title: Sqlpostinstallererror-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPostInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPostInstallerError
helpviewer_keywords:
- SQLPostInstallerError function [ODBC]
ms.assetid: 4c60d827-b2d2-4f27-b220-daa9e1fcdd8d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a041069de4c8b86946f7088d6a46462468cc3656
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487209"
---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0  
  
 **Zusammenfassung**  
 **Sqlpostinstallererror** bietet einen Mechanismus für eine Treiber-oder Konvertierungs-Setup Bibliothek zum Melden von Fehlern für die Funktionen " **ConfigDriver**", " **ConfigDSN**" und " **ConfigTranslator** " in der Fehler Warteschlange des Installers. Diese API wird von Anwendungen nicht verwendet. Sie verwenden **sqlinstallererror** zum Abrufen des Fehlers.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>Argumente  
 *"ferrorcode"*  
 Der Installationsprogramm Fehlercode.  
  
 *szErrorMsg*  
 Der Fehlermeldungs Text.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS oder SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnose  
 **Sqlpostinstallererror** sendet keine Fehler Werte für sich selbst. Wenn der Fehler erfolgreich an die Fehler Warteschlange des Installers gesendet wurde (abgerufen mit **sqlinstallererror**), wird SQL_SUCCESS zurückgegeben. SQL_ERROR wird zurückgegeben, wenn der Wert im *dwErrorCode* -Argument keinem der angegebenen Installationsfehler Codes entspricht.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen eines Treibers|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|Hinzufügen, ändern oder Entfernen von Datenquellen|[ConfigDSN ausgeführt werden](../../../odbc/reference/syntax/configdsn-function.md)|  
|Festlegen einer Übersetzungs Option|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|
