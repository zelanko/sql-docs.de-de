---
title: SQLColumns (Textdateitreiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 78c2e20f12dedf399ab36dd908f83aa93bebffc4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307866"
---
# <a name="sqlcolumns-text-file-driver"></a>SQLColumns (Textdateitreiber)
> [!NOTE]  
>  Dieses Thema enthält Textdateitreiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Column|Kommentare|  
|------------|--------------|  
|TABLE_QUALIFIER|Der Pfad zu einem Verzeichnis wird zurückgegeben.|  
|TABLE_OWNER|NULL wird in dieser Spalte zurückgegeben, da der Besitzername nicht unterstützt wird.|  
|NULLABLE|SQL_NO_NULLS wird für Spalten zurückgegeben, die an einem Primärschlüssel oder eindeutigen Index beteiligt sind.|
