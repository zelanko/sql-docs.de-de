---
title: Anwenden von Datenqualitätsregeln auf eine Datenquelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e9c42a8cd9b43672dc145f2176c2aba0cef89637
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694678"
---
# <a name="apply-data-quality-rules-to-data-source"></a>Anwenden von Datenqualitätsregeln auf eine Datenquelle
  Sie können mit Data Quality Services (DQS) Daten im Paketdatenfluss korrigieren, indem Sie eine Verbindung zwischen der DQS-Bereinigungstransformation und der Datenquelle herstellen. Weitere Informationen zu DQS finden Sie unter [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md). Weitere Informationen zu der Transformation finden Sie unter [DQS Cleansing Transformation](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md).  
  
 Wenn Sie Daten mit der DQS-Bereinigungstransformation verarbeiten, wird ein Data Quality-Projekt auf dem Data Quality-Server erstellt. Das Projekt wird mit dem Data Quality Client verwaltet. Weitere Informationen finden Sie unter [Öffnen, Entsperren, Umbenennen, Löschen von Data Quality-Projekten](../../../data-quality-services/open-unlock-rename-and-delete-a-data-quality-project.md).  
  
### <a name="to-correct-data-in-the-data-flow"></a>So korrigieren Sie Daten im Datenfluss  
  
1.  Erstellen eines Pakets.  
  
2.  Fügen Sie die DQS-Bereinigungstransformation hinzu, und konfigurieren Sie sie. Weitere Informationen finden Sie unter [DQS Cleansing Transformation Editor Dialog Box](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Verbinden Sie die DQS-Bereinigungstransformation mit einer Datenquelle.  
  
  
