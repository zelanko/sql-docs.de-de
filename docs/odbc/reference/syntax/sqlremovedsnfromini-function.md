---
title: Sqlremovedsnfromini-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDSNFromIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDSNFromIni
helpviewer_keywords:
- SQLRemoveDSNFromIni function [ODBC]
ms.assetid: bb2e8273-7b61-4113-bfc8-f7ccc607c811
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4cc83a8cafffc9b5d1166df76d91ce4c63f0b858
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68024530"
---
# <a name="sqlremovedsnfromini-function"></a>SQLRemoveDSNFromIni-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0  
  
 **Zusammenfassung**  
 **Sqlremovedsnfromini** entfernt eine Datenquelle aus den Systeminformationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLRemoveDSNFromIni(  
     LPCSTR   lpszDSN);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszdsn*  
 Der Der Name der zu entfernenden Datenquelle.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt "true" zurück, wenn die Datenquelle entfernt wird oder die Datenquelle nicht in der Datei "ODBC. ini" war. Wenn die Datenquelle nicht entfernt werden kann, wird false zurückgegeben.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlremovedsnfromini** false zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von " **sqlinstallererror**" abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_DSN|Ungültiger DSN|Das *lpszdsn* -Argument war ungültig.|  
|ODBC_ERROR_REQUEST_FAILED|Anforderung fehlgeschlagen|Der Installer konnte die DSN-Informationen nicht aus der Registrierung entfernen.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **Sqlremovedsnfromini** entfernt den Namen der Datenquelle aus dem Abschnitt [ODBC-Datenquellen] der Systeminformationen. Außerdem wird der Abschnitt Datenquellen Spezifikation aus den Systeminformationen entfernt.  
  
 Diese Funktion sollte nur von einer Treiber-Setup Bibliothek aufgerufen werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[ConfigDSN ausgeführt werden](../../../odbc/reference/syntax/configdsn-function.md)|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Entfernen der Standarddaten Quelle|[Sqlremovedefaultdatasource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Hinzufügen eines Datenquellen namens zu den Systeminformationen|[Sqlschreitedsnder ini](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
