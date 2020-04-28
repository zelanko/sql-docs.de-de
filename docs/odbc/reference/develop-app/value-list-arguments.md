---
title: Wertelisten Argumente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], value list
- value list arguments [ODBC]
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fd655bd745c3bb06923e047d4134b286cf64703e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306741"
---
# <a name="value-list-arguments"></a>Argumente der Werteliste
Ein Wert Listen Argument besteht aus einer Liste mit durch Trennzeichen getrennten Werten, die für den Abgleich verwendet werden sollen. In den ODBC-Katalog Funktionen gibt es nur ein Wert Listen Argument: das *TABLETYPE* -Argument in **SQLTables**. Das Festlegen von *TABLETYPE* auf einen NULL-Zeiger ist das gleiche, als ob es auf SQL_ALL_TABLE_TYPES festgelegt ist, das alle möglichen Member der Wertliste auflistet. Dieses Argument wird vom SQL_ATTR_METADATA_ID Statement-Attribut nicht beeinflusst. Weitere Informationen finden Sie in der Beschreibung der [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) -Funktion.
