---
description: SQLSetConfigMode-Funktion
title: Sqlsetconfigmode-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConfigMode
helpviewer_keywords:
- SQLSetConfigMode function [ODBC]
ms.assetid: 09eb88ea-b6f6-4eca-b19d-0951cebc6c0a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5aab5274403a654362c5732d8ec3f6eccae3be96
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499583"
---
# <a name="sqlsetconfigmode-function"></a>SQLSetConfigMode-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0  
  
 **Zusammenfassung**  
 **Sqlsetconfigmode** legt den Konfigurations Modus fest, der angibt, wo die Odbc.ini Eintrag DSN-Werte in den Systeminformationen enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Argumente  
 *wconfigmode*  
 Der Der installerkonfigurationsmodus (siehe "Kommentare"). Der Wert in *wconfigmode* kann wie folgt lauten:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlsetconfigmode** false zurückgibt, kann ein zugeordneter " * \* pferrorcode* "-Wert durch Aufrufen von " **sqlinstallererror**" abgerufen werden. In der folgenden Tabelle sind die " * \* pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Ungültige Parameter Sequenz.|Das *wconfigmode* -Argument enthielt nicht ODBC_USER_DSN, ODBC_SYSTEM_DSN oder ODBC_BOTH_DSN.|  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion wird verwendet, um festzulegen, wo der Odbc.ini Eintrag mit DSN-Werten in den Systeminformationen enthalten ist. Wenn *wconfigmode* ODBC_USER_DSN ist, ist der DSN ein Benutzer-DSN, und die Funktion liest aus dem Odbc.ini Eintrag in HKEY_CURRENT_USER. Wenn Sie ODBC_SYSTEM_DSN ist, ist der DSN ein System-DSN, und die Funktion liest aus dem Odbc.ini Eintrag in HKEY_LOCAL_MACHINE. Wenn Sie ODBC_BOTH_DSN, wird HKEY_CURRENT_USER versucht, und wenn Sie fehlschlägt, wird HKEY_LOCAL_MACHINE verwendet.  
  
 Diese Funktion wirkt sich nicht auf **sqlkreatedatasource** und **SQLDriverConnect**aus. Der Konfigurations Modus muss festgelegt werden, wenn ein Treiber aus der Registrierung liest, indem er **sqlgetprivateprofilestring** aufführt oder durch Aufrufen von **sqlwrite teprivateprofilestring**in die Registrierung schreibt. Aufrufe von **sqlgetprivateprofilestring** und **sqlschreiteprivateprofilestring** verwenden den Konfigurations Modus, um zu ermitteln, auf welchem Teil der Registrierung gearbeitet werden soll.  
  
> [!CAUTION]  
>  **Sqlsetconfigmode** sollte nur bei Bedarf aufgerufen werden. Wenn der Modus nicht ordnungsgemäß festgelegt wurde, funktioniert das ODBC-Installationsprogramm möglicherweise nicht ordnungsgemäß.  
  
 **Sqlsetconfigmode** bewirkt eine direkte Registrierungs Änderung des Konfigurations Modus. Dies unterscheidet sich vom Prozess der Änderung des Konfigurations Modus durch einen **SQLConfigDataSource**-Befehl. Durch einen **SQLConfigDataSource** -Befehl wird der Konfigurations Modus so festgelegt, dass Benutzer-und System-DSNs beim Ändern eines DSN unterschieden werden. Vor der Rückgabe setzt **SQLConfigDataSource** den Konfigurations Modus auf bothdsn zurück.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Erstellen einer Datenquelle|[Sqlkreatedatasource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle über eine Verbindungs Zeichenfolge oder ein Dialogfeld|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Abrufen des Konfigurations Modus|[Sqlgetconfigmode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|
