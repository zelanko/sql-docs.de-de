---
title: SQLGetEnvAttr-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetEnvAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetEnvAttr
helpviewer_keywords:
- SQLGetEnvAttr function [ODBC]
ms.assetid: 01f4590f-427a-4280-a1c3-18de9f7d86c1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70fe1ca95f5160f801eaf3528e625116705eda6d
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53203809"
---
# <a name="sqlgetenvattr-function"></a>SQLGetEnvAttr-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standardkompatibilität: ISO-92  
  
 **Zusammenfassung**  
 **SQLGetEnvAttr** die aktuelle Einstellung eines Umgebung-Attributs zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLGetEnvAttr(  
     SQLHENV        EnvironmentHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *EnvironmentHandle*  
 [Eingabe] Umgebungshandles.  
  
 *Attribut*  
 [Eingabe] Attribut, das abgerufen werden.  
  
 *ValuePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem den aktuellen Wert des Attributs gemäß zurückgegeben *Attribut*.  
  
 Wenn *ValuePtr* NULL ist, *StringLengthPtr* gibt die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer, der auf zurückgegeben *ValuePtr*.  
  
 *BufferLength*  
 [Eingabe] Wenn *ValuePtr* zeigt auf eine Zeichenfolge, in dieses Argument muss die Länge des \* *ValuePtr*. Wenn \* *ValuePtr* ist eine ganze Zahl, *Pufferlänge* wird ignoriert. Wenn  *\*ValuePtr* ist eine Unicodezeichenfolge (beim Aufrufen von **SQLGetEnvAttrW**), wird die *Pufferlänge* Argument muss eine gerade Zahl sein. Wenn Sie den Wert des Attributs nicht als eine Zeichenfolge ist *Pufferlänge* wird nicht verwendet.  
  
 *StringLengthPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen) zurückgegeben. verfügbar für die zurückzugebenden in  *\*ValuePtr*. Wenn *ValuePtr* ist ein null-Zeiger wird keine Länge zurückgegeben. Wenn Sie den Wert des Attributs ist eine Zeichenfolge und die Anzahl der Bytes, die für die Rückgabe verfügbar ist, größer als oder gleich *Pufferlänge*, die Daten in \* *ValuePtr* auf abgeschnitten  *BufferLength* abzüglich der Länge des ein Null-Terminierungszeichen und Null-terminiert ist vom Treiber.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA zurückgibt, wird SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetEnvAttr** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_ENV und *behandeln* von *EnvironmentHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLGetEnvAttr** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Die Daten im zurückgegebenen \* *ValuePtr* wurde abgeschnitten, um werden *Pufferlänge* minus der Null-Terminierungszeichen. Die Länge des Werts den ungekürzten Zeichenfolge wird zurückgegeben, **StringLengthPtr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) **SQL_ATTR_ODBC_VERSION** wurde noch nicht festgelegt wurde über **SQLSetEnvAttr**. Sie müssen nicht festzulegende **SQL_ATTR_ODBC_VERSION** explizit bei der Verwendung von **SQLAllocHandleStd**.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|Der angegebene Wert für das Argument *Attribut* war nicht gültig für die Version von ODBC, die vom Treiber unterstützt werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Der angegebene Wert für das Argument *Attribut* wurde ein gültiges Attribut des ODBC-Umgebung aus, für die ODBC-Version vom Treiber unterstützt werden, jedoch wurde vom Treiber nicht unterstützt.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber entspricht der *EnvironmentHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Eine Liste der Attribute, finden Sie unter [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Keine Treiber-spezifische Umgebungsattribute sind vorhanden. Wenn *Attribut* gibt an, ein Attribut, das eine Zeichenfolge zurückgibt, *ValuePtr* muss ein Zeiger auf einen Puffer, in dem die Zeichenfolge zurück. Die maximale Länge der Zeichenfolge, die Null-Terminierung Byte, einschließlich werden *Pufferlänge* Bytes.  
  
 **SQLGetEnvAttr** kann zu einem beliebigen Zeitpunkt zwischen der Zuordnung und die Freigabe des ein Umgebungshandle aufgerufen werden. Alle Umgebungsattribute, die von der Anwendung für die Umgebung wurde erfolgreich festgelegt bleiben, bis **SQLFreeHandle** aufgerufen wird, auf die *EnvironmentHandle* mit einer *HandleType*SQL_HANDLE_ENV auf. Mehr als ein Umgebungshandle kann gleichzeitig zugeordnet werden, in ODBC 3.*.x*. Ein Umgebungsattribut für eine Umgebung ist nicht betroffen, wenn eine andere Umgebung zugeordnet wurde.  
  
> [!NOTE]
>  SQL_ATTR_OUTPUT_NTS umgebungsattributs wird von den Standards entsprechende Anwendungen unterstützt. Wenn **SQLGetEnvAttr** aufgerufen wird, wird die ODBC 3.*.x* -Treiber-Manager gibt SQL_TRUE immer für dieses Attribut zurück. SQL_ATTR_OUTPUT_NTS kann auf SQL_TRUE festgelegt werden, nur durch einen Aufruf von **SQLSetEnvAttr**.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Die Einstellung ein Verbindungsattribut zurückgeben|[SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Die Einstellung für ein Anweisungsattribut zurückgeben|[SQLGetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|Ein Verbindungsattribut festlegen|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Ein Umgebungsattribut festlegen|[SQLSetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Wenn eine Anweisungsattribut|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
