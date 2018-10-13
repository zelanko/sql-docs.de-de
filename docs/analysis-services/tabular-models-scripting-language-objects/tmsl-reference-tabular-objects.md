---
title: Definitionen der datenebenenobjekte in Tabular Model Scripting Language (TMSL) | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: de968c32f8c00132157a5b1b7a6682adc7148446
ms.sourcegitcommit: b75fc8cfb9a8657f883df43a1f9ba1b70f1ac9fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851745"
---
# <a name="tmsl-reference---tabular-objects"></a>TMSL-Referenz – Tabellarische Objekte
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Anwendungen, die zu erstellen, verwenden oder Verwalten von tabellendatenbanken oder die Verbindung mit einer SQL Server 2016 Analysis Services-Instanz im tabellarischen Modus herstellen, können die Tabular Model Scripting Language (TMSL) für Befehle und objektdarstellungen im JSON-Format verwenden.  
  
 Dieser Artikel beschreibt die wichtigsten Objekte das TMSL-Schemas in generiert, indem Sie SQL Server Management Studio, SQL Server Data Tools (SSDT) und AMO PowerShell-Skripts verwendet.  
  
 Objektdefinitionen werden im JSON-Format und verwendet in TMSL-Befehle, z. B. Create-, Alter- und zu löschen. Finden Sie unter [Befehle in Tabular Model Scripting Language &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md) für eine Liste der Befehle.  
  
## <a name="main-objects"></a>Hauptobjekte  
 In der folgende Tabelle ist die Liste der am häufigsten verwendeten Objekte im TMSL-Skript.  
  
|||  
|-|-|  
|[Datenbankobjekt &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|Definiert eine tabellarische Datenbank mit Kompatibilitätsgrad 1200 oder höher, auf Grundlage eines Modells der gleichen Ebene.|  
|[Modellobjekt &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|Definiert ein tabellarisches Modell mit Kompatibilitätsgrad 1200 oder höher.|  
|[DataSources-Objekt &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|Definiert eine Verbindung mit einer Datenquelle, die während des Imports zum Laden des Modells oder für Pass-through-Abfragen verwendet werden, wenn das Modell im DirectQuery-Modus befindet.|  
|[Tables-Objekt &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|Gibt die Tabellen des Modells an.|  
|[Partitions-Objekt &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|Definiert die Speicherung der Tabelle-Schemarowsets, einschließlich der berechnete Tabellen.|  
|[Relationships-Objekt &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|Definiert die Beziehungen zwischen Tabellen.|  
|[Roles-Objekt &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|Definiert die Berechtigungen, Mitgliedschaft und Sicherheitsfilter, die Steuerung des Zugriffs auf Daten und Vorgänge.|  
  
## <a name="see-also"></a>Siehe auch  
 [Tabular Model Scripting Language &#40;TMSL&#41; – Referenz](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
