---
description: Groß-/Kleinschreibung von Bezeichnern
title: Bezeichnerfall | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ccac9b10e6a32c7265cd5f591944735454b85f80
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461442"
---
# <a name="identifier-case"></a>Groß-/Kleinschreibung von Bezeichnern
In SQL-Anweisungen und Catalog-Funktions Argumenten können Bezeichner und Bezeichner in Anführungszeichen entweder die Groß-/Kleinschreibung beachten oder nicht, die eine Anwendung durch Aufrufen von **SQLGetInfo** mit den Optionen SQL_IDENTIFIER_CASE und SQL_QUOTED_IDENTIFIER_CASE bestimmen kann.  
  
 Jede dieser Optionen hat vier mögliche Rückgabewerte: ein Wert, der angibt, dass der Bezeichner oder Bezeichner in Anführungszeichen vertraulich ist und drei besagt, dass er nicht vertraulich ist. Die drei Werte, bei denen die Groß-/Kleinschreibung nicht beachtet wird, beschreiben den Fall, in dem Bezeichner im System Katalog gespeichert werden. Die Art und Weise, wie Bezeichner im System Katalog gespeichert werden, ist nur für Anzeigezwecke relevant, z. b. Wenn eine Anwendung die Ergebnisse einer Katalog Funktion anzeigt. die Groß-/Kleinschreibung von bezeichatoren wird nicht geändert.
