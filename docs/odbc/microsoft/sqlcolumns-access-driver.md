---
description: SQLColumns (Access-Treiber)
title: SQLColumns (Zugriffs Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColumns function [ODBC], Access Driver
- Access driver [ODBC], SQLColumns
ms.assetid: 1eac255c-6110-4805-a1bc-feee1eec35d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3fef37db9ae45591b173db8822d17399c257b423
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412176"
---
# <a name="sqlcolumns-access-driver"></a>SQLColumns (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Zugriffs Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Column|Kommentare|  
|------------|--------------|  
|TABLE_QUALIFIER|Der Pfad zu einer Datenbankdatei wird zurückgegeben.|  
|TABLE_OWNER|In dieser Spalte wird NULL zurückgegeben, da der Besitzer Name nicht unterstützt wird.|  
|NULLABLE|SQL_NO_NULLS wird für Spalten zurückgegeben, die an einem Primärschlüssel oder einem eindeutigen Index beteiligt sind.|
