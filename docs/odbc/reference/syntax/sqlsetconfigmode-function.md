---
title: SQLSetConfigMode-Funktion | Microsoft Docs
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
ms.openlocfilehash: c36da48fa1493f61131d23a07f7a820b67ebac82
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293280"
---
# <a name="sqlsetconfigmode-function"></a>SQLSetConfigMode-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLSetConfigMode** legt den Konfigurationsmodus fest, der angibt, wo sich der Odbc.ini-Eintrag mit DSN-Werten in den Systeminformationen befindet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Argumente  
 *wConfigMode*  
 [Eingabe] Der Installationskonfigurationsmodus (siehe "Kommentare"). Der Wert in *wConfigMode* kann wie:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetConfigMode** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Ungültige Parametersequenz|Das *wConfigMode-Argument* enthielt keine ODBC_USER_DSN, ODBC_SYSTEM_DSN oder ODBC_BOTH_DSN.|  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion wird verwendet, um festzulegen, wo sich die DSN-Werte von Odbc.ini in den Systeminformationen befinden. Wenn *wConfigMode* ODBC_USER_DSN ist, ist der DSN ein Benutzer-DSN und die Funktion liest aus dem Odbc.ini-Eintrag in HKEY_CURRENT_USER. Wenn es ODBC_SYSTEM_DSN ist, ist der DSN ein System-DSN und die Funktion liest aus dem Odbc.ini-Eintrag in HKEY_LOCAL_MACHINE. Wenn es ODBC_BOTH_DSN ist, wird HKEY_CURRENT_USER versucht, und wenn es fehlschlägt, wird HKEY_LOCAL_MACHINE verwendet.  
  
 Diese Funktion wirkt sich nicht auf **SQLCreateDataSource** und **SQLDriverConnect**aus. Der Konfigurationsmodus muss festgelegt werden, wenn ein Treiber aus der Registrierung liest, indem er **SQLGetPrivateProfileString** aufruft oder in die Registrierung schreibt, indem **er SQLWritePrivateProfileString**aufruft. Aufrufe von **SQLGetPrivateProfileString** und **SQLWritePrivateProfileString** verwenden den Konfigurationsmodus, um zu wissen, auf welchem Teil der Registrierung ausgeführt werden soll.  
  
> [!CAUTION]  
>  **SQLSetConfigMode** sollte nur aufgerufen werden, wenn dies erforderlich ist. Wenn der Modus nicht ordnungsgemäß eingestellt ist, funktioniert der ODBC Installer möglicherweise nicht ordnungsgemäß.  
  
 **SQLSetConfigMode** nimmt eine direkte Registrierungsänderung des Konfigurationsmodus vor. Dies ist abgesehen vom Prozess der Änderung des Konfigurationsmodus durch einen Aufruf von **SQLConfigDataSource**. Ein Aufruf von **SQLConfigDataSource** legt den Konfigurationsmodus fest, um Benutzer- und System-DSNs beim Ändern einer DSN zu unterscheiden. Vor der Rückkehr setzt **SQLConfigDataSource** den Konfigurationsmodus auf BOTHDSN zurück.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Erstellen einer Datenquelle|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle über eine Verbindungszeichenfolge oder ein Dialogfeld|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Abrufen des Konfigurationsmodus|[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|
