---
title: Wertlistenargumente | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306741"
---
# <a name="value-list-arguments"></a>Argumente der Werteliste
Ein Wertlistenargument besteht aus einer Liste von durch Kommas getrennten Werten, die für den Abgleich verwendet werden sollen. Es gibt nur ein Wertlistenargument in den ODBC-Katalogfunktionen: das *TableType-Argument* in **SQLTables**. Das Festlegen von *TableType* auf einen Nullzeiger entspricht dem Wert, ob er auf SQL_ALL_TABLE_TYPES festgelegt ist, der alle möglichen Member der Wertliste auflistet. Dieses Argument wird vom Attribut SQL_ATTR_METADATA_ID-Anweisung nicht beeinflusst. Weitere Informationen finden Sie in der [SQLTables-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqltables-function.md)
