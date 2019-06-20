---
title: SQLWriteDSNToIni-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5a36be7a98a39cab8b9df428b8d4bd9a1d399a1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536791"
---
# <a name="sqlwritedsntoini-function"></a>SQLWriteDSNToIni-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 1.0  
  
 **Zusammenfassung**  
 **SQLWriteDSNToIni** Fügt eine Datenquelle, um die Systeminformationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszDSN*  
 [Eingabe] Der Name der Datenquelle hinzufügen.  
  
 *lpszDriver*  
 [Eingabe] Treiberbeschreibung (normalerweise der Name des zugeordneten DBMS) für Benutzer anstelle des Namens des physischen Treiber angezeigt werden.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLWriteDSNToIni** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_INVALID_DSN|Ungültige DSN|Die *LpszDSN* Argument enthalten sind, eine Zeichenfolge, die für eine DSN ungültig war.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Name für Treiber oder das Konvertierungsprogramm|Die *LpszDriver* Argument war ungültig.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Der Installer konnte nicht in der Registrierung ein DSN zu erstellen.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLWriteDSNToIni** fügt die Datenquelle mit dem Abschnitt [ODBC-Datenquellen] der Systeminformationen. Anschließend erstellt Sie einen Abschnitt der Spezifikation für die Datenquelle und fügt ein einzelnes Schlüsselwort (**Treiber**) mit dem Namen der Treiber-DLL als Wert. Wenn Data Source-Spezifikation-Abschnitt bereits vorhanden ist, **SQLWriteDSNToIni** alten Abschnitts entfernt, bevor die neue erstellen.  
  
 Der Aufrufer dieser Funktion muss Data Source-Spezifikation-Abschnitt die Systeminformationen alle treiberspezifischen Schlüsselwörter und Werte hinzufügen.  
  
 Wenn der Name der Datenquelle standardmäßig **SQLWriteDSNToIni** erstellt außerdem die Spezifikation den Standardabschnitt-Treiber in den Systeminformationen.  
  
 Diese Funktion sollte nur von einem Setup-DLL aufgerufen werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)(in der Setup-DLL)|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Name der Datenquelle entfernen aus der Systeminformationen|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|
