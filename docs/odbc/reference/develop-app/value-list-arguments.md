---
description: Argumente der Werteliste
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
ms.openlocfilehash: fd2f2e970ea94635cda0b43b741abfda1130645b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421414"
---
# <a name="value-list-arguments"></a>Argumente der Werteliste
Ein Wert Listen Argument besteht aus einer Liste mit durch Trennzeichen getrennten Werten, die für den Abgleich verwendet werden sollen. In den ODBC-Katalog Funktionen gibt es nur ein Wert Listen Argument: das *TABLETYPE* -Argument in **SQLTables**. Das Festlegen von *TABLETYPE* auf einen NULL-Zeiger ist das gleiche, als ob es auf SQL_ALL_TABLE_TYPES festgelegt ist, das alle möglichen Member der Wertliste auflistet. Dieses Argument wird vom SQL_ATTR_METADATA_ID Statement-Attribut nicht beeinflusst. Weitere Informationen finden Sie in der Beschreibung der [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) -Funktion.
