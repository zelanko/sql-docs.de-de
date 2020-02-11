---
title: Mehrere aktive Anweisungen und Verbindungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 76b74ff748a62a401955e4ea4a995f507314124e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942827"
---
# <a name="multiple-active-statements-and-connections"></a>Mehrere aktive Anweisungen und Verbindungen
Einige Treiber und DBMSs schränken die Anzahl der Anweisungen und Verbindungen ein, die gleichzeitig aktiv sein können. Diese Zahlen können so klein wie 1 sein. Weitere Informationen finden Sie unter den Optionen SQL_MAX_CONCURRENT_ACTIVITIES und SQL_MAX_DRIVER_CONNECTIONS in der Beschreibung der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktion und [Anweisungs Handles](../../../odbc/reference/develop-app/statement-handles.md) und [Verbindungs Handles](../../../odbc/reference/develop-app/connection-handles.md).
