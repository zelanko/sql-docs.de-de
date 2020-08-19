---
description: Mehrere aktive Anweisungen und Verbindungen
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 56897dedbd1bf0d96dfa73f75a28db5f1ca46c43
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429262"
---
# <a name="multiple-active-statements-and-connections"></a>Mehrere aktive Anweisungen und Verbindungen
Einige Treiber und DBMSs schränken die Anzahl der Anweisungen und Verbindungen ein, die gleichzeitig aktiv sein können. Diese Zahlen können so klein wie 1 sein. Weitere Informationen finden Sie unter den Optionen SQL_MAX_CONCURRENT_ACTIVITIES und SQL_MAX_DRIVER_CONNECTIONS in der Beschreibung der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktion und [Anweisungs Handles](../../../odbc/reference/develop-app/statement-handles.md) und [Verbindungs Handles](../../../odbc/reference/develop-app/connection-handles.md).
