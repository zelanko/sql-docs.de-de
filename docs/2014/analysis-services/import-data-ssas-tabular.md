---
title: Importieren von Daten (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 6617b2a2-9f69-433e-89e0-4c5dc92982cf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 340accda9321eb8732f909e73729ccaf5193e9a6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62730390"
---
# <a name="import-data-ssas-tabular"></a>Importieren von Daten (SSAS – tabellarisch)
  Sie können Daten aus einer Vielzahl von Quellen in ein Tabellenmodell importieren. In diesem Abschnitt wird beschrieben, wie der Datenimport-Assistent verwendet wird, um eine Verbindung herzustellen und die in das Modellprojekt zu importierenden Daten auszuwählen.  
  
> [!IMPORTANT]  
>  Wenn eine der Tabellen im Modell eine große Anzahl von Zeilen aufweist, erwägen Sie, während der Modellerstellung nur eine Teilmenge der Daten zu importieren. Sie können die Verarbeitungszeit und den Verbrauch von Arbeitsbereichsdatenbank-Serverressourcen reduzieren, indem Sie eine Teilmenge der Daten importieren.  
  
 Mit dem Tabellenimport-Assistenten können Sie Daten aus den folgenden Datenquellen importieren:  
  
|**Data Source**|**Beschreibung**|  
|---------------------|---------------------|  
|**Relationale Datenbanken**|Relationale Datenquellen umfassen:<br /><br /> Microsoft SQL Server<br /><br /> Microsoft SQL Azure<br /><br /> Microsoft SQL Server Parallel Data Warehouse<br /><br /> Microsoft Access<br /><br /> Oracle<br /><br /> Teradata<br /><br /> Sybase<br /><br /> Informix<br /><br /> IBM DB2<br /><br /> OLEDB/ODBC|  
|**Mehrdimensionale Quellen**|Microsoft SQL Server Analysis Services-Cube|  
|**Datenfeeds**|Datenfeeds umfassen:<br /><br /> Microsoft Reporting Services-Bericht<br /><br /> Azure DataMarket-Dataset<br /><br /> Atom-Feeds eines öffentlichen oder Unternehmensanbieters|  
|**Textdateien**|Textdateien umfassen:<br /><br /> Excel-Dateien (.xlsx)<br /><br /> Textdatei (.txt)|  
  
 Zusätzlich zum Importieren von Daten mit dem Tabellenimport-Assistenten können Sie auch kopierte Daten (aus dem Zwischenablage) in eine Tabelle einfügen. Eingefügte Daten verhalten sich anders als Daten, die aus anderen Datenquellen importiert wurden. In Tabellen eingefügte Daten verfügen über keine ConnectionName- oder SourceData-Eigenschaft. Eingefügte Daten werden in der Datei Model.bim beibehalten. Beim Speichern des Projekts oder der Datei Model.bim werden die eingefügten Daten ebenfalls gespeichert.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Thema|Description|  
|-----------|-----------------|  
|[Importieren aus einer relationalen Datenquelle &#40;SSAS – tabellarisch&#41;](import-from-a-relational-data-source-ssas-tabular.md)|Beschreibt, wie Daten aus relationalen Datenquellen wie einer Microsoft SQL Server-, Oracle- oder Teradata-Datenbank importiert werden.|  
|[Importieren aus einer mehrdimensionalen Datenquelle &#40;SSAS – tabellarisch&#41;](import-from-a-multidimensional-data-source-ssas-tabular.md)|Beschreibt, wie Daten aus einem mehrdimensionalen SQL Server Analysis Services-Cube importiert werden.|  
|[Importieren aus einem Datenfeed &#40;SSAS – tabellarisch&#41;](import-from-a-data-feed-ssas-tabular.md)|Beschreibt, wie Daten aus einem Datenfeed, z. B. einem Microsoft-Reporting Services-Bericht oder einem Azure Data Markt-Dataset, importiert werden.|  
|[Importieren aus einer Textdatei &#40;SSAS – tabellarisch&#41;](import-from-a-text-file-ssas-tabular.md)|Beschreibt, wie Daten aus einer Microsoft Excel-Arbeitsmappe oder einer Textdatei importiert werden.|  
|[Kopieren und Einfügen von Daten &#40;SSAS – tabellarisch&#41;](copy-and-paste-data-ssas-tabular.md)|Beschreibt, wie Daten einer vorhandenen Tabelle im Modell-Designer mit Einfügen und Am Ende einfügen hinzugefügt werden.|  
  
  
