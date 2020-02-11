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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ad15ad436b0f34f00acbd75e371e998183f22d2f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081908"
---
# <a name="create-index-statement"></a>CREATE INDEX-Anweisung
Die Syntax der CREATE INDEX-Anweisung lautet wie folgt:  
  
 Create [Unique] Index *Index-Name* für *Tabellenname* (*Spalten Bezeichner* [ASC] [ABSC] [, *Spalten Bezeichner* [ASC] [de]...]) WITH \< *Index-Optionsliste*>  
  
 die \< *Liste der Index Optionen* kann> lauten: primär &#124; NULL nicht zulassen &#124; NULL ignorieren.  
  
 Nur der Microsoft Access-Treiber verwendet die Optionen unallow NULL und NULL Index ignorieren. Der dBASE-und der Paradox-Treiber akzeptieren die Syntax, ignorieren jedoch das vorhanden sein einer der beiden Optionen.  
  
 Wenn der Paradox-Treiber verwendet wird, werden von der CREATE INDEX-Anweisung paradoxe Primärschlüssel Dateien und sekundäre Dateien erstellt.  
  
 Diese Anweisung wird von Microsoft Excel oder Text Treibern nicht unterstützt.
