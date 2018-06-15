---
title: Aktivieren neue Datentypen durch Festlegen von ExtendedAnsiSQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], enabling new data types
ms.assetid: f2865543-7fff-44fa-9a6a-968bec33acdc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c9f7c4c66bebb2404ef8477ed85e0f36edc1407
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32902495"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Neue Datentypen aktivieren durch Festlegen von ExtendedAnsiSQL
Zwei neue Datentypen sind in Jet 4.0-Datenbanken verfügbar, wenn das ExtendedAnsiSQL-Flag aktiviert ist: SQL_DECIMAL und SQL_NUMERIC. Die standardmäßige Genauigkeit und Dezimalstellenanzahl sind 18 und 0 (null) bzw. Daten, die über ODBC, der als SQL_DECIMAL oder SQL_NUMERIC eingegeben wird zugegriffen werden Microsoft Jet Decimal anstatt Währung zugeordnet werden.  
  
 Wenn das Flag ExtendedAnsiSQL deaktiviert ist, Tabellen mit Datentypen decimal und numeric kann nicht erstellt werden können, und diese Typen nicht in SQLGetTypeInfo() angezeigt. Jedoch, wenn die Tabelle die neuen Datentypen enthält, können sie mit den richtigen Datentypen verwendet werden.
