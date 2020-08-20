---
description: ODBC-Dienstanbieterschnittstelle – Übersicht
title: Zusammenfassung der ODBC-Dienstanbieter Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 00d15d33fba1e697eebbe6a640c4f8a4d8eadea7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487343"
---
# <a name="odbc-service-provider-interface-summary"></a>ODBC-Dienstanbieterschnittstelle – Übersicht
In der folgenden Tabelle werden die Funktionen der ODBC-Dienstanbieter Schnittstelle beschrieben. Weitere Informationen zur Syntax und Semantik für die einzelnen Funktionen finden Sie in der [Referenz zur ODBC-Dienstanbieter Schnittstelle (SPI)](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md).  
  
|Funktionsname|Zweck|  
|-------------------|-------------|  
|[Sqlsetconnectattrfordbcinfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Identisch mit [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), aber das-Attribut wird auf das Verbindungs Informations Token festgelegt, anstatt auf das Verbindungs Handle.|  
|[Sqlsetdriverconnectinfo](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|Legt die Verbindungs Zeichenfolge in das Verbindungs Informations Token für den [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) -Befehl einer Anwendung fest.|  
|[Sqlsetconnectinfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Legt die Datenquelle, die Benutzer-ID und das Kennwort in das Verbindungs Informations Token für den [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md) -Befehl einer Anwendung fest.|  
|[Sqlgetpoolid](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Ruft die Pool-ID ab.|  
|[Sqlrateconnetction](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Bestimmt, ob ein Treiber eine vorhandene Verbindung im Verbindungspool wieder verwenden kann.|  
|[Sqlpoolconnect](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Erstellen Sie eine neue Verbindung, wenn keine Verbindung im Pool wieder verwendet werden kann.|  
|[Sqlcleanupconnectionpoolid](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Informiert einen Treiber darüber, dass ein Timeout für eine Pool-ID aufgetreten ist.|
