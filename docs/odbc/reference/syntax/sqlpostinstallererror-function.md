---
title: SQLPostInstallerError-Funktion | Microsoft Docs
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
ms.openlocfilehash: cdceff5c4e175ba9f135c6e5e4405933b1a86b7c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306891"
---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLPostInstallerError** stellt einen Mechanismus für eine Treiber- oder Übersetzer-Setupbibliothek bereit, um Fehler für die Funktionen **ConfigDriver**, **ConfigDSN**und **ConfigTranslator** an die Installationsfehlerwarteschlange zu melden. Anwendungen verwenden diese API nicht. Sie verwenden **SQLInstallerError,** um den Fehler abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>Argumente  
 *fErrorCode*  
 [Eingabe] Installer-Fehlercode.  
  
 *szErrorMsg*  
 [Eingabe] Fehlermeldungstext.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS oder SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLPostInstallerError** gibt keine Fehlerwerte für sich selbst. Wenn der Fehler erfolgreich in der Installationsfehlerwarteschlange (abrufbar mit **SQLInstallerError**) gesendet wurde, wird SQL_SUCCESS zurückgegeben. SQL_ERROR wird zurückgegeben, wenn der Wert im *dwErrorCode-Argument* nicht zu den angegebenen Installationsfehlercodes gehört.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, Ändern oder Entfernen eines Treibers|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|Hinzufügen, Ändern oder Entfernen von Datenquellen|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Festlegen einer Übersetzungsoption|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|
