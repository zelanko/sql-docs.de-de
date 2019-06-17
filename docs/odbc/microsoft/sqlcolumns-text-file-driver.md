---
title: SQLColumns (Textdateitreiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLColumns
- SQLColumns function [ODBC], Text File Driver
ms.assetid: c99e5f8d-4e43-48f8-9e0e-086707b411f5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8189a5f6a89f072988404e722a88c29af2d88ca6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62665794"
---
# <a name="sqlcolumns-text-file-driver"></a>SQLColumns (Textdateitreiber)
> [!NOTE]  
>  Dieses Thema enthält die Textdatei-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Spalte|Kommentare|  
|------------|--------------|  
|TABLE_QUALIFIER|Der Pfad zu einem Verzeichnis wird zurückgegeben.|  
|TABLE_OWNER|In dieser Spalte wird NULL zurückgegeben, da der Name des Besitzers nicht unterstützt wird.|  
|NULLABLE|SQL_NO_NULLS wird zurückgegeben, für Spalten, die einbezogen werden, in einer primary key- oder unique-Index.|
