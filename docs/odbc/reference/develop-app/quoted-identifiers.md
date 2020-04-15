---
title: Zitierte Identifikatoren | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], quoted identifiers
- quoted identifiers [ODBC]
ms.assetid: 729ba55f-743b-4a04-8c39-ac0a9914211d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c03fa8bbc059566288997b29c899056f26de252
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282003"
---
# <a name="quoted-identifiers"></a>Bezeichner in Anführungszeichen
In einer SQL-Anweisung müssen Bezeichner, die Sonderzeichen oder Übereinstimmungsschlüsselwörter enthalten, in *Bezeichner-Zitatzeichen*eingeschlossen werden. Bezeichner, die in solchen Zeichen eingeschlossen sind, werden als *zitierte Bezeichner* bezeichnet (in SQL-92 auch als *trennbegrenzte Bezeichner* bezeichnet). Beispielsweise wird der Kreditorenbezeichner in der folgenden **SELECT-Anweisung** angegeben:  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 Der Grund für das Zitieren von Bezeichnern besteht darin, die Anweisung sparierbar zu machen. Wenn z. B. Accounts Payable in der vorherigen Anweisung nicht zitiert wurde, geht der Parser davon aus, dass es zwei Tabellen gibt, Accounts und Payable, und gibt einen Syntaxfehler zurück, dass sie nicht durch ein Komma getrennt wurden. Das Bezeichner-Zitatzeichen ist treiberspezifisch und wird mit der Option SQL_IDENTIFIER_QUOTE_CHAR in **SQLGetInfo**abgerufen. Die Listen mit Sonderzeichen und Schlüsselwörtern werden mit den Optionen SQL_SPECIAL_CHARACTERS und SQL_KEYWORDS in **SQLGetInfo**abgerufen.  
  
 Um sicher zu sein, zitieren interoperable Anwendungen häufig alle Bezeichner mit Ausnahme der Bezeichner für Pseudospalten, z. B. die ROWID-Spalte in Oracle. **SQLSpecialColumns** gibt eine Liste von Pseudospalten zurück. Wenn es anwendungsspezifische Einschränkungen dafür gibt, wo Sonderzeichen in einem Objektnamen angezeigt werden können, ist es für interoperable Anwendungen am besten, keine Sonderzeichen in diesen Positionen zu verwenden.
