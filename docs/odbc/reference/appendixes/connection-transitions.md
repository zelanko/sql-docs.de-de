---
title: Verbindungsübergänge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transitioning states [ODBC], connection
- connection transitions [ODBC]
- state transitions [ODBC], connection
ms.assetid: 6b6e1a47-4a52-41c8-bb9e-7ddeae09913e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f808460a1421a9ab4cb3a76c2810d810b9636b11
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52537500"
---
# <a name="connection-transitions"></a>Verbindungsübergänge
ODBC-Verbindungen werden die folgenden Status haben.  
  
|Status|Description|  
|-----------|-----------------|  
|C0|Nicht zugeordnete Umgebung verfügbaren Verbindung|  
|C1|Zugeordnete Umgebung verfügbaren Verbindung|  
|C2|Zugeordnete Verbindung zugeordneten-Umgebung|  
|C3|Verbindungsfunktion benötigt Daten.|  
|C4|Verbundene Verbindung|  
|C5|Verbindung zugeordnete Anweisung verbunden|  
|C6|Verbundene Verbindung, die Transaktion ausgeführt. Es ist möglich, dass eine Verbindung im Zustand C6 keine Anweisungen für die Verbindung zugeordnet werden soll. Nehmen wir beispielsweise an, die Verbindung befindet sich im manuellen Commit-Modus und befindet sich im Zustand C4. Wenn eine Anweisung zugeordnet, ausgeführt (Starten einer Transaktion) und anschließend freigegeben ist, wird die Transaktion bleibt aktiv, aber es gibt keine Anweisungen für die Verbindung.|  
  
 Die folgenden Tabellen zeigen, wie jede ODBC-Funktion wirkt sich der Zustand der Verbindung auf.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|C0<br /><br /> Keine Env.|C1 nicht zugeordnet.|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|--------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|C1 [1]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|(BEI) [2]|C2|--[5]|--[5]|--[5]|--[5]|--[5]|  
|(BEI) [3]|(IH)|(08003)|(08003)|C5|--[5]|--[5]|  
|(BEI) [4]|(IH)|(08003)|(08003)|--[5]|--[5]|--[5]|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* wurde SQL_HANDLE_DBC auf.  
  
 [3] für diese Zeile zeigt die Übergänge beim *HandleType* wurde von SQL_HANDLE_STMT auf.  
  
 [4] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_DESC wurde.  
  
 [5] aufrufen **SQLAllocHandle** mit *OutputHandlePtr* überschreibt dieses Handle ohne Berücksichtigung der vorherige Inhalt Ofthat Handle auf ein gültiges Handle verweist, und verursachen möglicherweise Probleme für ODBC-Treiber. Falsche ODBC-Anwendung programmieren aufrufen, ist **SQLAllocHandle** zweimal mit der gleichen Anwendungsvariablen, die für definierten  *\*OutputHandlePtr* ohne  **SQLFreeHandle** auf das Handle frei, bevor Sie es erneut zugewiesen werden. Überschreiben von ODBC können Handles auf diese Weise zu inkonsistentem Verhalten oder Fehler seitens der ODBC-Treiber führen.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|[D] C3, C4 [s]|--[d] C2 [e] C4 [s]|(08002)|(08002)|(08002)|  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--|: [1] C5 [2]|  
  
 [1]. die Verbindung wurde im Manualcommit Modus.  
  
 [2]. die Verbindung wurde im Autocommit Modus.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges und SQLTables  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|: [1] C6 [2]|--|  
  
 [1] für die Verbindung im Autocommit Modus wurde, oder die Datenquelle wurde nicht gestartet, eine Transaktion.  
  
 [2] für die Verbindung wurde im Manualcommit Modus, und die Datenquelle wurde eine Transaktion gestartet.  
  
## <a name="sqlconnect"></a>SQLConnect  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|C4|(08002)|(08002)|(08002)|(08002)|  
  
## <a name="sqlcopydesc-sqlgetdescfield-sqlgetdescrec-sqlsetdescfield-and-sqlsetdescrec"></a>SQLCopyDesc, SQLGetDescField, SQLGetDescRec, SQLSetDescField und SQLSetDescRec  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|--[1]|--|--|  
  
 [1] in diesem Fall werden die einzigen Deskriptoren für die Anwendung verfügbaren explizit Deskriptoren zugeordnet.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources und SQLDrivers  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|--|--|--|--|--|--|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(08003)|C2|C2|C2|25000|  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|C4 s – n [f]|(08002)|(08002)|(08002)|(08002)|  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(BEI) [1]|--[3]|--[3]|--[3]|--|--|: [4] oder ([5], [6] und [8]) C4 [5] und [7] C5 [5], [6] und [9]|  
