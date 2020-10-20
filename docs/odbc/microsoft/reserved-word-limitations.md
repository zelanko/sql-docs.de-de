---
description: Einschränkungen von reservierten Schlüsselwörtern
title: Einschränkungen für reservierte Wörter | Microsoft-Dokumentation
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
ms.openlocfilehash: 15033816b953df764126853ada353452f00650d6
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196174"
---
# <a name="reserved-keyword-limitations"></a>Einschränkungen von reservierten Schlüsselwörtern

Vermeiden Sie die Verwendung von reservierten ODBC-Schlüsselwörtern als Bezeichner in Ihren SQL-Tabellen oder verwandten Objekten. Wenn ein ungerade Fall auftritt, bei dem Sie ein reserviertes Schlüsselwort als Bezeichner verwenden müssen, müssen Sie den Bezeichner mit einem Paar von *Graviszeichen* (') umschließen. Ein weiterer Name für das *Graviszeichen* ist das *Rück Anführungs*Zeichen.

Die Einschränkung des reservierten Schlüssel Worts gilt auch für beliebige Kurzformen der reservierten Schlüsselwörter.

Eine Liste der reservierten ODBC-Schlüsselwörter finden Sie unter:

- [Reservierte ODBC-Schlüsselwörter](../reference/appendixes/reserved-keywords.md).

- Informationen zum *ODBC Programmer es Reference Guide*finden Sie unter [Anhang C: SQL-Grammatik](../reference/appendixes/appendix-c-sql-grammar.md).