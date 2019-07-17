---
title: SQLColumns (dBASE-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColumns function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLColumns
ms.assetid: 168171de-ab7d-4b5b-af7f-6e2106adfcce
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5afad2cc08910e036a571e3f32b144bc0b922dda
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68132602"
---
# <a name="sqlcolumns-dbase-driver"></a>SQLColumns (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die dBASE-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Spalte|Kommentare|  
|------------|--------------|  
|TABLE_QUALIFIER|Der Pfad zu einem Verzeichnis wird zurückgegeben.|  
|TABLE_OWNER|In dieser Spalte wird NULL zurückgegeben, da der Name des Besitzers nicht unterstützt wird.|  
|NULLABLE|SQL_NO_NULLS wird zurückgegeben, für Spalten, die einbezogen werden, in einer primary key- oder unique-Index.|
