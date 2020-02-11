---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c884d8594c3c4511bed0e24f9b3dd43092176b4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67988028"
---
# <a name="reserved-keyword-limitations"></a>Einschränkungen von reservierten Schlüsselwörtern

Vermeiden Sie die Verwendung von reservierten ODBC-Schlüsselwörtern als Bezeichner in Ihren SQL-Tabellen oder verwandten Objekten. Wenn ein ungerade Fall auftritt, bei dem Sie ein reserviertes Schlüsselwort als Bezeichner verwenden müssen, müssen Sie den Bezeichner mit einem Paar von *Graviszeichen* (') umschließen. Ein weiterer Name für das *Graviszeichen* ist das *Rück Anführungs*Zeichen.

Die Einschränkung des reservierten Schlüssel Worts gilt auch für beliebige Kurzformen der reservierten Schlüsselwörter.

Eine Liste der reservierten ODBC-Schlüsselwörter finden Sie unter:

- [Reservierte ODBC-Schlüsselwörter](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- Informationen zum *ODBC Programmer es Reference Guide*finden Sie unter [Anhang C: SQL-Grammatik](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).

