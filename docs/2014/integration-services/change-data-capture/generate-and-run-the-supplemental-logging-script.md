---
title: Generieren und Ausführen des ergänzenden Protokollierungsskripts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b5bfbff70d29e2b7b18c82b323d3ab34a3c6c60e
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58381522"
---
# <a name="generate-and-run-the-supplemental-logging-script"></a>Generieren und Ausführen des ergänzenden Protokollierungsskripts
  Verwenden Sie die Seite Set up Tables for Capturing Changes, um ein Skript für die Oracle-Quelldatenbank auszuführen, mit dem die ergänzende Protokollierung eingerichtet wird.  
  
 **So führen Sie die ergänzenden Protokollierungsskripts aus**  
  
 Klicken Sie auf **Run Script** , um das ergänzende Protokollierungsskript für die Tabellen auszuführen, die für die CDC-Instanz definiert sind. Dieses Skript weist die Oracle-Datenbank an, beim Protokollieren von UPDATE-Vorgängen zu aufgezeichneten Tabellen alle wichtigen Spalten in ihre Transaktionsprotokolle zu schreiben. Dieses Skript wird normalerweise von einem Oracle-Systemadministrator geprüft und ausgeführt.  
  
 Sie können die Skripts mit SQL*Plus auch manuell ausführen.  
  
 **So führen Sie Skripts manuell aus**  
  
 Klicken Sie auf **Kopieren** , um das Skript in die Zwischenablage einzufügen. Öffnen Sie SQL*Plus, und greifen Sie auf das Verzeichnis mit der Oracle-Quelldatenbank zu. Fügen Sie das Skript in SQL\*Plus ein, um es auszuführen.  
  
 Um das ergänzende Protokollierungsskript in einer Textdatei zu speichern, klicken Sie auf **Speichern unter** und greifen auf den Speicherort zu, an dem Sie die Datei speichern möchten. Geben Sie der Datei einen Namen, und klicken Sie auf **Speichern** , um die Datei zu speichern.  
  
 Klicken Sie auf **Weiter** , um den Schritt [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md)auszuführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen der Instanz für die SQL Server-Änderungsdatenbank](how-to-create-the-sql-server-change-database-instance.md)   
 [Überprüfen und Generieren ergänzender Protokollierungsskripts](review-and-generate-supplemental-logging-scripts.md)  
  
  
