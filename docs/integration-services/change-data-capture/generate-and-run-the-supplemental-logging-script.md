---
description: Generieren und Ausführen des ergänzenden Protokollierungsskripts
title: Generieren und Ausführen des ergänzenden Protokollierungsskripts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a54fc6cab8ea15556aec82f810e2b678f1c78c7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484683"
---
# <a name="generate-and-run-the-supplemental-logging-script"></a>Generieren und Ausführen des ergänzenden Protokollierungsskripts

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Verwenden Sie die Seite Set up Tables for Capturing Changes, um ein Skript für die Oracle-Quelldatenbank auszuführen, mit dem die ergänzende Protokollierung eingerichtet wird.  
  
 **So führen Sie die ergänzenden Protokollierungsskripts aus**  
  
 Klicken Sie auf **Run Script** , um das ergänzende Protokollierungsskript für die Tabellen auszuführen, die für die CDC-Instanz definiert sind. Dieses Skript weist die Oracle-Datenbank an, beim Protokollieren von UPDATE-Vorgängen zu aufgezeichneten Tabellen alle wichtigen Spalten in ihre Transaktionsprotokolle zu schreiben. Dieses Skript wird normalerweise von einem Oracle-Systemadministrator geprüft und ausgeführt.  
  
 Sie können die Skripts mit SQL*Plus auch manuell ausführen.  
  
 **So führen Sie Skripts manuell aus**  
  
 Klicken Sie auf **Kopieren** , um das Skript in die Zwischenablage einzufügen. Öffnen Sie SQL*Plus, und greifen Sie auf das Verzeichnis mit der Oracle-Quelldatenbank zu. Fügen Sie das Skript in SQL\*Plus ein, um es auszuführen.  
  
 Um das ergänzende Protokollierungsskript in einer Textdatei zu speichern, klicken Sie auf **Speichern unter** und greifen auf den Speicherort zu, an dem Sie die Datei speichern möchten. Geben Sie der Datei einen Namen, und klicken Sie auf **Speichern** , um die Datei zu speichern.  
  
 Klicken Sie auf **Weiter** , um den Schritt [Generate Mirror Tables and CDC Capture Instances](../../integration-services/change-data-capture/generate-mirror-tables-and-cdc-capture-instances.md)auszuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen der Instanz für die SQL Server-Änderungsdatenbank](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Überprüfen und Generieren ergänzender Protokollierungsskripts](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md)  
  
  
