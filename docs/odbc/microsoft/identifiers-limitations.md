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
ms.openlocfilehash: 251ae0e4e94cec903e2c4b5cf687ed9b8b41dfc8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952391"
---
# <a name="identifiers-limitations"></a>Einschränkungen für Bezeichner
Wenn ein Bezeichner ein Leerzeichen oder ein Sonderzeichen enthält, muss der Bezeichner in Back Anführungszeichen eingeschlossen werden. Ein gültiger Name ist eine Zeichenfolge mit höchstens 64 Zeichen, von denen das erste Zeichen ein Leerzeichen nicht sein muss. Gültige Namen darf keine Steuerzeichen oder die folgenden Sonderzeichen enthalten: " &#124; # *? [ ] . ! $ .  
  
 Verwenden Sie nicht die reservierten Wörter, in der SQL-Grammatik in Anhang C aufgeführt die *ODBC Programmer's Reference* (oder die Kurzform dieser reservierte Wörter) als Bezeichner (d. h. Tabellen- oder Spaltennamen), es sei denn, Sie umschließen, dass das Wort im Anführungszeichen (').
