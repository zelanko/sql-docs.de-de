---
title: Sqlvaliddsn-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLValidDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLValidDSN
helpviewer_keywords:
- SQLValidDSN [ODBC]
ms.assetid: 930d1d89-337a-4429-85a2-84ee10555ac9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bbd8df72bcb0e76c8abcc3d738c2ff8da61a7bfe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039486"
---
# <a name="sqlvaliddsn-function"></a>SQLValidDSN-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 2,0  
  
 **Zusammenfassung**  
 **Sqlvaliddsn** überprüft die Länge und die Gültigkeit des Datenquellen namens, bevor der Name den Systeminformationen hinzugefügt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszdsn*  
 Der Der zu überprüfende Datenquellen Name.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn der Datenquellen Name gültig ist. Er gibt false zurück, wenn der Datenquellen Name ungültig ist oder der Funktions Aufrufvorgang fehlgeschlagen ist.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlvaliddsn** false zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von " **sqlinstallererror**" abgerufen werden. Ein * \*"pferrorcode* " wird nur zurückgegeben, wenn der Funktionsaufrufe fehlgeschlagen ist, nicht, wenn "false" zurückgegeben wurde, weil der Datenquellen Name ungültig In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **Sqlvaliddsn** wird vom [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) eines Treibers aufgerufen, um die Länge des Datenquellen namens und die Gültigkeit der einzelnen Zeichen im Datenquellen Namen zu überprüfen. Er überprüft, ob die Länge des Namens größer als SQL_MAX_DSN_LENGTH ist, wie in sqlext. h definiert. (Die Länge des Datenquellen namens wird auch von [sqlschreitedsnyini](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)geprüft.) **Sqlvaliddsn** überprüft, ob eine der folgenden ungültigen Zeichen im Datenquellen Namen enthalten ist:  
  
 [ ] { } ( ) , ; ? * = ! \@ \  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (in der Setup-DLL)|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Schreiben eines Datenquellen namens in die Systeminformationen|[Sqlschreitedsnder ini](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
