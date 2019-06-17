---
title: Beschränkungen in Word reserviert | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 531a100fed389264d9af6a1733636792a3dc7920
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62660942"
---
# <a name="reserved-keyword-limitations"></a>Reserviertes Schlüsselwort-Einschränkungen

Verwenden Sie keine reservierten ODBC-Schlüsselwörter als Bezeichner in Ihrer SQL-Tabellen oder zugehörige Objekte. Wenn ein ungerader Fall auftritt, in dem Sie ein reserviertes Schlüsselwort als Bezeichner verwenden müssen, müssen Sie den Bezeichner umschließen, mit einem Paar von *Graviszeichen* ('). Ein anderer Name für *Graviszeichen* ist *Anführungszeichen Sichern*.

Die Beschränkung auf reserviertes Schlüsselwort gilt auch für alle Kurzschriftform der reservierten Schlüsselwörter verwendet werden.

Eine Liste der reservierten ODBC-Schlüsselwörter finden Sie unter:

- [Reservierte ODBC-Schlüsselwörter](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- In der *ODBC Programmer's Reference Guide*, finden Sie unter [Anhang C: SQL-Grammatik](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).

