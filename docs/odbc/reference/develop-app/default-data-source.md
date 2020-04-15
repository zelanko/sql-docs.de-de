---
title: Standarddatenquelle | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305991"
---
# <a name="default-data-source"></a>Standarddatenquelle
Der Treiber kann eine Datenquelle auswählen, die als Standarddatenquelle bezeichnet wird, in bestimmten Fällen, in denen die Anwendung keine Datenquelle explizit angibt:  
  
-   Bei einem Aufruf von **SQLConnect,** bei dem das *Argument ServerName* eine Zeichenfolge mit einer Länge von null, ein Nullzeiger oder DEFAULT ist.  
  
-   Bei einem Aufruf von **SQLDriverConnect,** bei dem *InConnectionString* entweder **DSN**=DEFAULT angibt oder mit dem **DSN-Schlüsselwort** eine Datenquelle angibt, die nicht in den Systeminformationen enthalten ist.  
  
 Es ist treiberdefiniert, wie die Standarddatenquelle angegeben wird. Dies kann administrative Maßnahmen beinhalten und vom Benutzer abhängen.
