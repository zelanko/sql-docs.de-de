---
title: CREATE INDEX-Anweisung | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280970"
---
# <a name="create-index-statement"></a>CREATE INDEX-Anweisung
Die Syntax der CREATE INDEX-Anweisung lautet:  
  
 CREATE [UNIQUE] INDEX *Indexname* ON *Tabellenname* (*Spaltenbezeichner* [ASC][DESC][, *Spaltenbezeichner* [ASC][DESC]...]) WITH \< *Indexoptionsliste*>  
  
 Wobei \< *Indexoptionsliste*> sein kann: PRIMARY &#124; DISALLOW NULL &#124; IGNORE NULL  
  
 Nur der Microsoft Access-Treiber verwendet die Indexoptionen DISALLOW NULL und IGNORE NULL. Die Treiber dBASE und Paradox akzeptieren die Syntax, ignorieren jedoch das Vorhandensein einer der beiden Optionen.  
  
 Wenn der Paradox-Treiber verwendet wird, erstellt die CREATE INDEX-Anweisung Paradox Primärschlüsseldateien und sekundäre Dateien.  
  
 Diese Anweisung wird von den Microsoft Excel- oder Texttreibern nicht unterstützt.
