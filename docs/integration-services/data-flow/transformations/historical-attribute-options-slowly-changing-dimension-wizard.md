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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4b06f56346e8e17fbdb9284dded2bfc154b9ae1a
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71297918"
---
# <a name="historical-attribute-options-slowly-changing-dimension-wizard"></a>Optionen für Verlaufsattribute (Assistent für langsam veränderliche Dimensionen)

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Mithilfe des Dialogfelds **Optionen für Verlaufsattribute** können Sie Verlaufsattribute nach Anfangs- und Enddatum anzeigen oder sie in einer speziell zu diesem Zweck erstellten Spalte aufzeichnen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>enthalten  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
