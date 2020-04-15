---
title: SQLSpecialColumns (Desktop-Datenbanktreiber) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299390"
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (Desktop-Datenbanktreiber)
Für das SQL_BEST_ROWID-Flag in *fColType*wird ein eindeutiger Index zurückgegeben (sofern vorhanden). Für das SQL_ROWVER-Flag wird kein Resultset zurückgegeben.  
  
 Alle Zeilen-IDs haben einen SQL_SCOPE_CURROW.-Bereich.  
  
 Der Musterabgleich wird weder für das Argument *szTableQualifier* noch *szTableName* unterstützt.
