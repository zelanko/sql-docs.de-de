---
title: SQLSetPos (Desktop-Datenbanktreiber) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301461"
---
# <a name="sqlsetpos-desktop-database-drivers"></a>SQLSetPos (Desktop-Datenbanktreiber)
Die Semantik für das Massenmodell von **SQLSetPos** -aufrufen mit dem *IRow* -Argument gleich 0 wird unterstützt.  
  
 SQL_LOCK_NO_CHANGE wird für die *Herde*unterstützt. SQL_LOCK_EXCLUSIVE und SQL_LOCK_UNLOCK werden nicht unterstützt.  
  
 **SQLSetPos** unterstützt aktualisierbare Joins. (Weitere Informationen finden Sie im *Microsoft Jet Datenbank-Engine Programmer es Guide*.)
