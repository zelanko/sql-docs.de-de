---
title: SQLRemoveDSNFromIni-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 848e82741954ab24941d5d519699292727ca25d6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301799"
---
# <a name="sqlremovedsnfromini-function"></a>SQLRemoveDSNFromIni-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0  
  
 **Zusammenfassung**  
 **SQLRemoveDSNFromIni** entfernt eine Datenquelle aus den Systeminformationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLRemoveDSNFromIni(  
     LPCSTR   lpszDSN);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszDSN*  
 [Eingabe] Name der zu entfernenden Datenquelle.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn die Datenquelle entfernt wird oder die Datenquelle nicht in der Datei Odbc.ini enthalten war. Es gibt FALSE zurück, wenn die Datenquelle nicht entfernt werden kann.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLRemoveDSNFromIni** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* durch Aufrufen von **SQLInstallerError**abgerufen werden. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_DSN|Ungültiger DSN|Das Argument *lpszDSN* war ungültig.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Das Installationsprogramm konnte die DSN-Informationen nicht aus der Registrierung entfernen.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLRemoveDSNFromIni** entfernt den Datenquellennamen aus dem Abschnitt [ODBC-Datenquellen] der Systeminformationen. Außerdem wird der Abschnitt datenquellenspezifikation aus den Systeminformationen entfernt.  
  
 Diese Funktion sollte nur von einer Treibereinrichtungsbibliothek aufgerufen werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, Ändern oder Entfernen einer Datenquelle|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Hinzufügen, Ändern oder Entfernen einer Datenquelle|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Entfernen der Standarddatenquelle|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Hinzufügen eines Datenquellennamens zu den Systeminformationen|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
