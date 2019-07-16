---
title: Groß-und Kleinschreibung | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138974"
---
# <a name="identifier-case"></a>Groß-/Kleinschreibung von Bezeichnern
In SQL-Anweisungen und Katalog-Funktionsargumente, Bezeichner und Bezeichner in Anführungszeichen können es sich entweder Groß-/Kleinschreibung oder nicht, die ermittelt eine Anwendung, durch den Aufruf **SQLGetInfo** mit dem SQL_IDENTIFIER_CASE und SQL_QUOTED_ IDENTIFIER_CASE-Optionen.  
  
 Jede dieser Optionen hat vier mögliche Rückgabewerte: eine mit dem Hinweis, dass der Bezeichner oder Bezeichner in Anführungszeichen Groß-/Kleinschreibung beachtet wird und drei mit dem Hinweis, dass er nicht vertraulich ist. Weitere beschrieben, die drei Werte, die Groß-/ nicht Kleinschreibung den Fall, in dem Bezeichner im Systemkatalog gespeichert sind. Wie die Bezeichner im Systemkatalog gespeichert werden, gilt nur zu Anzeigezwecken, z. B. wenn eine Anwendung angezeigt wird, die Ergebnisse einer Katalog-Funktion; Er ändert nicht die Kleinschreibung von Bezeichnern.
