---
title: Umweltübergänge | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ebfb5475d24d5fc70c4cb46a666b2573066565a1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283300"
---
# <a name="environment-transitions"></a>Umgebungsübergänge
ODBC-Umgebungen haben die folgenden drei Zustände.  
  
|State|BESCHREIBUNG|  
|-----------|-----------------|  
|E0|Nicht zugewiesene Umgebung|  
|E1|Zugeordnete Umgebung, nicht zugewiesene Verbindung|  
|E2|Zugeordnete Umgebung, zugewiesene Verbindung|  
  
 Die folgenden Tabellen zeigen, wie sich jede ODBC-Funktion auf den Umgebungsstatus auswirkt.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|E1[1]|--[4]|--[4]|  
|(IH) [2]|E2[5]<br />(HY010) [6]|--[4]|  
|(IH) [3]|(IH)|--[4]|  
  
 [1] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DBC wurde.  
  
 [3] Diese Zeile zeigt Übergänge, wenn *HandleType* SQL_HANDLE_STMT oder SQL_HANDLE_DESC wurde.  
  
 [4] Das Aufrufen von **SQLAllocHandle** mit *OutputHandlePtr, das* auf ein gültiges Handle verweist, überschreibt dieses Handle. Dies kann ein Anwendungsprogrammierfehler sein.  
  
 [5] Das SQL_ATTR_ODBC_VERSION Umgebungsattribut wurde für die Umgebung festgelegt.  
  
 [6] Das SQL_ATTR_ODBC_VERSION Umgebungsattribut wurde nicht für die Umgebung festgelegt.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources und SQLDrivers  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010) [2]|--[1]<br />(HY010) [2]|  
  
 [1] Das SQL_ATTR_ODBC_VERSION Umgebungsattribut wurde für die Umgebung festgelegt.  
  
 [2] Das SQL_ATTR_ODBC_VERSION Umgebungsattribut wurde nicht für die Umgebung festgelegt.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH) [1]|--[3]<br />(HY010) [4]|--[3]<br />(HY010) [4]|  
|(IH) [2]|(IH)|--|  
  
 [1] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DBC wurde.  
  
 [3] Das SQL_ATTR_ODBC_VERSION Umgebungsattribut wurde für die Umgebung festgelegt.  
  
 [4] Das SQL_ATTR_ODBC_VERSION Umgebungsattribut wurde nicht für die Umgebung festgelegt.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH) [1]|E0|(HY010)|  
|(IH) [2]|(IH)|--[4]<br />E1[5]|  
|(IH) [3]|(IH)|--|  
  
 [1] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DBC wurde.  
  
 [3] Diese Zeile zeigt Übergänge, wenn *HandleType* SQL_HANDLE_STMT oder SQL_HANDLE_DESC wurde.  
  
 [4] Es gab weitere zugewiesene Verbindungshandles.  
  
 [5] Das in *Handle* angegebene Verbindungshandle war das einzige zugewiesene Verbindungshandle.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField und SQLGetDiagRec  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH) [1]|--|--|  
|(IH) [2]|(IH)|--|  
  
 [1] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] Diese Zeile zeigt Übergänge an, bei denen *HandleType* SQL_HANDLE_DBC, SQL_HANDLE_STMT oder SQL_HANDLE_DESC wurde.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010) [2]|--|  
  
 [1] Das SQL_ATTR_ODBC_VERSION Umgebungsattribut wurde für die Umgebung festgelegt.  
  
 [2] Das SQL_ATTR_ODBC_VERSION Umgebungsattribut wurde nicht für die Umgebung festgelegt.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010) [2]|(HY011)|  
  
 [1] Das SQL_ATTR_ODBC_VERSION Umgebungsattribut wurde für die Umgebung festgelegt.  
  
 [2] Das *Attributargument* wurde nicht SQL_ATTR_ODBC_VERSION, und das SQL_ATTR_ODBC_VERSION Umgebungsattribut wurde nicht für die Umgebung festgelegt.  
  
## <a name="all-other-odbc-functions"></a>Alle anderen ODBC-Funktionen  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|(IH)|(IH)|--|
