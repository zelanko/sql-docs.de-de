---
description: SQLColumns (Paradox-Treiber)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee5c823c6b2ee908b61c68f316b9e598f7c386eb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412046"
---
# <a name="sqlcolumns-paradox-driver"></a>SQLColumns (Paradox-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Paradox-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Column|Kommentare|  
|------------|--------------|  
|TABLE_QUALIFIER|Der Pfad zu einem Verzeichnis wird zurückgegeben.|  
|TABLE_OWNER|In dieser Spalte wird NULL zurückgegeben, da der Besitzer Name nicht unterstützt wird.|  
|NULLABLE|SQL_NO_NULLS wird für Spalten zurückgegeben, die an einem Primärschlüssel oder einem eindeutigen Index beteiligt sind.|
