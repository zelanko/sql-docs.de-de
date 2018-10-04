---
title: Aktivieren neuer Datentypen durch Festlegen von ExtendedAnsiSQL | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 80a86ef188796883e76c6d5f6149a3e40afd341b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692159"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Aktivieren neuer Datentypen durch Festlegen von ExtendedAnsiSQL
Zwei neue Datentypen sind in Jet 4.0-Datenbanken verfügbar, wenn das Flag ExtendedAnsiSQL aktiviert ist: SQL_DECIMAL und SQL_NUMERIC. Die standardmäßige Genauigkeit und Dezimalstellenanzahl sind 18 0 (null) bzw. Daten, die über ODBC, die als SQL_DECIMAL oder SQL_NUMERIC typisiert ist zugegriffen werden Microsoft Jet Decimal anstatt Währung zugeordnet werden.  
  
 Wenn das Flag ExtendedAnsiSQL deaktiviert ist, können Sie mit Datentypen decimal und numeric Tabellen können nicht erstellt, und diese Typen nicht in SQLGetTypeInfo() angezeigt. Aber wenn die Tabelle über die neuen Datentypen enthält, können sie mit den richtigen Datentypen verwendet werden.
