---
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
ms.openlocfilehash: c6aa512ff789fcbd00f45f84fb194d4ab3f5da07
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280970"
---
# <a name="create-index-statement"></a>CREATE INDEX-Anweisung
Die Syntax der CREATE INDEX-Anweisung lautet wie folgt:  
  
 Create [Unique] Index *Index-Name* für *Tabellenname* (*Spalten Bezeichner* [ASC] [ABSC] [, *Spalten Bezeichner* [ASC] [de]...]) WITH \< *Index-Optionsliste*>  
  
 die \< *Liste der Index Optionen* kann> lauten: primär &#124; NULL nicht zulassen &#124; NULL ignorieren.  
  
 Nur der Microsoft Access-Treiber verwendet die Optionen unallow NULL und NULL Index ignorieren. Der dBASE-und der Paradox-Treiber akzeptieren die Syntax, ignorieren jedoch das vorhanden sein einer der beiden Optionen.  
  
 Wenn der Paradox-Treiber verwendet wird, werden von der CREATE INDEX-Anweisung paradoxe Primärschlüssel Dateien und sekundäre Dateien erstellt.  
  
 Diese Anweisung wird von Microsoft Excel oder Text Treibern nicht unterstützt.
