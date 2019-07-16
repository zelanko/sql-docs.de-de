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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081908"
---
# <a name="create-index-statement"></a>CREATE INDEX-Anweisung
Die Syntax der CREATE INDEX-Anweisung ist:  
  
 Erstellen [UNIQUE] INDEX *Indexname* ON *Tabellenname* (*Spaltenbezeichner* [ASC] [DESC] [, *Spaltenbezeichner* [ASC][DESC]...]) MIT \< *Optionsliste für Index*>  
  
 in denen \< *Index Optionsliste*> kann sein: PRIMÄRE &#124; DISALLOW NULL &#124; IGNORIEREN NULL  
  
 Nur der Microsoft Access-Treiber verwendet die Optionen für die NULL nicht zulassen und ignorieren NULL-Index. Die Access und Paradox-Treiber die Syntax akzeptiert, aber ignorieren das Vorhandensein der beiden Optionen.  
  
 Wenn die Paradox-Treiber verwendet wird, erstellt die CREATE INDEX-Anweisung Paradox-Dateien mit Schlüsseln von primären und sekundären Dateien.  
  
 Diese Anweisung wird durch die Microsoft Excel- oder Textdateien Treiber nicht unterstützt.
