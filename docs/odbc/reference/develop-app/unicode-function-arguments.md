---
title: Unicode-Funktionsargumente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 40ef9f63345572b5613942c1174ceeecadd146ee
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529739"
---
# <a name="unicode-function-arguments"></a>Unicode-Funktionsargumente
Der Treiber-Manager von ODBC 3,5 (oder höher) unterstützt sowohl ANSI-als auch Unicode-Versionen aller Funktionen, die Zeiger auf Zeichen folgen oder SQLPOINTER in ihren Argumenten akzeptieren. Die Unicode-Funktionen werden als Funktionen implementiert (mit einem Suffix von *W*), nicht als Makros. Die ANSI-Funktionen (die mit oder ohne *Suffix von aufgerufen*werden können) sind identisch mit den aktuellen ODBC-API-Funktionen.  
  
## <a name="remarks"></a>Bemerkungen  
 Bei Unicode-Funktionen, die immer Zeichen folgen oder Längen Argumente zurückgeben oder annehmen, werden die Argumente als Anzahl von Zeichen übergebenen. Für Funktionen, die Längen Informationen für Serverdaten zurückgeben, werden die Anzeige Größe und die Genauigkeit als Anzahl von Zeichen beschrieben. Wenn eine Länge (Übertragungs Größe der Daten) auf Zeichen folgen-oder nicht-Zeichen folgen Daten verweisen kann, wird die Länge in oktetelängen beschrieben. **Sqlgetinfow** nimmt z. b. immer noch die Länge als Anzahl von Bytes an, **sqlexecdirectw** verwendet jedoch die Anzahl von Zeichen.  
  
 Anzahl von Zeichen bezieht sich auf die Anzahl von Bytes (Oktette) für ANSI-Funktionen und die Anzahl von WCHAR (16-Bit-Wörtern) für Unicode-Funktionen. Insbesondere eine Doppelbyte-Zeichenfolge (Double-Byte Character Sequence, DBCS) oder eine multibytezeichensequenz (MBCS) kann aus mehreren Bytes bestehen. Eine UTF-16-Unicode-Zeichenfolge kann aus mehreren WCHARs bestehen.  
  
 Im folgenden finden Sie eine Liste der ODBC-API-Funktionen, die sowohl Unicode (W)-als auch ANSI (a)-Versionen unterstützen:  
  
|||  
|-|-|  
|**SQLBrowseConnect**|**SQLGetDiagRec**|  
|**SQLColAttribute**|**SQLGetInfo**|  
|**SQLColAttributes**|**'SQLGetStmtAttr'**|  
|**SQLColumnPrivileges**|**SQLGetTypeInfo**|  
|**SQLColumns**|**SQLNativeSQL**|  
|**SQLConnect**|**SQLPrepare**|  
|**SQLDataSources**|**SQLPrimaryKeys**|  
|**SQLDescribeCol**|**SQLProcedureColumns**|  
|**SQLDriverConnect**|**'SQLProcedures'**|  
|**SQLDrivers**|**SQLSetConnectAttr**|  
|**SQLError**|**SQLSetConnectOption**|  
|**SQLExecDirect**|**SQLSetCursorName**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**SQLGetConnectOption**|**'SQLSpecialColumns'**|  
|**SQLGetCursorName**|**'SQLStatistics'**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
|**SQLGetDiagField**||  
  
 Im folgenden finden Sie eine Liste der ODBC-Installer-und ODBC-Konvertierungs Funktionen, die sowohl Unicode (W)-als auch ANSI (a)-Versionen unterstützen:  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**Sqlinstalldrivermanager**|  
|**Sqlkreatedatasource**|**Sqlinstallererror**|  
|**Sqldatasourceto Driver**|**SQLInstallODBC**|  
|**Sqldriverflidatasource**|**Sqllesfiledsn**|  
|**Sqlgetavailabledrivers**|**Sqlremovedsnfromini**|  
|**Sqlgetinstalleddrivers**|**Sqlvaliddsn**|  
|**Sqlgettranslator**|**Sqlschreitedsnder ini**|  
|**SQLInstallDriver**||  
  
> [!NOTE]
>  Als veraltet markierte Funktionen werden Unicode-zu-ANSI-Mapping unterstützt, da der Treiber-Manager von ODBC *3.* x das erneute Kompilieren von ODBC *2. x* -Anwendungen mit dem Unicode- **#define**unterstützt.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Unicode-Anwendungen](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Unicode-Treiber](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [Funktionszuordnung im Treiber-Manager](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
