---
title: Standarddaten Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to data source [ODBC], default data source
- functions [ODBC], data source or driver connections
- data sources [ODBC], default
- default data source [ODBC]
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], default data source
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: dd473cc6-f051-4aa0-ab14-3dd1b37fe99e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 978362b7dfe92d1333f83be684f6326cf25dd69b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305991"
---
# <a name="default-data-source"></a>Standarddatenquelle
Der Treiber kann eine Datenquelle, die als Standarddaten Quelle bezeichnet wird, in bestimmten Fällen auswählen, in denen die Anwendung nicht explizit eine Datenquelle angibt:  
  
-   Bei einem **SQLCONNECT** -Befehl, bei dem das *Servername* -Argument eine Zeichenfolge der Länge 0 (null), ein NULL-Zeiger oder ein Standardwert ist.  
  
-   Bei einem **SQLDriverConnect** -Befehl, bei dem *InConnectionString* entweder **DSN**= Default angibt oder mit dem **DSN** -Schlüsselwort eine Datenquelle angibt, die nicht in den Systeminformationen enthalten ist.  
  
 Es ist Treiber definiert, wie die Standarddaten Quelle angegeben wird. Dabei kann es sich um administrative Aktionen handeln, die ggf. vom Benutzer abhängig sind.
