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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 88f11adcab09dbe6964bfd67a944912fc185bccb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68031119"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Aktivieren neuer Datentypen durch Festlegen von ExtendedAnsiSQL
Zwei neue Datentypen sind in Jet 4,0-Datenbanken verfügbar, wenn das extendedansisql-Flag aktiviert ist: SQL_DECIMAL und SQL_NUMERIC. Die Standardgenauigkeit und-Skala sind 18 bzw. 0. Daten, auf die über ODBC zugegriffen wird und die als SQL_DECIMAL oder SQL_NUMERIC typisiert werden, werden Microsoft Jet Decimal anstelle von Currency zugeordnet.  
  
 Wenn das extendedansisql-Flag deaktiviert ist, können Sie keine Tabellen mit Decimal-oder numeric-Typen erstellen, und diese Typen werden nicht in SQLGetTypeInfo () angezeigt. Wenn die Tabelle jedoch die neuen Datentypen enthält, können Sie mit den richtigen Datentypen verwendet werden.
