---
title: SQL_ARD_TYPE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], SQL_ARD_TYPE
- SQL_ARD_TYPE [ODBC]
ms.assetid: 8d87ca10-f955-4284-8689-e9f4cc31e7ae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 802040851259a8537fabcd3cc0da1afdf9b8dbe0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057056"
---
# <a name="sqlardtype"></a>SQL_ARD_TYPE
Der Typbezeichner SQL_ARD_TYPE wird verwendet, um anzugeben, dass die Daten in einem Puffer des Typs in das Feld SQL_DESC_CONCISE_TYPE der ARD angegeben werden. SQL_ARD_TYPE eingegeben wird, der *TargetType* Argument eines Aufrufs von **SQLGetData** anstelle von einem bestimmten Datentyp und geben Sie eine Anwendung so ändern Sie die Daten des Puffers durch Ändern des Deskriptors aktiviert Feld. Dieser Wert verknüpft, den den Datentyp des der  *\*TargetValuePtr* Puffer, in das Deskriptorfeld. (SQL_ARD_TYPE wird nicht in einem Aufruf von eingegeben **SQLBindCol** oder **SQLBindParameter** daran, dass der Typ des gebundenen Puffer bereits an den SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE gebunden ist und geändert werden kann zu einem beliebigen Zeitpunkt durch eines dieser Felder ändern.)  
  
 Der Typbezeichner SQL_ARD_TYPE kann verwendet werden, um benutzerdefinierte Werte für die führende Genauigkeit und die Genauigkeit des Datentyps Interval angeben, und geben Sie die Genauigkeit und Dezimalstellenanzahl Werte für die SQL_C_NUMERIC-Daten. Weitere Informationen finden Sie unter [überschreiben führende Standard und Genauigkeit der Sekunden für Intervalldatentypen](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md) und [überschreiben standardmäßig Genauigkeit und Dezimalstellenanzahl für numerische Datentypen](../../../odbc/reference/appendixes/overriding-default-precision-and-scale-for-numeric-data-types.md)weiter unten in diesem Anhang.
