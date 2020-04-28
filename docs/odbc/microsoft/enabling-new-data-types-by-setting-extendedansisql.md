---
title: Aktivieren neuer Datentypen durch Festlegen von extendedansisql | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], enabling new data types
ms.assetid: f2865543-7fff-44fa-9a6a-968bec33acdc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b703c5c14c4743e13feee139d16e5dfeb3c24c63
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303411"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Aktivieren neuer Datentypen durch Festlegen von ExtendedAnsiSQL
Zwei neue Datentypen sind in Jet 4,0-Datenbanken verfügbar, wenn das extendedansisql-Flag aktiviert ist: SQL_DECIMAL und SQL_NUMERIC. Die Standardgenauigkeit und-Skala sind 18 bzw. 0. Daten, auf die über ODBC zugegriffen wird und die als SQL_DECIMAL oder SQL_NUMERIC typisiert werden, werden Microsoft Jet Decimal anstelle von Currency zugeordnet.  
  
 Wenn das extendedansisql-Flag deaktiviert ist, können Sie keine Tabellen mit Decimal-oder numeric-Typen erstellen, und diese Typen werden nicht in SQLGetTypeInfo () angezeigt. Wenn die Tabelle jedoch die neuen Datentypen enthält, können Sie mit den richtigen Datentypen verwendet werden.
