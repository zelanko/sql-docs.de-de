---
title: Umgebungsübergänge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment transitions [ODBC]
- transitioning states [ODBC], environment
- state transitions [ODBC], environment
ms.assetid: 9d11b1ab-f4c8-48ca-9812-8c04303f939d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ed2bbf40ac333db34d3920b2ed2ec688c344bfe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188991"
---
# <a name="environment-transitions"></a>Umgebungsübergänge
ODBC-Umgebungen müssen die folgenden drei Zustände.  
  
|Status|Description|  
|-----------|-----------------|  
|E0|Nicht zugeordnete Umgebung|  
|E1|Zugeordnete Umgebung verfügbaren Verbindung|  
|E2|Zugeordnete Verbindung zugeordneten-Umgebung|  
  
 Die folgenden Tabellen zeigen, wie jede ODBC-Funktion den Zustand der Umgebung auswirkt.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> zugewiesen|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|E1[1]|--[4]|--[4]|  
|(IH)[2]|E2[5]<br />(HY010)[6]|--[4]|  
|(IH)[3]|(IH)|--[4]|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* wurde SQL_HANDLE_DBC auf.  
  
 [3] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_STMT auf oder SQL_HANDLE_DESC war.  
  
 [4] aufrufen **SQLAllocHandle** mit *OutputHandlePtr* verweist auf ein gültiges Handle dieses Handle überschreibt. Dies kann eine Anwendung Programmierfehler sein.  
  
 [5] SQL_ATTR_ODBC_VERSION umgebungsattributs mussten für die Umgebung festgelegt wurde.  
  
 [6] SQL_ATTR_ODBC_VERSION umgebungsattributs hatte nicht für die Umgebung festgelegt wurde.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources und SQLDrivers  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> zugewiesen|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010)[2]|--[1]<br />(HY010)[2]|  
  
 [1] SQL_ATTR_ODBC_VERSION umgebungsattributs mussten für die Umgebung festgelegt wurde.  
  
 [2] SQL_ATTR_ODBC_VERSION umgebungsattributs hatte nicht für die Umgebung festgelegt wurde.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> zugewiesen|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)[1]|--[3]<br />(HY010)[4]|--[3]<br />(HY010)[4]|  
|(IH)[2]|(IH)|--|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* wurde SQL_HANDLE_DBC auf.  
  
 [3] SQL_ATTR_ODBC_VERSION umgebungsattributs mussten für die Umgebung festgelegt wurde.  
  
 [4] SQL_ATTR_ODBC_VERSION umgebungsattributs hatte nicht für die Umgebung festgelegt wurde.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> zugewiesen|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)[1]|E0|(HY010)|  
|(IH)[2]|(IH)|--[4]<br />E1[5]|  
|(IH)[3]|(IH)|--|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* wurde SQL_HANDLE_DBC auf.  
  
 [3] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_STMT auf oder SQL_HANDLE_DESC war.  
  
 [4] gab auf anderen Verbindungshandles zugeordnete.  
  
 [5] Verbindungshandles, die im angegebenen *behandeln* wurde das einzige zugeordnete Verbindungshandle.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField und SQLGetDiagRec  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> zugewiesen|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)[1]|--|--|  
|(IH)[2]|(IH)|--|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* war SQL_HANDLE_DBC auf, SQL_HANDLE_STMT auf oder SQL_HANDLE_DESC.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> zugewiesen|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010)[2]|--|  
  
 [1] SQL_ATTR_ODBC_VERSION umgebungsattributs mussten für die Umgebung festgelegt wurde.  
  
 [2] SQL_ATTR_ODBC_VERSION umgebungsattributs hatte nicht für die Umgebung festgelegt wurde.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> zugewiesen|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010)[2]|(HY011)|  
  
 [1] SQL_ATTR_ODBC_VERSION umgebungsattributs mussten für die Umgebung festgelegt wurde.  
  
 [2] der *Attribut* Argument war kein SQL_ATTR_ODBC_VERSION und umgebungsattributs SQL_ATTR_ODBC_VERSION hatte nicht für die Umgebung festgelegt wurde.  
  
## <a name="all-other-odbc-functions"></a>Alle anderen ODBC-Funktionen  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> zugewiesen|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)|(IH)|--|
