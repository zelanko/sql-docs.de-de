---
title: SQLSetPos (Desktop-Datenbanktreiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], Desktop Database Drivers
ms.assetid: 8ef027ec-8512-48fe-8fe2-2ff7cd81e331
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e151e3abc4032ea3180e46360c501d9fbea9ae30
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301461"
---
# <a name="sqlsetpos-desktop-database-drivers"></a>SQLSetPos (Desktop-Datenbanktreiber)
Die Massenmodellsemantik für **SQLSetPos-Aufrufe** mit dem *argument irow* gleich 0 wird unterstützt.  
  
 SQL_LOCK_NO_CHANGE wird für *fLock*unterstützt. SQL_LOCK_EXCLUSIVE und SQL_LOCK_UNLOCK werden nicht unterstützt.  
  
 **SQLSetPos** unterstützt aktualisierbare Verknüpfungen. (Weitere Informationen finden Sie im *Microsoft Jet Database Engine Programmer es Guide*.)
