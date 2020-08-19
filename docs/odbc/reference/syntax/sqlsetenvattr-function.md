---
description: SQLSetEnvAttr-Funktion
title: Sqlsettenvattr-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetEnvAttr
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetEnvAttr
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC]
ms.assetid: 0343241c-4b15-4d4b-aa2b-2e8ab5215cd2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f535c860df212c708f11339165b2d05d4a79647
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421114"
---
# <a name="sqlsetenvattr-function"></a>SQLSetEnvAttr-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLSetEnvAttr** legt Attribute fest, die Aspekte von Umgebungen steuern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLSetEnvAttr(  
     SQLHENV      EnvironmentHandle,  
     SQLINTEGER   Attribute,  
     SQLPOINTER   ValuePtr,  
     SQLINTEGER   StringLength);  
```  
  
## <a name="arguments"></a>Argumente  
 *Environment-THandle*  
 Der Umgebungs Handle.  
  
 *Attribut*  
 Der Das festzulegende Attribut, aufgelistet in "comments".  
  
 *ValuePtr*  
 Der Zeiger auf den Wert, der dem *Attribut*zugeordnet werden soll. Abhängig vom Wert des *Attributs*ist *ValuePtr* ein ganzzahliger Wert von 32 Bit oder zeigt auf eine auf NULL endende Zeichenfolge.  
  
 *StringLength*  
 Der Wenn *ValuePtr* auf eine Zeichenfolge oder einen binären Puffer verweist, sollte dieses Argument die Länge von **ValuePtr*aufweisen. Für Zeichen folgen Daten sollte dieses Argument die Anzahl der Bytes in der Zeichenfolge enthalten.  
  
 Wenn *ValuePtr* eine ganze Zahl ist, wird *StringLength* ignoriert.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlsettenvattr** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_ENV und einem *handle* von *environmenthandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **sqlsettenvattr** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist. Wenn ein Treiber kein Umgebungs Attribut unterstützt, kann der Fehler nur während der Verbindungszeit zurückgegeben werden.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01s02 entsprechen|Optionswert geändert|Der Treiber hat den in *ValuePtr* angegebenen Wert nicht unterstützt und ersetzt einen ähnlichen Wert. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das Attribut Argument hat ein Umgebungs Attribut identifiziert, das einen Zeichen folgen Wert erforderte, und das *ValuePtr* -Argument war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) ein Verbindungs Handle wurde auf Environment- *THandle*zugeordnet.<br /><br /> (DM) **SQL_ATTR_ODBC_VERSION** nicht mit **SQLSetEnvAttr** festgelegt wurde und das *Attribut* nicht gleich **SQL_ATTR_ODBC_VERSION**ist. Sie müssen **SQL_ATTR_ODBC_VERSION** nicht explizit festlegen, wenn Sie **sqlzuzugchandlestd**verwenden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY024|Ungültiger Attribut Wert|Bei Angabe des angegebenen *Attribut* Werts wurde in *ValuePtr*ein ungültiger Wert angegeben.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|Das *StringLength* -Argument war kleiner als 0 (null), war aber nicht SQL_NTS.|  
|HY092|Ungültiger Attribut/Options Bezeichner|(DM) der für das Argument *Attribut* angegebene Wert war für die vom Treiber unterstützte ODBC-Version ungültig.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Der für das Argument- *Attribut* angegebene Wert war ein gültiges ODBC-Umgebungs Attribut für die Version von ODBC, die vom Treiber unterstützt wird, jedoch nicht vom Treiber unterstützt wurde.<br /><br /> (DM) das *Attribut* Argument wurde SQL_ATTR_OUTPUT_NTS, und *ValuePtr* wurde SQL_FALSE.|  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung kann **SQLSetEnvAttr** nur dann aufzurufen, wenn kein Verbindungs Handle in der Umgebung zugeordnet ist. Alle Umgebungs Attribute, die von der Anwendung für die Umgebung erfolgreich festgelegt wurden, bleiben so lange erhalten, bis **SQLFreeHandle** für die Umgebung aufgerufen wird. In ODBC *3. x*kann gleichzeitig mehr als ein Umgebungs Handle zugeordnet werden.  
  
 Das Format der Informationen, die über *ValuePtr* festgelegt werden, hängt vom angegebenen *Attribut*ab. **Sqlsertenvattr** akzeptiert Attributinformationen in einem von zwei verschiedenen Formaten: einer auf NULL endenden Zeichenfolge oder einem ganzzahligen Wert von 32 Bit. Das Format der einzelnen wird in der Beschreibung des Attributs angegeben.  
  
 Es sind keine treiberspezifischen Umgebungs Attribute vorhanden.  
  
 Verbindungs Attribute können nicht durch einen **SQLSetEnvAttr**-Befehl festgelegt werden. Bei diesem Vorgang wird SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurückgegeben.  
  
|*Attribut*|*ValuePtr* -Inhalt|  
|-----------------|-------------------------|  
|SQL_ATTR_CONNECTION_POOLING (ODBC 3,8)|Ein 32-Bit-SQLUINTEGER-Wert, der das Verbindungspooling auf Umgebungs Ebene aktiviert oder deaktiviert. Die folgenden Werte werden verwendet:<br /><br /> SQL_CP_OFF = Verbindungspooling ist deaktiviert. Dies ist die Standardoption.<br /><br /> SQL_CP_ONE_PER_DRIVER = ein einzelner Verbindungspool wird für jeden Treiber unterstützt. Jede Verbindung in einem Pool ist einem Treiber zugeordnet.<br /><br /> SQL_CP_ONE_PER_HENV = für jede Umgebung wird ein einzelner Verbindungspool unterstützt. Jede Verbindung in einem Pool ist einer Umgebung zugeordnet.<br /><br /> SQL_CP_DRIVER_AWARE = verwenden Sie die Funktion für die Funktion zum Verwenden des Verbindungspools des Treibers, sofern verfügbar. Wenn der Treiber keine Informationen zum Verbindungspool unterstützt, wird SQL_CP_DRIVER_AWARE ignoriert und SQL_CP_ONE_PER_HENV verwendet. Weitere Informationen finden Sie unter [Treiber fähiges Verbindungs Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md). In einer Umgebung, in der einige Treiber unterstützen, und einige Treiber keine Informationen zum Verbindungspool unterstützen, können SQL_CP_DRIVER_AWARE das Feature für die Verbindungspool Erkennung für diese unterstützenden Treiber aktivieren, aber es entspricht dem Festlegen von, um auf die Treiber zu SQL_CP_ONE_PER_HENV, die die Funktion zur Erkennung von Verbindungspools nicht unterstützen.<br /><br /> Das Verbindungspooling wird durch Aufrufen von **SQLSetEnvAttr** aktiviert, um das SQL_ATTR_CONNECTION_POOLING-Attribut auf SQL_CP_ONE_PER_DRIVER oder SQL_CP_ONE_PER_HENV festzulegen. Dieser Rückruf muss erfolgen, bevor die Anwendung die freigegebene Umgebung zuordnet, für die das Verbindungspooling aktiviert werden soll. Das Umgebungs Handle im-Befehl von **SQLSetEnvAttr** wird auf NULL festgelegt, wodurch SQL_ATTR_CONNECTION_POOLING ein Attribut auf Prozessebene ist. Nachdem das Verbindungspooling aktiviert ist, ordnet die Anwendung eine implizite freigegebene Umgebung zu, indem **sqlzuordchandle** aufgerufen wird, wobei das *InputHandle* -Argument auf SQL_HANDLE_ENV festgelegt ist.<br /><br /> Nachdem das Verbindungspooling aktiviert und eine freigegebene Umgebung für eine Anwendung ausgewählt wurde, können SQL_ATTR_CONNECTION_POOLING für diese Umgebung nicht zurückgesetzt werden, da **SQLSetEnvAttr** beim Festlegen dieses Attributs mit einem NULL-Umgebungs Handle aufgerufen wird. Wenn dieses Attribut festgelegt wird, während das Verbindungspooling bereits in einer freigegebenen Umgebung aktiviert ist, wirkt sich das Attribut nur auf freigegebene Umgebungen aus, die später zugeordnet werden.<br /><br /> Es ist auch möglich, das Verbindungspooling für eine Umgebung zu aktivieren. Beachten Sie Folgendes zum Verbindungspooling in der Umgebung:<br /><br /> -Das Aktivieren des Verbindungspooling für ein NULL-Handle ist ein Attribut auf Prozessebene. Anschließend werden zugeordnete Umgebungen als freigegebene Umgebung verwendet und erben die Einstellung für das Verbindungspooling auf Prozessebene.<br />-Nachdem eine Umgebung zugewiesen wurde, kann eine Anwendung ihre Verbindungspool Einstellung weiterhin ändern.<br />: Wenn das Umgebungs Verbindungspooling aktiviert ist und der Treiber der Verbindung das Treiber Pooling verwendet, wird das Umgebungs Pooling bevorzugt.<br /><br /> SQL_ATTR_CONNECTION_POOLING ist im Treiber-Manager implementiert. Ein Treiber muss SQL_ATTR_CONNECTION_POOLING nicht implementieren. ODBC 2,0-und 3,0-Anwendungen können dieses Umgebungs Attribut festlegen.<br /><br /> Weitere Informationen finden Sie unter [ODBC-Verbindungspooling](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md).|  
|SQL_ATTR_CP_MATCH (ODBC 3,0)|Ein 32-Bit-SQLUINTEGER-Wert, der bestimmt, wie eine Verbindung aus einem Verbindungspool ausgewählt wird. Wenn **SQLCONNECT** oder **SQLDriverConnect** aufgerufen wird, bestimmt der Treiber-Manager, welche Verbindung aus dem Pool wieder verwendet wird. Der Treiber-Manager versucht, die Verbindungsoptionen im-Rückruf und die von der Anwendung festgelegten Verbindungs Attribute mit den Schlüsselwörtern und Verbindungs Attributen der Verbindungen im Pool abzugleichen. Der Wert dieses Attributs bestimmt den Genauigkeits Grad der Übereinstimmungs Kriterien.<br /><br /> Die folgenden Werte werden verwendet, um den Wert dieses Attributs festzulegen:<br /><br /> SQL_CP_STRICT_MATCH = nur Verbindungen, die exakt mit den Verbindungsoptionen im-Rückruf übereinstimmen, und die von der Anwendung festgelegten Verbindungs Attribute werden wieder verwendet. Dies ist die Standardoption.<br /><br /> SQL_CP_RELAXED_MATCH = Verbindungen mit übereinstimmenden Schlüsselwörtern für Verbindungs Zeichenfolgen können verwendet werden. Schlüsselwörter müssen abgeglichen werden, aber nicht alle Verbindungs Attribute müssen entsprechen.<br /><br /> Weitere Informationen zum Durchführen der Entsprechung durch den Treiber-Manager beim Herstellen einer Verbindung mit einer gepoolten Verbindung finden Sie unter [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md). Weitere Informationen zum Verbindungspooling finden Sie unter [ODBC-Verbindungspooling](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md).|  
|SQL_ATTR_ODBC_VERSION (ODBC 3,0)|Eine 32-Bit-Ganzzahl, die bestimmt, ob eine bestimmte Funktionalität das ODBC *2. x* -Verhalten oder das ODBC *3. x* -Verhalten aufweist. Die folgenden Werte werden verwendet, um den Wert dieses Attributs festzulegen:<br /><br /> SQL_OV_ODBC3_80 = der Treiber-Manager und der Treiber weisen das folgende ODBC 3,8-Verhalten auf:<br /><br /> -Der Treiber gibt zurück und erwartet ODBC *3. x* -Codes für Date, Time und TIMESTAMP.<br />-Der Treiber gibt ODBC *3. x* -SQLSTATE-Codes zurück, wenn **SQLError**, **SQLGetDiagField**oder **SQLGetDiagRec** aufgerufen wird.<br />-Das *CatalogName* -Argument in einem ' **SQLTables** '-Befehl akzeptiert ein Suchmuster.<br />-Der Treiber-Manager unterstützt die Erweiterbarkeit von C-Datentypen. Weitere Informationen zur Erweiterbarkeit von c-Datentypen finden Sie unter [c-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).<br /><br /> Weitere Informationen finden Sie unter [What es New in ODBC 3,8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).<br /><br /> SQL_OV_ODBC3 = der Treiber-Manager und der Treiber weisen das folgende ODBC *3. x* -Verhalten auf:<br /><br /> -Der Treiber gibt zurück und erwartet ODBC *3. x* -Codes für Date, Time und TIMESTAMP.<br />-Der Treiber gibt ODBC *3. x* -SQLSTATE-Codes zurück, wenn **SQLError**, **SQLGetDiagField**oder **SQLGetDiagRec** aufgerufen wird.<br />-Das *CatalogName* -Argument in einem ' **SQLTables** '-Befehl akzeptiert ein Suchmuster.<br />-Der Treiber-Manager bietet keine Unterstützung für die Erweiterbarkeit von C-Datentypen.<br /><br /> SQL_OV_ODBC2 = der Treiber-Manager und der Treiber weisen das folgende ODBC *2. x* -Verhalten auf. Dies ist besonders nützlich für eine ODBC *2. x* -Anwendung, die mit einem ODBC *3. x* -Treiber arbeitet.<br /><br /> -Der Treiber gibt zurück und erwartet ODBC *2. x* -Codes für Date, Time und TIMESTAMP.<br />-Der Treiber gibt ODBC *2. x* -SQLSTATE-Codes zurück, wenn **SQLError**, **SQLGetDiagField**oder **SQLGetDiagRec** aufgerufen wird.<br />-Das *CatalogName* -Argument in einem ' **SQLTables** '-Befehl akzeptiert kein Suchmuster.<br />-Der Treiber-Manager bietet keine Unterstützung für die Erweiterbarkeit von C-Datentypen.<br /><br /> Eine Anwendung muss dieses Umgebungs Attribut festlegen, bevor eine Funktion mit einem sqlhenv-Argument aufgerufen wird, oder der Aufruf gibt SQLSTATE HY010 (Funktions Sequenz Fehler) zurück. Es ist Treiber spezifisch, ob für diese Umgebungs Flags zusätzliches Verhalten vorhanden ist.<br /><br /> -Weitere Informationen finden Sie unter [Deklarieren der ODBC-Version der Anwendung](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) und [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md).|  
|SQL_ATTR_OUTPUT_NTS (ODBC 3,0)|Eine 32-Bit-Ganzzahl, die bestimmt, wie der Treiber Zeichen folgen Daten zurückgibt. Wenn SQL_TRUE, gibt der Treiber Zeichen folgen Daten zurück, die auf Null enden. Wenn SQL_FALSE, gibt der Treiber keine null-terminierten Zeichen folgen Daten zurück.<br /><br /> Dieses Attribut ist standardmäßig SQL_TRUE. Ein **SQLSetEnvAttr** -Befehl, um ihn auf SQL_TRUE festzulegen, gibt SQL_SUCCESS zurück. Ein **SQLSetEnvAttr** -Befehl, um ihn auf SQL_FALSE festzulegen, gibt SQL_ERROR und SQLSTATE HYC00 (optionales Feature nicht implementiert) zurück.|  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuordnen eines Handles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Zurückgeben der Einstellung eines Umgebungs Attributs|[SQLGetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Header Dateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Neuerungen in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
