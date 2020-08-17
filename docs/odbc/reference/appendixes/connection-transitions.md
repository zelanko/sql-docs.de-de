---
description: Verbindungsübergänge
title: Verbindungs Übergänge | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5f7fecf0ad25311e9d96f4db8554c1cdbf24e91
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339446"
---
# <a name="connection-transitions"></a>Verbindungsübergänge
ODBC-Verbindungen weisen die folgenden Zustände auf.  
  
|Staat|Beschreibung|  
|-----------|-----------------|  
|C0|Nicht zugeordnete Umgebung, nicht zugewiesene Verbindung|  
|C1|Zugeordnete Umgebung, nicht zugeordnete Verbindung|  
|C2|Zugeordnete Umgebung, zugeordnete Verbindung|  
|C3|Verbindungsfunktion benötigt Daten|  
|C4|Verbundene Verbindung|  
|C5|Verbundene Verbindung, zugewiesene Anweisung|  
|C6|Verbundene Verbindung, laufende Transaktion. Eine Verbindung kann sich im Status "C6" befinden, ohne dass der Verbindung eine-Anweisung zugeordnet ist. Nehmen Sie beispielsweise an, die Verbindung befindet sich im manuellen Commitmodus und befindet sich im Zustand C4. Wenn eine-Anweisung zugeordnet, ausgeführt (startet eine Transaktion) und dann freigegeben wird, bleibt die Transaktion aktiv, aber es sind keine-Anweisungen für die Verbindung vorhanden.|  
  
 Die folgenden Tabellen zeigen, wie sich jede ODBC-Funktion auf den Verbindungsstatus auswirkt.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|C0<br /><br /> Keine "-v".|C1 nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|--------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|C1 [1]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|IH 2,2|C2|--[5]|--[5]|--[5]|--[5]|--[5]|  
|IH €|IH|(08003)|(08003)|C5|--[5]|--[5]|  
|IH 0:|IH|(08003)|(08003)|--[5]|--[5]|--[5]|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_ENV wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DBC wurde.  
  
 [3] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_STMT wurde.  
  
 [4] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DESC wurde.  
  
 [5] das Aufrufen von **sqlzugewiesene CHandle** mit *outputhandleptr* , das auf ein gültiges Handle verweist, überschreibt dieses Handle ohne Berücksichtigung der vorherigen Inhalte dieses Handles und kann zu Problemen mit ODBC-Treibern führen. Es ist eine falsche ODBC-Anwendungsprogrammierung zum doppelten Aufrufen von **sqlzuordchandle** mit der gleichen Anwendungsvariablen, die für * \* outputhandleptr* definiert ist, ohne **SQLFreeHandle** aufzurufen, um das Handle vor der erneuten Zuordnung freizugeben. Das Überschreiben von ODBC-Handles auf diese Weise kann zu inkonsistenten Verhalten oder Fehlern im Rahmen der ODBC-Treiber führen.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|C3 [d] C4 [s]|--[d] C2 [e] C4 [s]|(08002)|(08002)|(08002)|  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|IH|IH|IH|--|--[1] C5 [2]|  
  
 [1] die Verbindung befand sich im manuellen Commit-Modus.  
  
 [2] die Verbindung befand sich im Autocommit-Modus.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges, SQLColumns, sqlauslännkeys, SQLGetTypeInfo, SQLPrimaryKeys, sqlprocedurecolrens, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges und SQLTables  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|IH|IH|IH|--[1] C6 [2]|--|  
  
 [1] die Verbindung befand sich im Autocommit-Modus, oder die Datenquelle hat keine Transaktion gestartet.  
  
 [2] die Verbindung befand sich im manuellen Commit-Modus, und die Datenquelle hat eine Transaktion gestartet.  
  
## <a name="sqlconnect"></a>SQLConnect  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|C4|(08002)|(08002)|(08002)|(08002)|  
  
