---
description: SQLWriteDSNToIni-Funktion
title: Sqlwrite tedsnto ini-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: 08a1094d29bbba9dc52974bd1cef5cd6645aa5dc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421014"
---
# <a name="sqlwritedsntoini-function"></a>SQLWriteDSNToIni-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0  
  
 **Zusammenfassung**  
 **Sqlwrite tedsndeini** fügt den Systeminformationen eine Datenquelle hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszdsn*  
 Der Der Name der hinzu zufügenden Datenquelle.  
  
 *lpszDriver*  
 Der Treiber Beschreibung (in der Regel der Name des zugeordneten DBMS), der Benutzern anstelle des Namens des physischen Treibers angezeigt wird.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlwrite tedsntoini** "false" zurückgibt, kann ein zugeordneter " * \* pferrorcode* "-Wert durch Aufrufen von **sqlinstallererror**abgerufen werden. In der folgenden Tabelle sind die " * \* pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_DSN|Ungültiger DSN|Das *lpszdsn* -Argument enthielt eine Zeichenfolge, die für einen DSN ungültig war.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber-oder Konvertierungs Name|Das *lpszDriver* -Argument war ungültig.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Fehler beim Erstellen eines DSN in der Registrierung durch den Installer.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **Sqlwrite tedsndeini** fügt die Datenquelle zum Abschnitt [ODBC-Datenquellen] der Systeminformationen hinzu. Anschließend wird ein Spezifikations Abschnitt für die Datenquelle erstellt, und es wird ein einzelnes Schlüsselwort (**Driver**) mit dem Namen der Treiber-DLL als Wert hinzugefügt. Wenn der Abschnitt zur Datenquellen Spezifikation bereits vorhanden ist, entfernt **sqlschreitedsnesini** den alten Abschnitt vor der Erstellung der neuen.  
  
 Der Aufrufer dieser Funktion muss alle treiberspezifischen Schlüsselwörter und Werte zum Abschnitt Datenquellen Spezifikation der Systeminformationen hinzufügen.  
  
 Wenn der Name der Datenquelle Default ist, erstellt **sqlwrite tedsndeini** auch den Abschnitt mit der Standardtreiber Spezifikation in den Systeminformationen.  
  
 Diese Funktion sollte nur von einer Setup-DLL aufgerufen werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)(in der Setup-DLL)|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Entfernen eines Datenquellen namens aus den Systeminformationen|[Sqlremovedsnfromini](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|
