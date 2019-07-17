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
ms.openlocfilehash: 0a97bed3bb921b9c881a98d8d9a9031ef7630f26
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111898"
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
