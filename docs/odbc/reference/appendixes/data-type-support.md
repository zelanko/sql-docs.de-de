---
title: Unterstützung von Datentypen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b5fe4081d0786ace40dd027606a830982798075e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68044947"
---
# <a name="data-type-support"></a>Datentypunterstützung
ODBC-Treiber müssen mindestens eine SQL_CHAR und SQL_VARCHAR unterstützen. Die Unterstützung für andere Datentypen wird durch den SQL-92-Konformitäts Grad des Treibers oder der Datenquelle bestimmt. Eine Anwendung sollte **SQLGetTypeInfo** aufrufen, um die vom Treiber unterstützten Datentypen zu bestimmen.  
  
 Weitere Informationen zu-Datentypen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).
