---
title: Ziel-Editor für Partitions Verarbeitung (Seite erweitert) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.advanced.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 2039ee0f-069d-479d-90b2-2a12481b1162
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 53db6110e47f5664e7107090179b6ac7bcf4a361
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423457"
---
# <a name="partition-processing-destination-editor-advanced-page"></a>Ziel-Editor für Partitionsverarbeitung (Seite Erweitert)
  Auf der Seite **Erweitert** des Dialogfelds **Ziel-Editor für Partitionsverarbeitung** konfigurieren Sie die Fehlerbehandlung.  
  
 Weitere Informationen zum Ziel für Partitionsverarbeitung finden Sie unter [Partition Processing Destination](data-flow/partition-processing-destination.md).  
  
> [!NOTE]  
>  Hier beschriebene Tasks gelten nicht für tabellarische Analysis Services-Modelle.  Sie können Partitionsspalten für tabellarische Modelle keine Eingabespalten zuordnen. Sie können stattdessen den Analysis Services-Task "DDL ausführen" [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) verwenden, um die Partition zu verarbeiten.  
  
## <a name="options"></a>Optionen  
 **Standardfehlerkonfiguration verwenden**  
 Gibt an, ob die Standardfehlerbehandlung von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verwendet werden soll. Der Standardwert ist `True`.  
  
 **Schlüsselfehler Aktion**  
 Gibt an, wie Datensätze behandelt werden, die unzulässige Schlüsselwerte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**ConvertToUnknown**|Konvertiert den unzulässigen Schlüsselwert in den Wert Unknown.|  
|**DiscardRecord**|Verwirft den Datensatz.|  
  
 **Fehler ignorieren**  
 Gibt an, dass Fehler ignoriert werden sollen.  
  
 **Bei Fehler abbrechen**  
 Gibt an, dass die Verarbeitung beendet werden soll, wenn ein Fehler auftritt.  
  
 **Anzahl von Fehlern**  
 Gibt den Schwellenwert für die Anzahl von Fehlern an, ab dem die Verarbeitung beendet werden soll, wenn Sie **Bei Fehler beenden**ausgewählt haben.  
  
 **Aktion bei Fehler**  
 Gibt die Aktion an, die bei Erreichen des Fehlerschwellenwerts ausgeführt wird, wenn Sie **Bei Fehler beenden**ausgewählt haben.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**StopProcessing**|Beendet die Verarbeitung.|  
|**StopLogging**|Beendet das Protokollieren der Fehler.|  
  
 **Schlüssel nicht gefunden**  
 Gibt die Aktion an, die beim Fehler Schlüssel nicht gefunden ausgeführt werden soll. Standardmäßig ist dieser Wert **ReportAndContinue**.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**IgnoreError**|Ignoriert den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndContinue**|Berichtet den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndStop**|Berichtet den Fehler, und beendet die Verarbeitung.|  
  
 **Doppelter Schlüssel**  
 Gibt die Aktion an, die beim Fehler Doppelter Schlüssel ausgeführt werden soll. Standardmäßig ist dieser Wert **IgnoreError**.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**IgnoreError**|Ignoriert den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndContinue**|Berichtet den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndStop**|Berichtet den Fehler, und beendet die Verarbeitung.|  
  
 **NULL-Schlüssel in unbekanntes konvertiert**  
 Gibt die Aktion an, die ausgeführt werden soll, wenn ein NULL-Schlüssel in den Wert Unknown konvertiert wurde. Standardmäßig ist dieser Wert **IgnoreError**.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**IgnoreError**|Ignoriert den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndContinue**|Berichtet den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndStop**|Berichtet den Fehler, und beendet die Verarbeitung.|  
  
 **NULL-Schlüssel nicht zulässig**  
 Gibt die Aktion an, die ausgeführt wird, wenn NULL-Schlüssel unzulässig sind und ein NULL-Schlüssel entdeckt wurde. Standardmäßig ist dieser Wert **ReportAndContinue**.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**IgnoreError**|Ignoriert den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndContinue**|Berichtet den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndStop**|Berichtet den Fehler, und beendet die Verarbeitung.|  
  
 **Fehlerprotokollpfad**  
 Geben Sie den Pfad für das Fehlerprotokoll ein, oder wählen Sie mit der Schaltfläche **Durchsuchen (...)** ein Ziel aus.  
  
 **Durchsuchen (…)**  
 Wählen Sie einen Pfad für das Fehlerprotokoll aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Ziel-Editor für Partitionsverarbeitung &#40;Seite Zuordnungen&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)  
  
  
