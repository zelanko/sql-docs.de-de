---
description: Einschränkungen der WHERE-Klausel
title: Einschränkungen der WHERE-Klausel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, WHERE clause limitations
- WHERE clause limitations [ODBC]
ms.assetid: 46b54f74-e4a3-4318-87cf-8a97c38a2718
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8b6b9e72176f447c71daccfbd0393f414558d49d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466282"
---
# <a name="where-clause-limitations"></a>Einschränkungen der WHERE-Klausel
Die maximale Anzahl von Klauseln in einer WHERE-Klausel ist 40.  
  
 Die Spalten LONGVARBINARY und LONGVARCHAR können mit literalen von bis zu 255 Zeichen verglichen werden, können aber nicht mit Parametern verglichen werden.
