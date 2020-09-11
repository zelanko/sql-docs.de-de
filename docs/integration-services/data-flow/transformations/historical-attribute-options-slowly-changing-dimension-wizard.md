---
description: Optionen für Verlaufsattribute (Assistent für langsam veränderliche Dimensionen)
title: Optionen für Verlaufsattribute (Assistent für langsam veränderliche Dimensionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.loaddimwizard.histattriboption.f1
ms.assetid: a176ec66-ec39-4c99-99d1-c1afa8450e1e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9610a734543c9199e54d3f8489d86e03089f10ed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430702"
---
# <a name="historical-attribute-options-slowly-changing-dimension-wizard"></a>Optionen für Verlaufsattribute (Assistent für langsam veränderliche Dimensionen)

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  Mithilfe des Dialogfelds **Optionen für Verlaufsattribute** können Sie Verlaufsattribute nach Anfangs- und Enddatum anzeigen oder sie in einer speziell zu diesem Zweck erstellten Spalte aufzeichnen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Einzelne Spalte zum Anzeigen der aktuellen und abgelaufenen Datensätze verwenden**  
 Wenn Sie eine einzelne Spalte für zum Aufzeichnen des Status von Verlaufsattributen verwenden, sind folgende Optionen verfügbar:  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|**Spalte mit Indikator für aktuellen Datensatz**|Wählen Sie eine Spalte aus, in der der aktuelle Datensatz angezeigt werden soll.|  
|**Wert, wenn aktuell**|Verwenden Sie entweder **True** oder **Current** , um anzuzeigen, dass der Datensatz aktuell ist.|  
|**Wert, wenn abgelaufen**|Verwenden Sie entweder **False** oder **Abgelaufen** , um anzuzeigen, dass der Datensatz ein abgelaufener Wert ist.|  
  
 **Start- und Enddatum zum Identifizieren aktueller und abgelaufener Datensätze verwenden**  
 Die Dimensionstabelle für diese Option muss eine Datumsspalte enthalten. Wenn Sie die Verlaufsattribute nach Start- und Enddatum anzeigen, sind folgende Optionen verfügbar:  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|**Spalte mit Startdatum**|Wählen Sie die Spalte in der Dimensionstabelle aus, die das Startdatum enthalten soll.|  
|**Spalte mit Enddatum**|Wählen Sie die Spalte in der Dimensionstabelle aus, die das Enddatum enthalten soll.|  
|**Variable zum Festlegen von Datumswerten**|Wählen Sie eine Variable für die Datumswerte aus der Liste aus.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
