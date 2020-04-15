---
title: Mehrere aktive Anweisungen und Verbindungen | Microsoft Docs
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
ms.openlocfilehash: 8259967942f47b06c50a9043158f8b3b45c58d7a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302429"
---
# <a name="multiple-active-statements-and-connections"></a>Mehrere aktive Anweisungen und Verbindungen
Einige Treiber und DBMS begrenzen die Anzahl der Anweisungen und Verbindungen, die gleichzeitig aktiv sein können. Diese Zahlen können so klein wie eine sein. Weitere Informationen finden Sie in den Optionen SQL_MAX_CONCURRENT_ACTIVITIES und SQL_MAX_DRIVER_CONNECTIONS in der [SQLGetInfo-Funktionsbeschreibung](../../../odbc/reference/syntax/sqlgetinfo-function.md) sowie [in den Anweisungshandles](../../../odbc/reference/develop-app/statement-handles.md) und [Verbindungshandles](../../../odbc/reference/develop-app/connection-handles.md).
