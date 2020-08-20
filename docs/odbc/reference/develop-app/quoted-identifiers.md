---
description: Bezeichner in Anführungszeichen
title: Bezeichner in Anführungszeichen | Microsoft-Dokumentation
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
ms.openlocfilehash: cd317e5d92618d8b458d6d28fa870c6945e136fd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465680"
---
# <a name="quoted-identifiers"></a>Bezeichner in Anführungszeichen
In einer SQL-Anweisung müssen Bezeichner mit Sonderzeichen oder Match-Schlüsselwörtern in *bezeichneranführungs Zeichen*eingeschlossen werden. in diesen Zeichen eingeschlossene Bezeichner werden als Bezeichner in Anführungs *Zeichen (auch als* *Begrenzungs* Bezeichner bezeichnet in SQL-92) bezeichnet. Beispielsweise wird der Bezeichner für die Konten Kennung in der folgenden **Select** -Anweisung angegeben:  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 Der Grund für das Zitieren von bezeichgern besteht darin, die Anweisung zu erstellen. Wenn z. b. Konten in der vorherigen Anweisung nicht in Anführungszeichen eingeschlossen wurden, nimmt der Parser an, dass zwei Tabellen, Konten und kostenpflichtig sind, und gibt einen Syntax Fehler zurück, der nicht durch ein Komma getrennt wurde. Das bezeichneranführungs Zeichen ist Treiber spezifisch und wird mit der SQL_IDENTIFIER_QUOTE_CHAR-Option in **SQLGetInfo**abgerufen. Die Listen der Sonderzeichen und der Schlüsselwörter werden mit den Optionen SQL_SPECIAL_CHARACTERS und SQL_KEYWORDS in **SQLGetInfo**abgerufen.  
  
 Um sicher zu sein, werden interoperable Anwendungen häufig alle Bezeichner mit Ausnahme derjenigen für Pseudo Spalten, wie z. b. die ROWID-Spalte in Oracle, angeben. **SQLSpecialColumns** gibt eine Liste von Pseudo Spalten zurück. Wenn anwendungsspezifische Einschränkungen in Bezug auf die Verwendung von Sonderzeichen in einem Objektnamen vorliegen, empfiehlt es sich für interoperable Anwendungen am besten, in diesen Positionen keine Sonderzeichen zu verwenden.
