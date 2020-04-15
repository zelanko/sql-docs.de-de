---
title: SQLGetEnvAttr-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetEnvAttr
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLGetEnvAttr
helpviewer_keywords:
- SQLGetEnvAttr function [ODBC]
ms.assetid: 01f4590f-427a-4280-a1c3-18de9f7d86c1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 77cd24386a8eea6769aee59f3674b681c516d9ed
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285310"
---
# <a name="sqlgetenvattr-function"></a>SQLGetEnvAttr-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetEnvAttr** gibt die aktuelle Einstellung eines Umgebungsattributs zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetEnvAttr(  
     SQLHENV        EnvironmentHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *EnvironmentHandle*  
 [Eingabe] Umgebungshandle.  
  
 *Attribut*  
 [Eingabe] Attribut, das abgerufen werden soll.  
  
 *ValuePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem der aktuelle Wert des von *Attribut*angegebenen Attributs zurückgegeben werden soll.  
  
 Wenn *ValuePtr* NULL ist, gibt *StringLengthPtr* weiterhin die Gesamtzahl der Bytes (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten) zurück, auf die im Puffer von *ValuePtr*verwiesen wird.  
  
 *BufferLength*  
 [Eingabe] Wenn *ValuePtr* auf eine Zeichenfolge verweist, sollte \*dieses Argument die Länge von *ValuePtr*sein. Wenn \* *ValuePtr* eine ganze Zahl ist, wird *BufferLength* ignoriert. Wenn * \*ValuePtr* eine Unicode-Zeichenfolge ist (beim Aufrufen von **SQLGetEnvAttrW**), muss das *BufferLength-Argument* eine gerade Zahl sein. Wenn der Attributwert keine Zeichenfolge ist, wird *BufferLength* nicht verwendet.  
  
 *StringLengthPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes (mit Ausnahme des Null-Beendigungszeichens) zurückgegeben werden soll, die in * \*ValuePtr*zurückgegeben werden können. Wenn *ValuePtr* ein Nullzeiger ist, wird keine Länge zurückgegeben. Wenn der Attributwert eine Zeichenfolge ist und die Anzahl der zurückzugebenden Bytes größer \*oder gleich *BufferLength*ist, werden die Daten in *ValuePtr* auf *BufferLength* abzüglich der Länge eines Null-Beendigungszeichens abgeschnitten und vom Treiber null beendet.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetEnvAttr** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_ENV und einem *Handle* von *EnvironmentHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLGetEnvAttr** zurückgegeben werden, und es werden die SQLSTATE-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Die in \* *ValuePtr* zurückgegebenen Daten wurden als *BufferLength* abzüglich des Nullbeendigungszeichens abgeschnitten. Die Länge des nicht abgeschnittenen Zeichenfolgenwerts wird in **StringLengthPtr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY010|Funktionssequenzfehler|(DM) **SQL_ATTR_ODBC_VERSION** wurde noch nicht über **SQLSetEnvAttr**festgelegt. Sie müssen **SQL_ATTR_ODBC_VERSION** nicht explizit festlegen, wenn Sie **SQLAllocHandleStd**verwenden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|Der für das Argument *Attribut* angegebene Wert war für die vom Treiber unterstützte ODBC-Version ungültig.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Der für das Argument *Attribut* angegebene Wert war ein gültiges ODBC-Umgebungsattribut für die vom Treiber unterstützte ODBC-Version, wurde jedoch vom Treiber nicht unterstützt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *EnvironmentHandle* entsprechende Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Eine Liste der Attribute finden Sie unter [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Es sind keine treiberspezifischen Umgebungsattribute vorhanden. Wenn *Attribute* ein Attribut angibt, das eine Zeichenfolge zurückgibt, muss *ValuePtr* ein Zeiger auf einen Puffer sein, in dem die Zeichenfolge zurückgegeben werden soll. Die maximale Länge der Zeichenfolge, einschließlich des Null-Beendigungsbyts, ist *BufferLength-Bytes.*  
  
 **SQLGetEnvAttr** kann jederzeit zwischen der Zuweisung und dem Freiwerden eines Umgebungshandles aufgerufen werden. Alle Umgebungsattribute, die von der Anwendung für die Umgebung erfolgreich festgelegt wurden, bleiben bestehen, bis **SQLFreeHandle** für *EnvironmentHandle* mit einem *HandleType* von SQL_HANDLE_ENV aufgerufen wird. In ODBC 3 *.x*können mehrere Umgebungshandles gleichzeitig zugewiesen werden. Ein Umgebungsattribut für eine Umgebung ist nicht betroffen, wenn eine andere Umgebung zugewiesen wurde.  
  
> [!NOTE]
>  Das SQL_ATTR_OUTPUT_NTS-Umgebungsattribut wird von standardkonformen Anwendungen unterstützt. Wenn **SQLGetEnvAttr** aufgerufen wird, gibt der ODBC 3 *.x-Treiber-Manager* immer SQL_TRUE für dieses Attribut zurück. SQL_ATTR_OUTPUT_NTS kann nur durch einen Aufruf von **SQLSetEnvAttr**auf SQL_TRUE festgelegt werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben der Einstellung eines Verbindungsattributs|[SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Zurückgeben der Einstellung eines Anweisungsattributs|[SQLGetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|Festlegen eines Verbindungsattributs|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Festlegen eines Umgebungsattributs|[SQLSetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Festlegen eines Anweisungsattributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
