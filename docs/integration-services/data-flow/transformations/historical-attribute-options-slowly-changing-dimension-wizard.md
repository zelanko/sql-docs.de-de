---
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1a5a01a87bb8b8d52f4d3857c3b44aee3dbde52a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47847578"
---
# <a name="historical-attribute-options-slowly-changing-dimension-wizard"></a>Optionen für Verlaufsattribute (Assistent für langsam veränderliche Dimensionen)
  Mithilfe des Dialogfelds **Optionen für Verlaufsattribute** können Sie Verlaufsattribute nach Anfangs- und Enddatum anzeigen oder sie in einer speziell zu diesem Zweck erstellten Spalte aufzeichnen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Einzelne Spalte zum Anzeigen der aktuellen und abgelaufenen Datensätze verwenden**  
 Wenn Sie eine einzelne Spalte für zum Aufzeichnen des Status von Verlaufsattributen verwenden, sind folgende Optionen verfügbar:  
  
|Option|und Beschreibung|  
|------------|-----------------|  
|**Spalte mit Indikator für aktuellen Datensatz**|Wählen Sie eine Spalte aus, in der der aktuelle Datensatz angezeigt werden soll.|  
|**Wert, wenn aktuell**|Verwenden Sie entweder **True** oder **Current** , um anzuzeigen, dass der Datensatz aktuell ist.|  
|**Wert, wenn abgelaufen**|Verwenden Sie entweder **False** oder **Abgelaufen** , um anzuzeigen, dass der Datensatz ein abgelaufener Wert ist.|  
  
 **Start- und Enddatum zum Identifizieren aktueller und abgelaufener Datensätze verwenden**  
 Die Dimensionstabelle für diese Option muss eine Datumsspalte enthalten. Wenn Sie die Verlaufsattribute nach Start- und Enddatum anzeigen, sind folgende Optionen verfügbar:  
  
|Option|und Beschreibung|  
|------------|-----------------|  
|**Spalte mit Startdatum**|Wählen Sie die Spalte in der Dimensionstabelle aus, die das Startdatum enthalten soll.|  
|**Spalte mit Enddatum**|Wählen Sie die Spalte in der Dimensionstabelle aus, die das Enddatum enthalten soll.|  
|**Variable zum Festlegen von Datumswerten**|Wählen Sie eine Variable für die Datumswerte aus der Liste aus.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
