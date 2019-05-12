---
title: SQLSetEnvAttr-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetEnvAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetEnvAttr
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC]
ms.assetid: 0343241c-4b15-4d4b-aa2b-2e8ab5215cd2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 09e5483bd5d1a1e2cb7398ee73d456c46439893f
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65536297"
---
# <a name="sqlsetenvattr-function"></a>SQLSetEnvAttr-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLSetEnvAttr** legt diese fest, die Aspekte der Umgebungen zu steuern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLSetEnvAttr(  
     SQLHENV      EnvironmentHandle,  
     SQLINTEGER   Attribute,  
     SQLPOINTER   ValuePtr,  
     SQLINTEGER   StringLength);  
```  
  
## <a name="arguments"></a>Argumente  
 *EnvironmentHandle*  
 [Eingabe] Umgebungshandles.  
  
 *Attribut*  
 [Eingabe] Attribut, das festgelegt wird, aufgeführt in "Kommentare".  
  
 *ValuePtr*  
 [Eingabe] Zeiger auf den Wert zugeordnet werden *Attribut*. Abhängig vom Wert *Attribut*, *ValuePtr* wird ein 32-Bit-Ganzzahl-Wert sein, oder zeigen Sie auf eine Null-terminierte Zeichenfolge.  
  
 *StringLength*  
 [Eingabe] Wenn *ValuePtr* zeigt auf eine Zeichenfolge oder ein binärer Puffer, in dieses Argument muss die Länge des **ValuePtr*. Für Zeichenfolgendaten sollte dieses Argument die Anzahl der Bytes in der Zeichenfolge enthalten.  
  
 Wenn *ValuePtr* ist eine ganze Zahl, *StringLength* wird ignoriert.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetEnvAttr** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_ENV und *behandeln* von *EnvironmentHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLSetEnvAttr** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben. Wenn ein Umgebungsattribut mit ein Treiber nicht unterstützt wird, kann der Fehler nur während der Dauer der Verbindung zurückgegeben werden.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Der Treiber nicht den Wert im angegebenen *ValuePtr* und einen ähnlichen Wert ersetzt. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY009|Ungültige Verwendung eines null-Zeiger|Das Attributargument identifiziert ein Umgebungsattribut, die einen Zeichenfolgenwert erforderlich und die *ValuePtr* Argument wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) für ein Verbindungshandle zugeordnet wurde *EnvironmentHandle*.<br /><br /> (DM) **SQL_ATTR_ODBC_VERSION** wurde nicht festgelegt wurde, mit **SQLSetEnvAttr** und *Attribut* ist nicht gleich **SQL_ATTR_ODBC_VERSION**. Sie müssen nicht festzulegende **SQL_ATTR_ODBC_VERSION** explizit bei der Verwendung von **SQLAllocHandleStd**.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY024|Ungültiger Attributwert|Berücksichtigung des angegebenen *Attribut* Wert in wurde ein ungültiger Wert angegeben *ValuePtr*.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|Die *StringLength* Argument war kleiner als 0, aber nicht SQL_NTS.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|(DM) der Wert für das Argument angegebene *Attribut* war nicht gültig für die Version von ODBC, die vom Treiber unterstützt werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Der angegebene Wert für das Argument *Attribut* wurde ein gültiges Attribut des ODBC-Umgebung aus, für die ODBC-Version vom Treiber unterstützt werden, jedoch wurde vom Treiber nicht unterstützt.<br /><br /> (DM) die *Attribut* Argument war SQL_ATTR_OUTPUT_NTS, und *ValuePtr* wurde SQL_FALSE.|  
  
## <a name="comments"></a>Kommentare  
 Kann eine Anwendung aufrufen **SQLSetEnvAttr** nur dann, wenn keine Verbindungshandle in der Umgebung zugeordnet ist. Alle Umgebungsattribute, die von der Anwendung für die Umgebung wurde erfolgreich festgelegt bleiben, bis **SQLFreeHandle** in der Umgebung aufgerufen wird. Mehr als ein Umgebungshandle kann gleichzeitig zugeordnet werden, in ODBC 3.*.x*.  
  
 Legen Sie das Format der Informationen über *ValuePtr* hängt von der angegebenen *Attribut*. **SQLSetEnvAttr** Attributinformationen in einem von zwei verschiedenen Formaten akzeptiert: eine Null-terminierte Zeichenfolge oder einen 32-Bit-Ganzzahl-Wert. Das Format der einzelnen wird in seine Beschreibung aufgeführt.  
  
 Keine Treiber-spezifische Umgebungsattribute sind vorhanden.  
  
 Verbindungsattribute können nicht festgelegt werden, durch einen Aufruf von **SQLSetEnvAttr**. Dies erledigen möchte SQLSTATE HY092 zurück (Attribut/Optionsbezeichner ungültig).  
  
|*Attribut*|*ValuePtr* Inhalt|  
|-----------------|-------------------------|  
|SQL_ATTR_CONNECTION_POOLING (ODBC 3.8)|Eine 32-Bit-SQLUINTEGER-Wert, der aktiviert oder deaktiviert die Verbindungspooling auf der Umgebungsebene. Die folgenden Werte werden verwendet:<br /><br /> SQL_CP_OFF = Verbindung zum Verbindungspooling deaktiviert ist. Dies ist die Standardeinstellung.<br /><br /> SQL_CP_ONE_PER_DRIVER = ein einzelnes des Verbindungspools wird für jeden Treiber unterstützt. Jede Verbindung in einem Pool ist ein Treiber zugeordnet.<br /><br /> SQL_CP_ONE_PER_HENV = eine einzelne Verbindungspools für jede Umgebung unterstützt wird. Jede Verbindung in einem Pool ist eine Umgebung zugeordnet.<br /><br /> SQL_CP_DRIVER_AWARE = verwendet die Verbindungspool Awareness-Funktion des Treibers, sofern diese verfügbar ist. Wenn der Treiber die Verbindung-Pool Awareness nicht unterstützt, SQL_CP_DRIVER_AWARE wird ignoriert, und SQL_CP_ONE_PER_HENV wird verwendet. Weitere Informationen finden Sie unter [Treiberfähiges Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md). In einer Umgebung, in dem einige Treiber unterstützen und einige Treiber unterstützen keine Verbindungspool Unterstützung, SQL_CP_DRIVER_AWARE können die Verbindungspool Awareness-Funktion auf die Treiber unterstützt, aber dies ist äquivalent zum Einstellung aus, um SQL_CP_ONE_PER_HENV auf Treiber, die Connection-Pool Awareness-Feature nicht unterstützen.<br /><br /> Verbindungs-pooling aktiviert ist, durch den Aufruf **SQLSetEnvAttr** Attributs SQL_ATTR_CONNECTION_POOLING SQL_CP_ONE_PER_DRIVER oder SQL_CP_ONE_PER_HENV festlegen. Dieser Aufruf muss vorgenommen werden, bevor die Anwendung die freigegebene Umgebung weist pooling ist für die Verbindung aktiviert werden. Das Umgebungshandle im Aufruf von **SQLSetEnvAttr** ist auf Null gesetzt, wodurch SQL_ATTR_CONNECTION_POOLING ein Attribut auf Prozessebene. Wenn Verbindungspooling aktiviert ist, weist die Anwendung dann eine implizite freigegebene Umgebung durch Aufrufen von **SQLAllocHandle** mit der *InputHandle* -Argument auf SQL_HANDLE_ENV auf festgelegt.<br /><br /> Nach dem Verbindungs-pooling aktiviert wurde, und eine freigegebene Umgebung für eine Anwendung ausgewählt wurde, SQL_ATTR_CONNECTION_POOLING kann nicht zurückgesetzt werden, für die jeweilige Umgebung, da **SQLSetEnvAttr** aufgerufen wird und eine null-Umgebung Behandeln Sie, wenn dieses Attribut festlegen. Wenn dieses Attribut festgelegt ist, während die Verbindungspooling auf einer freigegebenen Umgebung bereits aktiviert ist, beeinflusst das Attribut nur freigegebene Umgebungen, die anschließend zugeordnet sind.<br /><br /> Es ist auch möglich, um Verbindungspooling in einer Umgebung zu aktivieren. Beachten Sie Folgendes zum Verbindungspooling für Umgebung:<br /><br /> – Aktivieren von Verbindungspooling in einem NULL-Handle ist ein auf Prozessebene-Attribut. Anschließend zugeordnete Umgebungen werden einer freigegebenen Umgebung aus, und übernimmt die Einstellung Verbindungspooling auf Prozessebene.<br />: Nachdem Sie eine Umgebung zugeordnet ist, kann eine Anwendung weiterhin die verbindungspooleinstellung ändern.<br />– Wenn Umgebung Verbindungspooling aktiviert ist, und die Verbindung-Treiber verwendet Treiber Verbindungspooling, wird die Umgebung pooling Einstellung.<br /><br /> SQL_ATTR_CONNECTION_POOLING wird innerhalb des Treiber-Managers implementiert. Ein Treiber muss es sich nicht um SQL_ATTR_CONNECTION_POOLING zu implementieren. ODBC 2.0 und 3.0-Anwendungen können dieses Umgebungsattribut festlegen.<br /><br /> Weitere Informationen finden Sie unter [ODBC-Verbindungspooling](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md).|  
|SQL_ATTR_CP_MATCH (ODBC 3.0)|Ein 32-Bit-SQLUINTEGER-Wert, der bestimmt, wie eine Verbindung aus einem Verbindungspool ausgewählt wird. Wenn **SQLConnect** oder **SQLDriverConnect** wird aufgerufen, der Treiber-Manager bestimmt, welche Verbindung aus dem Pool wiederverwendet wird. Der Treiber-Manager versucht die Verbindungsoptionen in den Aufruf und die Verbindungsattribute, die von der Anwendung für die Schlüsselwörter und Verbindungsattribute der Verbindungen im Pool festlegen. Der Wert dieses Attributs bestimmt die Genauigkeit der übereinstimmenden Kriterien.<br /><br /> Die folgenden Werte werden verwendet, um den Wert dieses Attributs festzulegen:<br /><br /> SQL_CP_STRICT_MATCH = nur Verbindungen, die die Verbindungsoptionen im Aufruf exakt übereinstimmen und die Verbindung, die Attribute festgelegt werden, von der Anwendung wiederverwendet werden. Dies ist die Standardeinstellung.<br /><br /> SQL_CP_RELAXED_MATCH = Verbindungen mit passenden Verbindungszeichenfolge-Schlüsselwörter verwendet werden können. Schlüsselwörtern übereinstimmen, aber nicht alle Verbindungsattribute müssen übereinstimmen.<br /><br /> Weitere Informationen dazu, wie der Treiber-Manager die Übereinstimmung beim Herstellen einer Verbindung zu einer in einem Pool zusammengefasste Verbindung ausführt, finden Sie unter [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md). Weitere Informationen zum Verbindungspooling finden Sie unter [ODBC-Verbindungspooling](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md).|  
|SQL_ATTR_ODBC_VERSION (ODBC 3.0)|Eine 32-Bit-Ganzzahl, die bestimmt, ob bestimmte Funktionen ODBC 2. weist *.x* Verhalten oder ODBC 3.*.x* Verhalten. Die folgenden Werte werden verwendet, um den Wert dieses Attributs festzulegen:<br /><br /> SQL_OV_ODBC3_80 = der Treiber-Manager und Verhalten von Treibern die folgenden ODBC 3.8-Anhang:<br /><br /> -Der Treiber gibt zurück, und ODBC 3. erwartet. *x* Codes für Date, Time und Timestamp.<br />-Der Treiber gibt ODBC 3. zurück. *x* SQLSTATE-codes bei **SQLError**, **SQLGetDiagField**, oder **SQLGetDiagRec** aufgerufen wird.<br />– Die *CatalogName* Argument in einem Aufruf von **SQLTables** akzeptiert ein Suchmuster.<br />-Der Treiber-Manager unterstützt die C-Typ datenerweiterung. Weitere Informationen zu Typ C die datenerweiterung, finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).<br /><br /> Weitere Informationen finden Sie unter [Neuigkeiten in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).<br /><br /> SQL_OV_ODBC3 = der Treiber-Manager und Anhang der Treiber die folgenden ODBC 3.*.x* Verhalten:<br /><br /> -Der Treiber gibt zurück, und erwartet, dass ODBC 3.*.x* Codes für Date, Time und Timestamp.<br />-Der Treiber gibt ODBC 3.*.x* SQLSTATE-codes bei **SQLError**, **SQLGetDiagField**, oder **SQLGetDiagRec** aufgerufen wird.<br />– Die *CatalogName* Argument in einem Aufruf von **SQLTables** akzeptiert ein Suchmuster.<br />-Der Treiber-Manager unterstützt keine C-Typ datenerweiterung.<br /><br /> SQL_OV_ODBC2 = der Treiber-Manager und Anhang der Treiber die folgenden ODBC 2.*.x* Verhalten. Dies ist besonders nützlich für eine ODBC 2.*.x* Anwendung mit einer ODBC 3.*.x* Treiber.<br /><br /> -Der Treiber gibt zurück, und erwartet, dass ODBC 2.*.x* Codes für Date, Time und Timestamp.<br />-Der Treiber gibt ODBC 2.*.x* SQLSTATE-codes bei **SQLError**, **SQLGetDiagField**, oder **SQLGetDiagRec** aufgerufen wird.<br />– Die *CatalogName* Argument in einem Aufruf von **SQLTables** akzeptiert kein Suchmuster.<br />-Der Treiber-Manager unterstützt keine C-Typ datenerweiterung.<br /><br /> Eine Anwendung muss dieses Umgebungsattribut festgelegt, bevor sie eine Funktion aufruft, die ein Argument SQLHENV oder SQLSTATE HY010 gibt der Aufruf zurück (Sequenzfehler funktionieren). Es ist treiberspezifisch, ob zusätzliches Verhalten für diese Umgebung Flags vorhanden ist.<br /><br /> -Weitere Informationen finden Sie unter [Deklarieren der ODBC-Version der Anwendung](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) und [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md).|  
|SQL_ATTR_OUTPUT_NTS (ODBC 3.0)|Eine 32-Bit-Ganzzahl, die bestimmt, wie der Treiber Zeichenfolgendaten zurückgegeben wird. Wenn SQL_TRUE, den Treiber Zeichenfolgendaten Null-terminierte zurückgibt. Wenn SQL_FALSE, den Treiber keine Null-terminierte Zeichenfolgendaten zurückgibt.<br /><br /> Dieses Attribut standardmäßig auf SQL_TRUE. Ein Aufruf von **SQLSetEnvAttr** auf festgelegt ist, dass SQL_TRUE gibt SQL_SUCCESS zurück. Ein Aufruf von **SQLSetEnvAttr** zu SQL_FALSE gibt SQL_ERROR zurück, und SQLSTATE HYC00 festlegen (optionales Feature nicht implementiert).|  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ein Handle zuordnen|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Die Einstellung ein Umgebungsattribut zurückgeben|[SQLGetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [What's New in ODBC 3.8 (Neues in ODBX 3.8)](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
