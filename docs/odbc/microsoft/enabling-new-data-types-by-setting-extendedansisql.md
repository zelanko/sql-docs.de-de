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
ms.openlocfilehash: 88f11adcab09dbe6964bfd67a944912fc185bccb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031119"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Aktivieren neuer Datentypen durch Festlegen von ExtendedAnsiSQL
Zwei neue Datentypen sind in Jet 4.0-Datenbanken verfügbar, wenn das Flag ExtendedAnsiSQL aktiviert ist: SQL_DECIMAL und SQL_NUMERIC. Die standardmäßige Genauigkeit und Dezimalstellenanzahl sind 18 0 (null) bzw. Daten, die über ODBC, die als SQL_DECIMAL oder SQL_NUMERIC typisiert ist zugegriffen werden Microsoft Jet Decimal anstatt Währung zugeordnet werden.  
  
 Wenn das Flag ExtendedAnsiSQL deaktiviert ist, können Sie mit Datentypen decimal und numeric Tabellen können nicht erstellt, und diese Typen nicht in SQLGetTypeInfo() angezeigt. Aber wenn die Tabelle über die neuen Datentypen enthält, können sie mit den richtigen Datentypen verwendet werden.
