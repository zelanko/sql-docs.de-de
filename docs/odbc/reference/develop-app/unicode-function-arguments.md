---
title: Unicode-Funktionsargumente | Microsoft Docs
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
ms.openlocfilehash: a25dd6fe0a77aad5c5ec9ba15eaf12bd2ec3fc18
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284290"
---
# <a name="unicode-function-arguments"></a>Unicode-Funktionsargumente
Der ODBC 3.5 (oder höher) Treiber-Manager unterstützt sowohl ANSI- als auch Unicode-Versionen aller Funktionen, die Zeiger auf Zeichenfolgen oder SQLPOINTER in ihren Argumenten akzeptieren. Die Unicode-Funktionen werden als Funktionen (mit dem Suffix *W*) und nicht als Makros implementiert. Die ANSI-Funktionen (die mit oder ohne Suffix *Von A*aufgerufen werden können) sind identisch mit den aktuellen ODBC-API-Funktionen.  
  
## <a name="remarks"></a>Bemerkungen  
 Unicode-Funktionen, die immer Zeichenfolgen oder Längenargumente zurückgeben oder verwenden, werden als Zeichenanzahl übergeben. Bei Funktionen, die Längeninformationen für Serverdaten zurückgeben, werden die Anzeigegröße und -genauigkeit in der Anzahl der Zeichen beschrieben. Wenn eine Länge (Übertragungsgröße der Daten) auf Zeichenfolgen- oder Nichtstringdaten verweisen kann, wird die Länge in Oktettlängen beschrieben. **SqlGetInfoW** nimmt z. B. immer noch die Länge als Anzahl von Bytes an, aber **SQLExecDirectW** verwendet Anzahl-zeichen.  
  
 Die Anzahl der Zeichen bezieht sich auf die Anzahl der Bytes (Oktette) für ANSI-Funktionen und die Anzahl der WCHAR (16-Bit-Wörter) für UNICODE-Funktionen. Insbesondere kann eine Doppelbyte-Zeichensequenz (DBCS) oder eine Multibyte-Zeichensequenz (MBCS) aus mehreren Bytes bestehen. Eine UTF-16 Unicode-Zeichenfolge kann aus mehreren WCHARs bestehen.  
  
 Im Folgenden finden Sie eine Liste der ODBC-API-Funktionen, die sowohl Unicode-Versionen (W) als auch ANSI (A)-Versionen unterstützen:  
  
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
|**Sqlerror**|**SQLSetConnectOption**|  
|**SQLExecDirect**|**SQLSetCursorName**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**SQLGetConnectOption**|**'SQLSpecialColumns'**|  
|**SQLGetCursorName**|**'SQLStatistics'**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
|**SQLGetDiagField**||  
  
 Im Folgenden finden Sie eine Liste der Funktionen ODBC Installer und ODBC Translator, die sowohl Unicode(W) als auch ANSI (A)-Versionen unterstützen:  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**SQLInstallDriverManager**|  
|**SQLCreateDataSource**|**SQLInstallerError**|  
|**SQLDataSourceToDriver**|**SQLInstallODBC**|  
|**SQLDriverToDataSource**|**SQLReadFileDSN**|  
|**SQLGetAvailableDrivers**|**SQLRemoveDSNFromINI**|  
|**SQLGetInstalledDrivers**|**SQLValidDSN**|  
|**SQLGetTranslator**|**SQLWriteDSNtoINI**|  
|**SQLInstallDriver**||  
  
> [!NOTE]
>  Veraltete Funktionen verfügen über Unicode-zu-ANSI-Zuordnungsunterstützung, da der ODBC *3.x* Driver Manager das Neukompilieren von ODBC *2.x-Anwendungen* mit dem UNICODE-#define unterstützt. **#define**  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Unicode-Anwendungen](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Unicode-Treiber](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [Funktionszuordnung im Treiber-Manager](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
