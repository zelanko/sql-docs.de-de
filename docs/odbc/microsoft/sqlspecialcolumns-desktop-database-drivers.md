---
title: SQLSpecialColumns (Desktop-Datenbanktreiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Desktop Database Drivers
ms.assetid: 3de66fdf-053b-4354-979d-e76a5a5e975f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e530d0b16811cdf25a5bc1d99f5386efdb55ccd4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905328"
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (Desktop-Datenbanktreiber)
Ein eindeutiger Index wird (sofern vorhanden) für das SQL_BEST_ROWID-Flag in " *f Type*" zurückgegeben. Für das SQL_ROWVER-Flag wird kein Resultset zurückgegeben.  
  
 Alle Zeilen-IDs haben den Bereich SQL_SCOPE_CURROW.  
  
 Der Musterabgleich wird weder für das *sztablequalifier* -Argument noch für das *sztablename* -Argument unterstützt.
