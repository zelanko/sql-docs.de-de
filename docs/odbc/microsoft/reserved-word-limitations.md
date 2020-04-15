---
title: Reservierte Wortbeschränkungen | Microsoft Docs
ms.custom: ''
ms.date: 05/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ed42f083-c9e8-4ee4-9d64-d879bf955c78
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf536e06556e6b2e7b27f220d09a51f91b44d23c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304008"
---
# <a name="reserved-keyword-limitations"></a>Reservierte Keyword-Beschränkungen

Vermeiden Sie die Verwendung reservierter ODBC-Schlüsselwörter als Bezeichner in Ihren SQL-Tabellen oder verwandten Objekten. Wenn ein ungerader Fall auftritt, in dem Sie ein reserviertes Schlüsselwort als Bezeichner verwenden müssen, müssen Sie den Bezeichner mit einem Paar *Backticks* (') umgeben. Ein anderer Name für *backtick* ist *back quote*.

Die reservierte Keyword-Beschränkung gilt auch für jede Kurzform der reservierten Keywords.

Eine Liste der reservierten ODBC-Schlüsselwörter finden Sie unter:

- [ODBC Reserved Keywords](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- Im *Referenzhandbuch des ODBC-Programmierers*siehe [Anhang C: SQL Grammar](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).

