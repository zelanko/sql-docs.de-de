---
title: Zusammenfassung der ODBC-Dienstanbieterschnittstelle | Microsoft Docs
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
ms.openlocfilehash: b2f7e459cc7b89106bf1b7ebcd49c699d43da9f6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298897"
---
# <a name="odbc-service-provider-interface-summary"></a>ODBC-Dienstanbieterschnittstelle – Übersicht
In der folgenden Tabelle werden die Schnittstellenfunktionen des ODBC-Dienstanbieters beschrieben. Weitere Informationen zur Syntax und Semantik für jede Funktion finden Sie unter [ODBC Service Provider Interface (SPI) Reference](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md).  
  
|Funktionsname|Zweck|  
|-------------------|-------------|  
|[SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Genauso wie [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), aber es legt das Attribut für das Verbindungsinformationstoken anstelle des Verbindungshandles fest.|  
|[SQLSetDriverConnectInfo](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|Legt die Verbindungszeichenfolge in das Verbindungsinfotoken für den [SQLDriverConnect-Aufruf](../../../odbc/reference/syntax/sqldriverconnect-function.md) einer Anwendung fest.|  
|[SQLSetConnectInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Legt die Datenquelle, die Benutzer-ID und das Kennwort in das Verbindungsinfotoken für den [SQLConnect-Aufruf](../../../odbc/reference/syntax/sqlconnect-function.md) einer Anwendung fest.|  
|[SQLGetPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Ruft die Pool-ID ab.|  
|[SQLRateConnection](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Legt fest, ob ein Treiber eine vorhandene Verbindung im Verbindungspool wiederverwenden kann.|  
|[SQLPoolConnect](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Erstellen Sie eine neue Verbindung, wenn keine Verbindung im Pool wiederverwendet werden kann.|  
|[SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Informiert einen Treiber darüber, dass ein Zeitdruck für eine Pool-ID festgelegt wurde.|
