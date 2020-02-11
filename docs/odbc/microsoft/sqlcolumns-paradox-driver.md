---
title: SQLColumns (Paradox-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColumns function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLColumns
ms.assetid: d7831c7d-8be9-40a7-bc70-8d89db8fe8c9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1738e17742e61a285a4d2d070b179d2832aaf40f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132513"
---
# <a name="sqlcolumns-paradox-driver"></a>SQLColumns (Paradox-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Paradox-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Column|Kommentare|  
|------------|--------------|  
|TABLE_QUALIFIER|Der Pfad zu einem Verzeichnis wird zurückgegeben.|  
|TABLE_OWNER|In dieser Spalte wird NULL zurückgegeben, da der Besitzer Name nicht unterstützt wird.|  
|NULLABLE|SQL_NO_NULLS wird für Spalten zurückgegeben, die an einem Primärschlüssel oder einem eindeutigen Index beteiligt sind.|
