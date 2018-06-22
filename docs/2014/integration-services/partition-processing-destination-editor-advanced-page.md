---
title: Partition Ziel-Editor (Seite erweitert) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.advanced.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 2039ee0f-069d-479d-90b2-2a12481b1162
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7f81cc34213d2288512a8d063b1e11e4dfd49d53
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047207"
---
# <a name="partition-processing-destination-editor-advanced-page"></a>Ziel-Editor für Partitionsverarbeitung (Seite Erweitert)
  Auf der Seite **Erweitert** des Dialogfelds **Ziel-Editor für Partitionsverarbeitung** konfigurieren Sie die Fehlerbehandlung.  
  
 Weitere Informationen zum Ziel für Partitionsverarbeitung finden Sie unter [Partition Processing Destination](data-flow/partition-processing-destination.md).  
  
> [!NOTE]  
>  Hier beschriebene Tasks gelten nicht für tabellarische Analysis Services-Modelle.  Sie können Partitionsspalten für tabellarische Modelle keine Eingabespalten zuordnen. Sie können stattdessen den Analysis Services-Task "DDL ausführen" [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) verwenden, um die Partition zu verarbeiten.  
  
## <a name="options"></a>Tastatur  
 **Standardfehlerkonfiguration verwenden**  
 Gibt an, ob die Standardfehlerbehandlung von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verwendet werden soll. Standardmäßig ist dieser Wert `True`.  
  
 **Schlüsselfehleraktion**  
 Gibt an, wie Datensätze behandelt werden, die unzulässige Schlüsselwerte aufweisen.  
  
|value|Description|  
|-----------|-----------------|  
|**ConvertToUnknown**|Konvertiert den unzulässigen Schlüsselwert in den Wert Unknown.|  
|**DiscardRecord**|Verwirft den Datensatz.|  
  
 **Fehler ignorieren**  
 Gibt an, dass Fehler ignoriert werden sollen.  
  
 **Bei Fehler beenden**  
 Gibt an, dass die Verarbeitung beendet werden soll, wenn ein Fehler auftritt.  
  
 **Anzahl von Fehlern**  
 Gibt den Schwellenwert für die Anzahl von Fehlern an, ab dem die Verarbeitung beendet werden soll, wenn Sie **Bei Fehler beenden**ausgewählt haben.  
  
 **Aktion bei Fehler**  
 Gibt die Aktion an, die bei Erreichen des Fehlerschwellenwerts ausgeführt wird, wenn Sie **Bei Fehler beenden**ausgewählt haben.  
  
|value|Description|  
|-----------|-----------------|  
|**StopProcessing**|Beendet die Verarbeitung.|  
|**StopLogging**|Beendet das Protokollieren der Fehler.|  
  
 **Schlüssel nicht gefunden**  
 Gibt die Aktion an, die beim Fehler Schlüssel nicht gefunden ausgeführt werden soll. Standardmäßig ist dieser Wert **ReportAndContinue**.  
  
|value|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignoriert den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndContinue**|Berichtet den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndStop**|Berichtet den Fehler, und beendet die Verarbeitung.|  
  
 **Doppelter Schlüssel**  
 Gibt die Aktion an, die beim Fehler Doppelter Schlüssel ausgeführt werden soll. Standardmäßig ist dieser Wert **IgnoreError**.  
  
|value|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignoriert den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndContinue**|Berichtet den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndStop**|Berichtet den Fehler, und beendet die Verarbeitung.|  
  
 **NULL-Schlüssel in unbekanntes Element konvertiert**  
 Gibt die Aktion an, die ausgeführt werden soll, wenn ein NULL-Schlüssel in den Wert Unknown konvertiert wurde. Standardmäßig ist dieser Wert **IgnoreError**.  
  
|value|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignoriert den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndContinue**|Berichtet den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndStop**|Berichtet den Fehler, und beendet die Verarbeitung.|  
  
 **NULL-Schlüssel nicht zulässig**  
 Gibt die Aktion an, die ausgeführt wird, wenn NULL-Schlüssel unzulässig sind und ein NULL-Schlüssel entdeckt wurde. Standardmäßig ist dieser Wert **ReportAndContinue**.  
  
|value|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignoriert den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndContinue**|Berichtet den Fehler, und setzt die Verarbeitung fort.|  
|**ReportAndStop**|Berichtet den Fehler, und beendet die Verarbeitung.|  
  
 **Fehlerprotokollpfad**  
 Geben Sie den Pfad für das Fehlerprotokoll ein, oder wählen Sie mit der Schaltfläche **Durchsuchen (...)** ein Ziel aus.  
  
 **Durchsuchen (…)**  
 Wählen Sie einen Pfad für das Fehlerprotokoll aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Ziel-Editor für Partition &#40;Seite "Zuordnungen"&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)  
  
  