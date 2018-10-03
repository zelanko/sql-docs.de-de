---
title: Wert der Argumente der Wertliste | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a971da68a8f2a35df8fa513e68d1eba127e9c430
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695710"
---
# <a name="value-list-arguments"></a>Argumente der Werteliste
Eine Liste Wertargument besteht aus einer Liste von durch Trennzeichen getrennte Werte, die für den Abgleich verwendet werden. In der ODBC-Katalogfunktionen Listenargument nur ein Wert vorliegt: die *TableType* -Argument in **SQLTables**. Festlegen von *TableType* auf einen null-Zeiger ist identisch, als ob er auf SQL_ALL_TABLE_TYPES, festgelegt ist, der alle verfügbaren Elemente der Werteliste aufgeführt. Dieses Argument ist das SQL_ATTR_METADATA_ID-Anweisungsattribut nicht betroffen. Weitere Informationen finden Sie unter den [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) funktionsbeschreibung.
