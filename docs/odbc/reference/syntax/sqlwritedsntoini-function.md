---
title: SQLWriteDSNToIni-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLWriteDSNToIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteDSNToIni
helpviewer_keywords:
- SQLWriteDSNToIni [ODBC]
ms.assetid: dc7018b2-18d4-4657-96d0-086479a47474
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8bb141c8f54c49ca3a5c6fc4bc15d434f91795c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286960"
---
# <a name="sqlwritedsntoini-function"></a>SQLWriteDSNToIni-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0  
  
 **Zusammenfassung**  
 **SQLWriteDSNToIni** fügt den Systeminformationen eine Datenquelle hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszDSN*  
 [Eingabe] Name der hinzuzufügenden Datenquelle.  
  
 *lpszDriver*  
 [Eingabe] Treiberbeschreibung (in der Regel der Name des zugehörigen DBMS), die den Benutzern anstelle des physischen Treibernamens angezeigt wird.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLWriteDSNToIni** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* durch Aufrufen von **SQLInstallerError**abgerufen werden. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_DSN|Ungültiger DSN|Das *argument lpszDSN* enthielt eine Zeichenfolge, die für einen DSN ungültig war.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber- oder Übersetzername|Das *Argument lpszDriver* war ungültig.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Das Installationsprogramm konnte in der Registrierung keine DSN erstellen.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLWriteDSNToIni** fügt die Datenquelle zum Abschnitt [ODBC Data Sources] der Systeminformationen hinzu. Anschließend wird ein Spezifikationsabschnitt für die Datenquelle erstellt und ein einzelnes Schlüsselwort (**Treiber**) mit dem Namen der Treiber-DLL als Wert hinzugefügt. Wenn der Abschnitt für die Datenquellenspezifikation bereits vorhanden ist, entfernt **SQLWriteDSNToIni** den alten Abschnitt, bevor der neue erstellt wird.  
  
 Der Aufrufer dieser Funktion muss dem Abschnitt Datenquellenspezifikation der Systeminformationen alle treiberspezifischen Schlüsselwörter und Werte hinzufügen.  
  
 Wenn der Name der Datenquelle Standard ist, erstellt **SQLWriteDSNToIni** auch den Standardtreiberspezifikationsabschnitt in den Systeminformationen.  
  
 Diese Funktion sollte nur von einer Setup-DLL aufgerufen werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, Ändern oder Entfernen einer Datenquelle|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)(in der Setup-DLL)|  
|Hinzufügen, Ändern oder Entfernen einer Datenquelle|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Entfernen eines Datenquellennamens aus den Systeminformationen|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|
