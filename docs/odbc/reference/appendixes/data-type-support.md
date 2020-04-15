---
title: Datentyp-Support | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3abfe85ee32fb9ff4a8499c9949c0685563fec70
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284427"
---
# <a name="data-type-support"></a>Datentypunterstützung
ODBC-Treiber müssen mindestens einen SQL_CHAR und SQL_VARCHAR unterstützen. Die Unterstützung für andere Datentypen wird durch die SQL-92-Konformitätsstufe des Treibers oder der Datenquelle bestimmt. Eine Anwendung sollte **SQLGetTypeInfo** aufrufen, um die vom Treiber unterstützten Datentypen zu bestimmen.  
  
 Weitere Informationen zu Datentypen finden Sie in [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).
