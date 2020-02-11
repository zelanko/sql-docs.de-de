---
title: SQLSetScrollOptions (Desktop-Datenbanktreiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0adedfb69cd4a7b5cf195916747687826805e8bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905394"
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (Desktop-Datenbanktreiber)
Forward-und static-Cursor werden für SQL_CONCUR_READ_ONLY unterstützt.  
  
 Nur keysetgesteuerte Cursor werden für ein Argument vom Typ " *f* " der SQL_CONCUR_LOCK unterstützt.  
  
 Ein *"* SQL_CONCUR_ROWVER"-Argument wird nicht unterstützt.  
  
 Dynamische Cursor und gemischte Cursor werden nicht unterstützt.
