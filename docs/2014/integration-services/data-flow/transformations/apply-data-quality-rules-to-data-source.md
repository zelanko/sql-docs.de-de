---
title: Anwenden von Datenqualitätsregeln auf eine Datenquelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d59e6fb5ffb752b3346d40740e0b841bf574344e
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85431037"
---
# <a name="apply-data-quality-rules-to-data-source"></a>Anwenden von Datenqualitätsregeln auf eine Datenquelle
  Sie können mit Data Quality Services (DQS) Daten im Paketdatenfluss korrigieren, indem Sie eine Verbindung zwischen der DQS-Bereinigungstransformation und der Datenquelle herstellen. Weitere Informationen zu DQS finden Sie unter [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md). Weitere Informationen zu der Transformation finden Sie unter [DQS Cleansing Transformation](dqs-cleansing-transformation.md).  
  
 Wenn Sie Daten mit der DQS-Bereinigungstransformation verarbeiten, wird ein Data Quality-Projekt auf dem Data Quality-Server erstellt. Das Projekt wird mit dem Data Quality Client verwaltet. Weitere Informationen finden Sie unter [Verwalten von Data Quality-Projekten &#40;Öffnen, Entsperren, Umbenennen, Löschen&#41;](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md).  
  
### <a name="to-correct-data-in-the-data-flow"></a>So korrigieren Sie Daten im Datenfluss  
  
1.  Erstellen eines Pakets.  
  
2.  Fügen Sie die DQS-Bereinigungstransformation hinzu, und konfigurieren Sie sie. Weitere Informationen finden Sie unter [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Verbinden Sie die DQS-Bereinigungstransformation mit einer Datenquelle.  
  
  
