---
title: SQL_ARD_TYPE | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d7e28d6babb7db8364697ae62092256396b44914
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305031"
---
# <a name="sql_ard_type"></a>SQL_ARD_TYPE
Der SQL_ARD_TYPE Typbezeichner wird verwendet, um anzugeben, dass die Daten in einem Puffer vom Typ sein, der im SQL_DESC_CONCISE_TYPE Feld der ARD angegeben ist. SQL_ARD_TYPE wird im *TargetType-Argument* eines Aufrufs von **SQLGetData** anstelle eines bestimmten Datentyps eingegeben und ermöglicht es einer Anwendung, den Datentyp des Puffers zu ändern, indem sie das Deskriptorfeld ändert. Dieser Wert bindet den Datentyp des * \*TargetValuePtr-Puffers* an das Deskriptorfeld. (SQL_ARD_TYPE wird nicht in einem Aufruf von **SQLBindCol** oder **SQLBindParameter** eingegeben, da der Typ des gebundenen Puffers bereits an die Felder SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE gebunden ist und jederzeit durch Ändern eines dieser Felder geändert werden kann.)  
  
 Der SQL_ARD_TYPE Typbezeichner kann verwendet werden, um nicht standardmäßige Werte für die führende Genauigkeit und Sekundengenauigkeit von Intervalldatentypen sowie Genauigkeits- und Skalierungswerte für den SQL_C_NUMERIC Datentyp anzugeben. Weitere Informationen finden Sie weiter unten in diesem Anhang unter Überschreiben der [Standard-Leading- und Seconds-Präzision für Intervalldatentypen](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md) und [überschreibende Standardgenauigkeit und Skalierung für numerische Datentypen.](../../../odbc/reference/appendixes/overriding-default-precision-and-scale-for-numeric-data-types.md)
