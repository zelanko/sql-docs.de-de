---
title: Proaktives Zwischenspeichern (Dimensionen) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: db9b77c799f674b39f3c6a66a6812464896abefc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="proactive-caching-dimensions"></a>Proaktives Zwischenspeichern (Dimensionen)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Proaktives Zwischenspeichern ermöglicht automatische MOLAP-Cacheerstellung und die Verwaltung von OLAP-Objekten. Cubes integrieren auf der Grundlage der von der Datenbank empfangenen Benachrichtigungen unverzüglich die Änderungen, die an den Daten in der Datenbank vorgenommen wurden. Das Ziel der proaktiven Zwischenspeicherung ist die Bereitstellung der Leistung von herkömmlichem MOLAP, während die Unmittelbarkeit und die einfache Handhabung von ROLAP erhalten bleibt.  
  
 Ein einfaches <xref:Microsoft.AnalysisServices.ProactiveCaching>-Objekt besteht aus: Zeitsteuerungsspezifikation und Tabellenbenachrichtigung. Die Zeitsteuerungsspezifikation definiert den zeitlichen Rahmen zum Aktualisieren des Caches, nachdem eine Änderungsbenachrichtigung empfangen wurde. Die Tabellenbenachrichtigung definiert das Benachrichtigungsschema zwischen der Datentabelle und dem <xref:Microsoft.AnalysisServices.ProactiveCaching>-Objekt.  
  
  
