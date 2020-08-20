---
description: Datentypunterstützung
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ab0fd163713a7f6657d8ce446336f5c35a3dd00
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456637"
---
# <a name="data-type-support"></a>Datentypunterstützung
ODBC-Treiber müssen mindestens eine SQL_CHAR und SQL_VARCHAR unterstützen. Die Unterstützung für andere Datentypen wird durch den SQL-92-Konformitäts Grad des Treibers oder der Datenquelle bestimmt. Eine Anwendung sollte **SQLGetTypeInfo** aufrufen, um die vom Treiber unterstützten Datentypen zu bestimmen.  
  
 Weitere Informationen zu-Datentypen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).
