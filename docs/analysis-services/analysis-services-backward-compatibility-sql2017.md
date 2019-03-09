---
title: Abwärtskompatibilität der SQL Server 2017 Analysis Services | Microsoft-Dokumentation
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: e7903de787a1b63627bca8da23369fbee9014c6e
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685737"
---
# <a name="analysis-services-backward-compatibility-sql-2017"></a>Analysis Services-Abwärtskompatibilität (SQL 2017)
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

In diesem Artikel werden Änderungen an der Verfügbarkeit von Features und verhaltensänderungen zwischen der aktuellen Version und der vorherigen Version beschrieben.

## <a name="deprecated-features"></a>Veraltete Features
Ein *veraltete Funktion* werden in einer zukünftigen Version wird aus dem Produkt eingestellt, aber ist immer noch unterstützt und in der aktuellen Version aus, um Abwärtskompatibilität enthalten. Es wird empfohlen, dass Sie dieses als veraltet markierte Funktionen in neue und vorhandene Projekte auf um Kompatibilität mit zukünftigen Versionen zu gewährleisten. Dokumentation ist nicht für die als veraltet markierte Funktionen aktualisiert.

Die folgenden Features sind in dieser Version als veraltet markiert:
  
|||  
|-|-|  
|**Im Modus/Kategorie**|**Funktion**|
|Multidimensional|Data Mining|
|Multidimensional|Remoteverknüpfte Measuregruppen|
|Tabellarisch|Modelle mit Kompatibilitätsgrad 1100 und 1103|
|Tabellarisch|Tabular Object Model-Eigenschaften: Column.TableDetailPosition, Column.IsDefaultLabel, Column.IsDefaultImage|
|Tools|SQL Server Profiler für die Ablaufverfolgungssammlung<br /><br /> Der Ersatz verwendet den in SQL Server Management Studio eingebetteten Profiler für erweiterte Ereignisse.  <br /> Weitere Informationen finden Sie unter [Überwachen von Analysis Services mit den erweiterten Ereignissen von SQL Server](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md).|  
|Tools|Server Profiler für die Ablaufverfolgungswiedergabe <br />Ersatz. Es gibt keinen Ersatz.|  
|Verwaltungsobjekte für die Ablaufverfolgung und Ablaufverfolgungs-APIs|Microsoft.AnalysisServices.Trace-Objekte (enthält die APIs für Analysis Services Ablauf-und Wiedergabeobjekte). Der Ersatz ist mehrteilig:<br /><br /> -Ablaufverfolgungskonfiguration: Microsoft.SqlServer.Management.XEvent<br />-Ablaufverfolgungslesevorgänge: Microsoft.SqlServer.XEvent.Linq<br />-Ablaufverfolgungswiedergabe: None|  


## <a name="discontinued-features"></a>Nicht mehr unterstützte Funktionen
Ein *nicht mehr unterstützte Funktion* wurde in einer früheren Version als veraltet markiert. Sie können weiterhin in der aktuellen Version enthalten sein, aber es wird nicht mehr unterstützt. Möglicherweise werden nicht mehr unterstützte Funktionen entfernt vollständig in einer zukünftigen Version, oder aktualisieren.

Die folgenden Features wurden in einer früheren Version als veraltet markiert und werden in dieser Version nicht mehr unterstützt.
  
|||  
|-|-|  
|**Im Modus/Kategorie**|**Funktion**|  
|Tabellarisch|VertipaqPagingPolicy Arbeitsspeicher-Eigenschaftswert (2), Enable-Auslagerung auf Datenträger, Speicher zugeordnet, Dateien.|
|Multidimensional|Remotepartitionen|  
|Multidimensional|Remoteverknüpfte Measuregruppen|  
|Multidimensional|Dimensionales Rückschreiben|  
|Multidimensional|Verknüpfte Dimensionen|


## <a name="breaking-changes"></a>Wichtige Änderungen
Ein *bedeutende Änderung* bewirkt, dass eine Funktion, Datenmodell, Anwendungscode oder Skript nicht mehr funktioniert nach dem Upgrade auf die aktuelle Version.

Es gibt keine wichtigen Änderungen in dieser Version.

## <a name="behavior-changes"></a>Verhaltensänderungen
Ein *verhaltensänderung* wirkt sich auf die gleiche Funktion wie in der aktuellen Version im Vergleich zum vorherigen Release funktioniert. Es werden nur bedeutungsvolles Verhalten ändert sich beschrieben. Änderungen in der Benutzeroberfläche sind nicht enthalten.

Änderungen an MDSCHEMA_MEASUREGROUP_DIMENSIONS und DISCOVER_CALC_DEPENDENCY, finden Sie unter den [Neuigkeiten in SQL Server 2017 CTP 2.1 für Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/05/18/whats-new-in-sql-server-2017-ctp-2-1-for-analysis-services/) Ankündigung.


## <a name="see-also"></a>Siehe auch
[Analysis Services-Abwärtskompatibilität (SQL Server 2016)](analysis-services-backward-compatibility.md)
