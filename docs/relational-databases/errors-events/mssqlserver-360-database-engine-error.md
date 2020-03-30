---
title: MSSQLSERVER_360 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a25f3809221476c2cc4f80bae42d1e0b38a83429
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68043594"
---
# <a name="mssqlserver_360"></a>MSSQLSERVER_360
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|360|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DML_UPDATE_SPARSE_AND_COLSET|  
|Meldungstext|Die Zielspaltenliste einer INSERT-, UPDATE- oder MERGE-Anweisung kann nicht sowohl eine Sparsespalte als auch den Spaltensatz enthalten, in dem sich die Sparsespalte befindet. Schreiben Sie die Anweisung um, sodass entweder nur die Sparsespalte oder nur der Spaltensatz enthalten ist.|  
  
## <a name="explanation"></a>Erklärung  
Ein Spaltensatz ist eine nicht typisierte XML-Darstellung, in der einige Spalten einer Tabelle zu einer strukturierten Ausgabe zusammengefasst werden. Es wurde versucht, sowohl den Spaltensatz als auch eine Spalte aus dem Spaltensatz zu ändern, sodass zwei Verweise auf die gleiche Spalte entstanden.  
  
## <a name="user-action"></a>Benutzeraktion  
Schreiben Sie die Anweisung um, sodass Verweise auf entweder die Spalte mit geringer Dichte oder auf den Spaltensatz enthalten sind. Schließen Sie jedoch keinesfalls beide in die Anweisung ein.  
  
