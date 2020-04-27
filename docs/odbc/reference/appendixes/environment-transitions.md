---
title: Umgebungs Übergänge | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283300"
---
# <a name="environment-transitions"></a>Umgebungsübergänge
ODBC-Umgebungen weisen die folgenden drei Zustände auf.  
  
|State|BESCHREIBUNG|  
|-----------|-----------------|  
|E0|Nicht zugewiesene Umgebung|  
|E1|Zugeordnete Umgebung, nicht zugeordnete Verbindung|  
|E2|Zugeordnete Umgebung, zugeordnete Verbindung|  
  
 Die folgenden Tabellen zeigen, wie sich jede ODBC-Funktion auf den Umgebungszustand auswirkt.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|E1 [1]|--[4]|--[4]|  
|IH 2,2|E2 [5]<br />HY010 6|--[4]|  
|IH €|IH|--[4]|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_ENV wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DBC wurde.  
  
 [3] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_STMT oder SQL_HANDLE_DESC wurde.  
  
 [4] das Aufrufen von **sqlzugewiesene CHandle** mit *outputhandleptr* , das auf ein gültiges Handle verweist, überschreibt dieses handle. Möglicherweise handelt es sich um einen Anwendungs Programmierfehler.  
  
 [5] das SQL_ATTR_ODBC_VERSION Environment-Attribut wurde für die Umgebung festgelegt.  
  
 [6] das SQL_ATTR_ODBC_VERSION Environment-Attribut wurde für die Umgebung nicht festgelegt.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources und SQLDrivers  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|IH|--[1]<br />HY010 2,2|--[1]<br />HY010 2,2|  
  
 [1] das SQL_ATTR_ODBC_VERSION Environment-Attribut wurde für die Umgebung festgelegt.  
  
 [2] das SQL_ATTR_ODBC_VERSION Environment-Attribut wurde für die Umgebung nicht festgelegt.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|IH 1|--[3]<br />HY010 0:|--[3]<br />HY010 0:|  
|IH 2,2|IH|--|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_ENV wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DBC wurde.  
  
 [3] das SQL_ATTR_ODBC_VERSION Environment-Attribut wurde für die Umgebung festgelegt.  
  
 [4] das SQL_ATTR_ODBC_VERSION Environment-Attribut wurde für die Umgebung nicht festgelegt.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|IH 1|E0|HY010|  
|IH 2,2|IH|--[4]<br />E1 [5]|  
|IH €|IH|--|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_ENV wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DBC wurde.  
  
 [3] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_STMT oder SQL_HANDLE_DESC wurde.  
  
 [4] Es sind andere zugeordnete Verbindungs Handles vorhanden.  
  
 [5] das in *handle* angegebene Verbindungs Handle war das einzige zugeordnete Verbindungs Handle.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField und SQLGetDiagRec  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|IH 1|--|--|  
|IH 2,2|IH|--|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_ENV wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DBC, SQL_HANDLE_STMT oder SQL_HANDLE_DESC war.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|IH|--[1]<br />HY010 2,2|--|  
  
 [1] das SQL_ATTR_ODBC_VERSION Environment-Attribut wurde für die Umgebung festgelegt.  
  
 [2] das SQL_ATTR_ODBC_VERSION Environment-Attribut wurde für die Umgebung nicht festgelegt.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|IH|--[1]<br />HY010 2,2|HY011|  
  
 [1] das SQL_ATTR_ODBC_VERSION Environment-Attribut wurde für die Umgebung festgelegt.  
  
 [2] das *Attribut* Argument wurde nicht SQL_ATTR_ODBC_VERSION, und das SQL_ATTR_ODBC_VERSION Umgebungs Attribut wurde für die Umgebung nicht festgelegt.  
  
## <a name="all-other-odbc-functions"></a>Alle anderen ODBC-Funktionen  
  
|E0<br /><br /> Nicht zugeordnet|E1<br /><br /> Zugeordnet|E2<br /><br /> Verbindung|  
|------------------------|----------------------|-----------------------|  
|IH|IH|--|
