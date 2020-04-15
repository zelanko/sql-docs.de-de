---
title: SQLGetConfigMode-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConfigMode
helpviewer_keywords:
- SQLGetConfigMode function [ODBC]
ms.assetid: b96ab3b8-08d5-4fea-9ffe-e03043efbf2d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc11bec24ede3352dd43f3645fb8c720b77fdabe
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285690"
---
# <a name="sqlgetconfigmode-function"></a>SQLGetConfigMode-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLGetConfigMode** ruft den Konfigurationsmodus ab, der angibt, wo sich der Odbc.ini-Eintrag mit DSN-Werten in den Systeminformationen befindet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Argumente  
 *pwConfigMode*  
 [Ausgabe] Zeiger auf den Puffer, der den Konfigurationsmodus enthält. (Siehe "Kommentare.") Der Wert in * \*pwConfigMode* kann wie:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetConfigMode** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion wird verwendet, um zu bestimmen, wo sich die DSN-Werte von Odbc.ini in den Systeminformationen befinden. Wenn * \*pwConfigMode* ODBC_USER_DSN ist, ist der DSN ein Benutzer-DSN und die Funktion liest aus dem Odbc.ini-Eintrag in HKEY_CURRENT_USER. Wenn es ODBC_SYSTEM_DSN ist, ist der DSN ein System-DSN und die Funktion liest aus dem Odbc.ini-Eintrag in HKEY_LOCAL_MACHINE. Wenn es ODBC_BOTH_DSN ist, wird HKEY_CURRENT_USER ausprobiert, und wenn es fehlschlägt, wird HKEY_LOCAL_MACHINE verwendet.  
  
 Standardmäßig gibt **SQLGetConfigMode** ODBC_BOTH_DSN zurück. Wenn ein Benutzer-DSN oder ein System-DSN durch einen Aufruf von **SQLConfigDataSource**erstellt wird, legt die Funktion den Konfigurationsmodus auf ODBC_USER_DSN oder ODBC_SYSTEM_DSN, um Benutzer- und System-DSNs beim Ändern eines DSN zu unterscheiden. Vor der Rückkehr setzt **SQLConfigDataSource** den Konfigurationsmodus auf ODBC_BOTH_DSN zurück.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Festlegen des Konfigurationsmodus|[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|
