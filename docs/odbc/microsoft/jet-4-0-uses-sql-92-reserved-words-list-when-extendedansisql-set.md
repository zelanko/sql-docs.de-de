---
title: Jet 4.0 verwendet SQL-92 Reserved Words List, wenn ExtendedAnsiSQL_Set | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], reserved words
ms.assetid: 7645187e-7777-4c07-9686-0a80d5c5834d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6988e0da1ecb881e0f6e88e35b66f1a6284f9b7a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299960"
---
# <a name="jet-40-uses-sql-92-reserved-words-list-when-extendedansisql_set"></a>Jet 4.0 verwendet die Liste reservierter Wörter von SQL-92 für ExtendedAnsiSQL_Set
Wenn das ExtendedAnsiSQL-Flag aktiviert ist, verwendet Jet 4.0 die SQL-92-Liste der reservierten Wörter. Der Versuch, ein reserviertes SQL-92-Wort als nicht zitierten Objektnamen zu verwenden, führt zu einem Syntaxfehler. Wenn das ExtendedAnsiSQL-Flag deaktiviert ist, können die neuen reservierten Wörter wie zuvor als Objektnamen verwendet werden.
