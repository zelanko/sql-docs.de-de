---
title: Standard-Datenquelle | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 909f9b3e7c8087add8eb66ca2f5c15253026304c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267654"
---
# <a name="default-data-source"></a>Standarddatenquelle
Der Treiber möglicherweise wählen Sie eine Datenquelle wird aufgerufen, die Standarddatenquelle in bestimmten Fällen, in dem die Anwendung nicht explizit einen angeben wird:  
  
-   In einem Aufruf von **SQLConnect** , in denen die *ServerName* Argument ist eine Zeichenfolge der Länge 0 (null), ein null-Zeiger oder Standard.  
  
-   In einem Aufruf von **SQLDriverConnect** , in denen *InConnectionString* gibt an, entweder **DSN**= DEFAULT oder gibt an, mit der **DSN** Schlüsselwort ein die Datenquelle, die nicht in den Systeminformationen enthalten ist.  
  
 Es ist treiberdefinierten, wie die Standarddatenquelle angegeben wird. Dies kann zur Folge haben administrative Maßnahmen und hängt von dem Benutzer.
