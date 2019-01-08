---
title: ODBC-Service-Dienstanbieterschnittstelle – Zusammenfassung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5f3c133b105c905b79589d86952658b6d39f0f6
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52390443"
---
# <a name="odbc-service-provider-interface-summary"></a>ODBC-Dienstanbieterschnittstelle – Übersicht
Die folgende Tabelle beschreibt die Funktionen der ODBC-Dienstanbieter-Schnittstelle. Weitere Informationen zur Syntax und Semantik für die einzelnen Funktionen finden Sie unter [ODBC Service Provider Interface (SPI) Verweis](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md).  
  
|Funktionsname|Zweck|  
|-------------------|-------------|  
|[SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Identisch mit [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), sondern legt das Attribut auf der Verbindung Informationen-Token anstelle von auf dem Verbindungshandle fest.|  
|[SQLSetDriverConnectInfo](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|Legt die Verbindungszeichenfolge fest, in das Verbindungstoken für die Informationen für einer Anwendung [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) aufrufen.|  
|[SQLSetConnectInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Legt die Datenquelle, Benutzer-ID und Kennwort in das Verbindungstoken für die Informationen für einer Anwendung [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) aufrufen.|  
|[SQLGetPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Ruft ab, die Pool-ID|  
|[SQLRateConnection](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Bestimmt, ob ein Treiber eine vorhandene Verbindung im Verbindungspool wiederverwendet werden kann.|  
|[SQLPoolConnect](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Erstellen Sie eine neue Verbindung, wenn keine Verbindung im Pool wiederverwendet werden kann.|  
|[SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Informiert einen Treiber, den Pool-ID Zeitlimit überschritten wurde.|
