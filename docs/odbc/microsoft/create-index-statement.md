---
description: CREATE INDEX-Anweisung
title: CREATE INDEX-Anweisung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7a3f5a13624cdb137e8c86cf2c27044c6705298f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483633"
---
# <a name="create-index-statement"></a>CREATE INDEX-Anweisung
Die Syntax der CREATE INDEX-Anweisung lautet wie folgt:  
  
 Create [Unique] Index *Index-Name* für *Tabellenname* (*Spalten Bezeichner* [ASC] [ABSC] [, *Spalten Bezeichner* [ASC] [de]...]) Entspricht \<*index option list*>  
  
 Where \<*index option list*> kann sein: Primary &#124; NULL nicht zulassen &#124; NULL ignorieren.  
  
 Nur der Microsoft Access-Treiber verwendet die Optionen unallow NULL und NULL Index ignorieren. Der dBASE-und der Paradox-Treiber akzeptieren die Syntax, ignorieren jedoch das vorhanden sein einer der beiden Optionen.  
  
 Wenn der Paradox-Treiber verwendet wird, werden von der CREATE INDEX-Anweisung paradoxe Primärschlüssel Dateien und sekundäre Dateien erstellt.  
  
 Diese Anweisung wird von Microsoft Excel oder Text Treibern nicht unterstützt.
