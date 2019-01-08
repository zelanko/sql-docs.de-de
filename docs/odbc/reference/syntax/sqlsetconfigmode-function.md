---
title: SQLSetConfigMode-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a10ec8f8fa6ef2b0e310680f58252f98628ff045
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53215609"
---
# <a name="sqlsetconfigmode-function"></a>SQLSetConfigMode-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLSetConfigMode** legt den Konfigurationsmodus zu wechseln, der angibt, in dem der Odbc.ini Eintrag Auflisten von DSN-Werte in den Systeminformationen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Argumente  
 *wConfigMode*  
 [Eingabe] Der Installer-Konfigurationsmodus (siehe "Kommentare"). Der Wert in *wConfigMode* sind möglich:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetConfigMode** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Ungültiger Parameter-Sequenz|Die *wConfigMode* Argument enthielt keine ODBC_USER_DSN ODBC_SYSTEM_DSN oder ODBC_BOTH_DSN.|  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion wird verwendet, um festzulegen, in denen die Odbc.ini Auflisten von DSN-Werte in den Systeminformationen spielt. Wenn *wConfigMode* ODBC_USER_DSN, der DSN ist eine Benutzer-DSN ist, und die Funktion liest aus dem Eintrag der Odbc.ini in HKEY_CURRENT_USER. Wenn es sich um ODBC_SYSTEM_DSN handelt, der DSN ist eine System-DSN, und die Funktion liest aus dem Eintrag der Odbc.ini in HKEY_LOCAL_MACHINE. HKEY_CURRENT_USER wird versucht, wenn es sich um ODBC_BOTH_DSN ist, und falls nicht, klicken Sie dann HKEY_LOCAL_MACHINE dient.  
  
 Diese Funktion hat keine Auswirkungen auf **SQLCreateDataSource** und **SQLDriverConnect**. Konfigurationsmodus muss festgelegt werden, wenn ein Treiber aus der Registrierung durch den Aufruf liest **SQLGetPrivateProfileString** oder in die Registrierung geschrieben werden, durch den Aufruf **SQLWritePrivateProfileString**. Aufrufe von **SQLGetPrivateProfileString** und **SQLWritePrivateProfileString** Verwenden des Konfigurationsmodus wissen, welcher Teil der Registrierung für verwendet werden.  
  
> [!CAUTION]  
>  **SQLSetConfigMode** aufgerufen werden soll, nur wenn erforderlich, wenn der Modus nicht ordnungsgemäß festgelegt ist, die ODBC-Installationsprogramms möglicherweise nicht ordnungsgemäß funktioniert.  
  
 **SQLSetConfigMode** stellt eine direkte registrierungsänderung, der den Konfigurationsmodus zu wechseln. Dies ist abgesehen von der Vorgang des Änderns des Konfigurationsmodus durch einen Aufruf von **SQLConfigDataSource**. Ein Aufruf von **SQLConfigDataSource** legt den Konfigurationsmodus zu wechseln, Benutzer und System-DSNs zu unterscheiden, wenn Sie einen DSN zu ändern. Vor der Rückgabe, **SQLConfigDataSource** den Konfigurationsmodus auf BOTHDSN zurückgesetzt.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Erstellen einer Datenquelle|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle mit einer Zeichenfolge oder eines Dialogfelds Verbindungsdialogfeld|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Abrufen des Konfigurationsmodus|[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|