## <a name="sqlcopydesc-sqlgetdescfield-sqlgetdescrec-sqlsetdescfield-and-sqlsetdescrec"></a>SQLCopyDesc, SQLGetDescField, SQLGetDescRec, SQLSetDescField und SQLSetDescRec  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|IH|IH|--[1]|--|--|  
  
 [1] in diesem Zustand sind die einzigen Deskriptoren, die für die Anwendung verfügbar sind, explizit zugeordnete Deskriptoren.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources und SQLDrivers  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|--|--|--|--|--|--|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|(08003)|C2|C2|C2|25000|  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|C4 s--n [f]|(08002)|(08002)|(08002)|(08002)|  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH 1|--[3]|--[3]|--[3]|--|--|--[4] oder ([5], [6] und [8]) C4 [5] und [7] C5 [5], [6] und [9]|  
|IH 2,2|IH|(08003)|(08003)|--|--|C5|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_ENV wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DBC wurde.  
  
 [3] da die Verbindung nicht verbunden ist, ist Sie von der Transaktion nicht betroffen.  
  
 [4] Fehler beim Commit oder Rollback für die Verbindung. In diesem Fall gibt die Funktion SQL_ERROR zurück.  
  
 [5] das Commit oder Rollback für die Verbindung war erfolgreich. Die Funktion gibt SQL_ERROR zurück, wenn ein Commit oder Rollback für eine andere Verbindung fehlgeschlagen ist, oder die Funktion gibt SQL_SUCCESS zurück, wenn der Commit oder Rollback für alle Verbindungen erfolgreich war.  
  
 [6] Es wurde mindestens eine-Anweisung für die Verbindung zugeordnet.  
  
 [7] Es wurden keine Anweisungen für die Verbindung zugeordnet.  
  
 [8] die Verbindung enthielt mindestens eine Anweisung, für die es einen geöffneten Cursor gab, und die Datenquelle behält Cursor bei, wenn für Transaktionen ein Commit oder ein Rollback ausgeführt wird (je nachdem, ob *CompletionType* SQL_COMMIT oder SQL_ROLLBACK). Weitere Informationen finden Sie in den SQL_CURSOR_COMMIT_BEHAVIOR-und SQL_CURSOR_ROLLBACK_BEHAVIOR-Attributen in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 [9] Wenn die Verbindung über Anweisungen verfügt, für die öffnende Cursor vorhanden waren, wurden die Cursor nicht beibehalten, als für die Transaktion ein Commit oder Rollback ausgeführt wurde.  
  
## <a name="sqlexecdirect-and-sqlexecute"></a>SQLExecDirect und SQLExecute  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|IH|IH|IH|--[1] C6 [2] C6 [3]|--|  
  
 [1] die Verbindung befand sich im Autocommit-Modus, und die ausgeführte Anweisung war keine *Cursor* *Spezifikation* (z. b. eine SELECT-Anweisung). oder die Verbindung befand sich im manuellen Commit-Modus, und die ausgeführte Anweisung hat keine Transaktion begonnen.  
  
 [2] die Verbindung befand sich im Autocommit-Modus, und die ausgeführte Anweisung war eine *Cursor* *Spezifikation* (z. b. eine SELECT-Anweisung).  
  
 [3] die Verbindung befand sich im manuellen Commit-Modus, und die Datenquelle hat eine Transaktion gestartet.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH 1|C0|HY010|HY010|HY010|HY010|HY010|  
|IH 2,2|IH|C1|HY010|HY010|HY010|HY010|  
|IH €|IH|IH|IH|IH|C4 [5]--[6]|--[7] C4 [5] und [8] C5 [6] und [8]|  
|IH 0:|IH|IH|IH|--|--|--|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_ENV wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DBC wurde.  
  
 [3] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_STMT wurde.  
  
 [4] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DESC wurde.  
  
 [5] Es wurde nur eine Anweisung für die Verbindung zugeordnet.  
  
 [6] Es wurden mehrere Anweisungen für die Verbindung zugeordnet.  
  
 [7] die Verbindung befand sich im manuellen Commit-Modus.  
  
 [8] die Verbindung befand sich im Autocommit-Modus.  
  
