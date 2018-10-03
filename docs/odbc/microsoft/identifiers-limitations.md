---
title: Einschränkungen von Bezeichnern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c781113124d456e1ba866546d6ada7a17371d71f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667388"
---
# <a name="identifiers-limitations"></a>Einschränkungen für Bezeichner
Wenn ein Bezeichner ein Leerzeichen oder ein Sonderzeichen enthält, muss der Bezeichner in Back Anführungszeichen eingeschlossen werden. Ein gültiger Name ist eine Zeichenfolge mit höchstens 64 Zeichen, von denen das erste Zeichen ein Leerzeichen nicht sein muss. Gültige Namen darf keine Steuerzeichen oder die folgenden Sonderzeichen enthalten: " &#124; # *? [ ] . ! $ .  
  
 Verwenden Sie nicht die reservierten Wörter, in der SQL-Grammatik in Anhang C aufgeführt die *ODBC Programmer's Reference* (oder die Kurzform dieser reservierte Wörter) als Bezeichner (d. h. Tabellen- oder Spaltennamen), es sei denn, Sie umschließen, dass das Wort im Anführungszeichen (').
