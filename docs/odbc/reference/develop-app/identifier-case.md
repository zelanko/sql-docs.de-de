---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 70728908f081ab89e08cad1265f04394f29b66ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138974"
---
# <a name="identifier-case"></a>Groß-/Kleinschreibung von Bezeichnern
In SQL-Anweisungen und Catalog-Funktions Argumenten können Bezeichner und Bezeichner in Anführungszeichen entweder die Groß-/Kleinschreibung beachten oder nicht, die eine Anwendung durch Aufrufen von **SQLGetInfo** mit den Optionen SQL_IDENTIFIER_CASE und SQL_QUOTED_IDENTIFIER_CASE bestimmen kann.  
  
 Jede dieser Optionen hat vier mögliche Rückgabewerte: ein Wert, der angibt, dass der Bezeichner oder Bezeichner in Anführungszeichen vertraulich ist und drei besagt, dass er nicht vertraulich ist. Die drei Werte, bei denen die Groß-/Kleinschreibung nicht beachtet wird, beschreiben den Fall, in dem Bezeichner im System Katalog gespeichert werden. Die Art und Weise, wie Bezeichner im System Katalog gespeichert werden, ist nur für Anzeigezwecke relevant, z. b. Wenn eine Anwendung die Ergebnisse einer Katalog Funktion anzeigt. die Groß-/Kleinschreibung von bezeichatoren wird nicht geändert.