|(BEI) [2]|(IH)|(08003)|(08003)|--|--|C5|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* wurde SQL_HANDLE_DBC auf.  
  
 [3] da die Verbindung nicht verbunden ist, ist es nicht von der Transaktion betroffen.  
  
 [4] für den Commit- oder Rollbackvorgang Fehler bei der Verbindung. In diesem Fall gibt die Funktion SQL_ERROR zurück.  
  
 [5] für den Commit- oder Rollbackvorgang, die auf die Verbindung war erfolgreich. Die Funktion gibt SQL_ERROR zurück, wenn der Commit oder Rollback, die auf eine andere Verbindung fehlgeschlagen ist oder die Funktion gibt SQL_SUCCESS zurück, wenn der Commit oder Rollback für alle Verbindungen erfolgreich war.  
  
 [6] Es wurde mindestens eine Anweisung, die bei der Verbindung zugeordnet.  
  
 [7] gab es keine Anweisungen für die Verbindung zugewiesen.  
  
 [8] die Verbindung haben mindestens eine Anweisung für die es wurde von einem geöffneten Cursor, und die Datenquelle beibehalten Cursor bei Transaktionen ein Commit oder Rollback ausgeführt werden, je nachdem, was angewendet wird (je nachdem, ob *' CompletionType '* SQL_ wurde COMMIT oder der SQL_ROLLBACK). Weitere Informationen finden Sie auf die SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR Attribute in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 [9] hätte die Verbindung alle Anweisungen für die geöffnete Cursor gab, wurden die Cursor nicht beibehalten, wenn die Transaktion wurde ein Commit oder Rollback.  
  
## <a name="sqlexecdirect-and-sqlexecute"></a>SQLExecDirect und SQLExecute  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--C6 VON [1] C6 [2] [3]|--|  
  
 [1] für die Verbindung im Autocommit Modus, und die ausgeführte Anweisung nicht wurde eine *Cursor* *Spezifikation* (z. B. eine SELECT-Anweisung) oder die Verbindung wurde im Manualcommit-Modus, und die Anweisung ausgeführt eine Transaktion nicht beginnen.  
  
 [2] für die Verbindung im Autocommit Modus und die ausgeführte Anweisung wurde eine *Cursor* *Spezifikation* (z. B. eine SELECT-Anweisung).  
  
 [3] die Verbindung wurde im Manualcommit Modus, und die Datenquelle wurde eine Transaktion gestartet.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(BEI) [1]|C0|(HY010)|(HY010)|(HY010)|(HY010)|(HY010)|  
|(BEI) [2]|(IH)|(C1)|(HY010)|(HY010)|(HY010)|(HY010)|  
|(BEI) [3]|(IH)|(IH)|(IH)|(IH)|C4 [5]: [6]|--[7] C4 [5] und [8] C5 [6] und [8]|  
|(BEI) [4]|(IH)|(IH)|(IH)|--|--|--|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* wurde SQL_HANDLE_DBC auf.  
  
 [3] für diese Zeile zeigt die Übergänge beim *HandleType* wurde von SQL_HANDLE_STMT auf.  
  
 [4] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_DESC wurde.  
  
 [5] gab es nur eine Anweisung, die bei der Verbindung zugeordnet.  
  
 [6] gab es mehrere Anweisungen, die bei der Verbindung zugeordnet.  
  
 [7] die Verbindung wurde im Manualcommit Modus.  
  
 [8] die Verbindung wurde im Autocommit Modus.  
  
