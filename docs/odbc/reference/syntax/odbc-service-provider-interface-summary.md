---
title: Zusammenfassung der ODBC-Dienstanbieter Schnittstelle | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68111898"
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
