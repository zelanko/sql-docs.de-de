---
title: SQLSetScrollOptions (Desktop-Datenbanktreiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5c47255b455354c49133d61c3546be63ab2380a1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299434"
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (Desktop-Datenbanktreiber)
Vorwärts- und statische Cursor werden für SQL_CONCUR_READ_ONLY unterstützt.  
  
 Nur Keyset-gesteuerte Cursor werden für ein *fConcurrency-Argument* von SQL_CONCUR_LOCK unterstützt.  
  
 Ein *fConcurrency-Argument* von SQL_CONCUR_ROWVER wird nicht unterstützt.  
  
 Dynamische Cursor und gemischte Cursor werden nicht unterstützt.