## <a name="sqlfreestmt"></a>'SQLFreeStmt'  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(BEI) [1]|(IH)|(IH)|(IH)|(IH)|--|C5 [3]: [4]|  
|(BEI) [2]|(IH)|(IH)|(IH)|(IH)|--|--|  
  
 [1] für diese Zeile zeigt Transaktionen bei der *Option* Argument ist SQL_CLOSE.  
  
 [2] für diese Zeile zeigt Transaktionen bei der *Option* Argument ist SQL_UNBIND oder SQL_RESET_PARAMS.  
  
 [3] die Verbindung im Autocommit Modus war und keine Cursor geöffnet, auf die Anweisungen, mit Ausnahme des vorliegenden waren.  
  
 [4] für die Verbindung wurde im Manualcommit-Modus oder im Autocommit Modus war und ein Cursor geöffnet, auf mindestens eine andere Anweisung war.  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|BEI|BEI|--[1] 08003[2]|HY010|--|--|--|  
  
 [1] der *Attribut* Argument war SQL_ATTR_ACCESS_MODE SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE oder SQL_ATTR_TRACEFILE oder ein Wert für das Verbindungsattribut festgelegt wurde.  
  
 [2] der *Attribut* Argument war kein SQL_ATTR_ACCESS_MODE SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE oder SQL_ATTR_TRACEFILE und hatte kein Wert für die Verbindung festgelegt wurde -Attribut.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField und SQLGetDiagRec  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(BEI) [1]|--|--|--|--|--|--|  
|(BEI) [2]|(IH)|--|--|--|--|--|  
|(BEI) [3]|(IH)|(IH)|(IH)|(IH)|--|--|  
|(BEI) [4]|(IH)|(IH)|(IH)|--|--|--|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* wurde SQL_HANDLE_DBC auf.  
  
 [3] für diese Zeile zeigt die Übergänge beim *HandleType* wurde von SQL_HANDLE_STMT auf.  
  
 [4] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_DESC wurde.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|BEI|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|BEI|BEI|HY010|HY010|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|BEI|BEI|--[1] 08003[2]|08003|--|--|--|  
  
 [1] der *Informationsart* Argument war SQL_ODBC_VER.  
  
 [2] der *Informationsart* Argument war kein SQL_ODBC_VER.  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|: [1] C6 [2]|: [3] C5 [1]|  
  
 [1] für die Verbindung im Autocommit-Modus, und der Aufruf wurde **SQLMoreResults** die Verarbeitung eines Resultsets einer Spezifikation Cursor wurde nicht initialisiert.  
  
 [2] für die Verbindung im Autocommit-Modus, und der Aufruf wurde **SQLMoreResults** wurde die Verarbeitung eines Resultsets von Cursorspezifikation initialisiert.  
  
 [3] die Verbindung wurde im Manualcommit Modus.  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(08003)|(08003)|--|--|--|  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|: [1] C6 [2]|--|  
  
 [1] für die Verbindung im Autocommit Modus wurde, oder die Datenquelle wurde nicht gestartet, eine Transaktion.  
  
 [2] für die Verbindung wurde im Manualcommit Modus, und die Datenquelle wurde eine Transaktion gestartet.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|BEI|BEI|--[1] 08003[2]|HY010|: [3] 08002 [4] HY011 [5]|: [3] 08002 [4] HY011 [5]|: [3] und [6] C5 [8] [4] HY011-08002 [5] oder [7]|  
  
 [1] der *Attribut* Argument war kein SQL_ATTR_TRANSLATE_LIB oder SQL_ATTR_TRANSLATE_OPTION.  
  
 [2] der *Attribut* Argument war SQL_ATTR_TRANSLATE_LIB oder SQL_ATTR_TRANSLATE_OPTION.  
  
 [3] die *Attribut* Argument war kein SQL_ATTR_ODBC_CURSORS oder SQL_ATTR_PACKET_SIZE.  
  
 [4] der *Attribut* Argument war SQL_ATTR_ODBC_CURSORS.  
  
 [5] die *Attribut* Argument war SQL_ATTR_PACKET_SIZE.  
  
 [6] die *Attribut* Argument war kein SQL_ATTR_AUTOCOMMIT, oder die *Attribut* Argument war SQL_ATTR_AUTOCOMMIT und das Festlegen dieses Attributs keinen commit der Transaktion.  
  
 [7] die *Attribut* Argument war SQL_ATTR_TXN_ISOLATION.  
  
 [8] die *Attribut* Argument war SQL_ATTR_AUTOCOMMIT und das Festlegen dieses Attributs Commit der Transaktions.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|--|--|(HY010)|--|--|--|  
  
## <a name="all-other-odbc-functions"></a>Alle anderen ODBC-Funktionen  
  
|C0<br /><br /> Keine Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> zugewiesen|C3<br /><br /> Daten erforderlich|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaction|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--|--|