## <a name="sqlfreestmt"></a>'SQLFreeStmt'  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH 1|IH|IH|IH|IH|--|C5 [3]--[4]|  
|IH 2,2|IH|IH|IH|IH|--|--|  
  
 [1] diese Zeile zeigt Transaktionen an, wenn das *options* Argument SQL_CLOSE ist.  
  
 [2] diese Zeile zeigt Transaktionen an, wenn das *options* Argument SQL_UNBIND oder SQL_RESET_PARAMS ist.  
  
 [3] die Verbindung befand sich im Autocommit-Modus, und es waren keine Cursor für Anweisungen mit Ausnahme dieser Anweisung geöffnet.  
  
 [4] die Verbindung befand sich im manuellen Commitmodus, oder Sie befand sich im Autocommit-Modus, und ein Cursor war bei mindestens einer anderen Anweisung geöffnet.  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|--[1] 08003 [2]|HY010|--|--|--|  
  
 [1] das *Attribut* Argument war SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE oder SQL_ATTR_TRACEFILE, oder für das Verbindungs Attribut wurde ein Wert festgelegt.  
  
 [2] das *Attribut* Argument war nicht SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE oder SQL_ATTR_TRACEFILE, und für das Verbindungs Attribut wurde kein Wert festgelegt.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField und SQLGetDiagRec  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH 1|--|--|--|--|--|--|  
|IH 2,2|IH|--|--|--|--|--|  
|IH €|IH|IH|IH|IH|--|--|  
|IH 0:|IH|IH|IH|--|--|--|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_ENV wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DBC wurde.  
  
 [3] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_STMT wurde.  
  
 [4] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DESC wurde.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|HY010|HY010|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|--[1] 08003 [2]|08003|--|--|--|  
  
 [1] das *InfoType* -Argument wurde SQL_ODBC_VER.  
  
 [2] das *InfoType* -Argument wurde nicht SQL_ODBC_VER.  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|IH|IH|IH|--[1] C6 [2]|--[3] C5 [1]|  
  
 [1] die Verbindung befand sich im Autocommit-Modus, und der **SQLMoreResults** -Befehl hat die Verarbeitung eines Resultsets einer Cursor Spezifikation nicht initialisiert.  
  
 [2] die Verbindung befand sich im Autocommit-Modus, und der **SQLMoreResults** -Befehl hat die Verarbeitung eines Resultsets einer Cursor Spezifikation initialisiert.  
  
 [3] die Verbindung befand sich im manuellen Commit-Modus.  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|(08003)|(08003)|--|--|--|  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|IH|IH|IH|--[1] C6 [2]|--|  
  
 [1] die Verbindung befand sich im Autocommit-Modus, oder die Datenquelle hat keine Transaktion gestartet.  
  
 [2] die Verbindung befand sich im manuellen Commit-Modus, und die Datenquelle hat eine Transaktion gestartet.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|--[1] 08003 [2]|HY010|--[3] 08002 [4] HY011 [5]|--[3] 08002 [4] HY011 [5]|--[3] und [6] C5 [8] 08002 [4] HY011 [5] oder [7]|  
  
 [1] das *Attribut* Argument wurde nicht SQL_ATTR_TRANSLATE_LIB oder SQL_ATTR_TRANSLATE_OPTION.  
  
 [2] das *Attribut* Argument wurde SQL_ATTR_TRANSLATE_LIB oder SQL_ATTR_TRANSLATE_OPTION.  
  
 [3] das *Attribut* Argument wurde nicht SQL_ATTR_ODBC_CURSORS oder SQL_ATTR_PACKET_SIZE.  
  
 [4] das *Attribut* Argument wurde SQL_ATTR_ODBC_CURSORS.  
  
 [5] das *Attribut* Argument wurde SQL_ATTR_PACKET_SIZE.  
  
 [6] das *Attribut* Argument wurde nicht SQL_ATTR_AUTOCOMMIT, oder das *Attribut* Argument war SQL_ATTR_AUTOCOMMIT, und durch das Festlegen dieses Attributs wurde kein Commit für die Transaktion durchgeführt.  
  
 [7] das *Attribut* Argument wurde SQL_ATTR_TXN_ISOLATION.  
  
 [8] das *Attribut* Argument wurde SQL_ATTR_AUTOCOMMIT, und durch das Festlegen dieses Attributs wurde ein Commit für die Transaktion ausgeführt.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|--|--|HY010|--|--|--|  
  
## <a name="all-other-odbc-functions"></a>Alle anderen ODBC-Funktionen  
  
|C0<br /><br /> Keine "-v".|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|IH|IH|IH|--|--|
