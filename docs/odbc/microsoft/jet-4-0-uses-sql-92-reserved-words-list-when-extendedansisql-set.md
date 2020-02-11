---
title: Jet 4,0 verwendet die Liste der reservierten Wörter von SQL-92, wenn ExtendedAnsiSQL_Set | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 93d23216db950ed861449061f3e35e5e88a637fb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68058788"
---
# <a name="jet-40-uses-sql-92-reserved-words-list-when-extendedansisql_set"></a>Jet 4.0 verwendet die Liste reservierter Wörter von SQL-92 für ExtendedAnsiSQL_Set
Wenn das extendedansisql-Flag aktiviert ist, verwendet Jet 4,0 die Liste der reservierten Wörter von SQL-92. Wenn Sie versuchen, ein reserviertes SQL-92-Wort als Objektnamen ohne Anführungszeichen zu verwenden, führt dies zu einem Syntax Fehler. Wenn das extendedansisql-Flag deaktiviert ist, können die neuen reservierten Wörter wie zuvor als Objektnamen verwendet werden.
