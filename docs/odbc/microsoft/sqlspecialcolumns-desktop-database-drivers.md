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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5f8cd4ed0912f9f1e71d64b32449b5d46f9ef1a3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299390"
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (Desktop-Datenbanktreiber)
Ein eindeutiger Index wird (sofern vorhanden) für das SQL_BEST_ROWID-Flag in " *f Type*" zurückgegeben. Für das SQL_ROWVER-Flag wird kein Resultset zurückgegeben.  
  
 Alle Zeilen-IDs haben den Bereich SQL_SCOPE_CURROW.  
  
 Der Musterabgleich wird weder für das *sztablequalifier* -Argument noch für das *sztablename* -Argument unterstützt.
