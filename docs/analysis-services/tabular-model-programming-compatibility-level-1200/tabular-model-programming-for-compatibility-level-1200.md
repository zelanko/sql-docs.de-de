---
title: Analysis Services tabular model-Programmierung für Kompatibilitätsgrad 1200 | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7493c09964db2e0a8cbd17c6a2278dd554a2dcc
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2019
ms.locfileid: "57579450"
---
# <a name="tabular-model-programming-for-compatibility-level-1200-and-higher"></a>Programmieren von tabellarischen Modellen für Kompatibilitätsgrad 1200 und höher
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Beginnend mit dem Kompatibilitätsgrad 1200, tabellarischer Metadaten dient zum Beschreiben der Model-Konstrukten, die historische mehrdimensionale Metadaten als Deskriptoren für tabellarische Modellobjekte ersetzen. Metadaten für Tabellen, Spalten und Beziehungen werden die Tabelle, Spalte und Beziehung, anstatt die mehrdimensionale Entsprechungen (Dimensions- und Attributtypen).  
  
Sie können Erstellen neuer Modelle mit Kompatibilitätsgrad 1200 oder höher mithilfe der Microsoft.AnalysisServices.Tabular-APIs, die neueste Version von SQL Server Data Tools (SSDT) oder durch Ändern der **CompatibilityLevel** einem vorhandenen tabellarischen Modell zu aktualisieren (auch in SSDT erfolgt). Auf diese Weise bindet das Modell auf neuere Versionen von Server, Tools und Programmierschnittstellen.   
  
Aktualisieren einer vorhandenen tabellarischen Lösung wird empfohlen, jedoch nicht erforderlich. Vorhandenes Skript und benutzerdefinierte Lösungen, die Zugriff auf oder Verwalten von tabellarischen Modellen oder Datenbanken können als verwendet werden – ist. Frühere Kompatibilitätsgraden werden in SQL Server 2016 mit den verfügbaren Funktionen auf dieser Ebene vollständig unterstützt. Kompatibilitätsgrad 1200 und höher wird nur von Azure Analysis Services unterstützt.
  
 Neue tabellarische Modelle müssen verschiedene Code- und Skriptbeispiele, unten zusammengefasst.  
  
## <a name="object-model-definitions-as-tabular-metadata-constructs"></a>Das Modelldefinitionen als tabellarischen Metadaten-Konstrukte  
 Für 1200 oder höher Modelle das Tabellenobjektmodell wird verfügbar gemacht, in JSON über die [Tabular Model Scripting Language](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference) und über die AMO-Datendefinitionssprache über einen neuen Namespace, [ Microsoft.AnalysisServices.Tabular](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.aspx)

## <a name="script-for-tabular-models-and-databases"></a>Skript für tabellarische Modelle und Datenbanken  
 TMSL wird eine JSON-Skriptsprache für tabellarische Modelle mit Unterstützung für das Erstellen, lesen, aktualisieren und eine Delete-Vorgänge. Sie können Aktualisieren von Daten über TMSL rufen Sie Datenbankvorgänge für anfügen, trenne, Sicherung, Wiederherstellung und zu synchronisieren.  
  
 AMO PowerShell akzeptiert TMSL-Skript als Eingabe.  
  
 Finden Sie unter [Tabular Model Scripting Language &#40;TMSL&#41; Verweis](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference) und [Analysis Services PowerShell Reference](../../analysis-services/powershell/analysis-services-powershell-reference.md) für Weitere Informationen.  
  
## <a name="query-languages"></a>Abfragesprachen  
 DAX und MDX, werden für alle tabellarischen Modelle unterstützt.  
  
## <a name="expression-language"></a>Sprache für Ausdrücke  
 Filter und Ausdrücke, mit denen berechnete Objekte, einschließlich Measures und KPIs erstellen, werden in DAX formuliert. Finden Sie unter [Grundlegendes zu DAX in tabellarischen Modellen](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md) und [Data Analysis Expressions &#40;DAX&#41; in Analysis Services](http://msdn.microsoft.com/library/abb336c9-3346-4cab-b91b-90f93f4575e5).  
  
## <a name="managed-code-for-tabular-models-and-databases"></a>Verwalteter Code für tabellarische Modelle und Datenbanken  
 AMO enthält einen neuen Namespace, Microsoft.AnalysisServices.Tabular, für das Arbeiten mit Modellen programmgesteuert an. Finden Sie unter [Microsoft.AnalysisServices Namespace](https://msdn.microsoft.com/library/ms146720\(SQL.130\).aspx) für Weitere Informationen.  
  
> [!NOTE]  
>  Clientbibliotheken von Analysis Services Management Objects (AMO), ADOMD.NET und Tabular Object Model (TOM) als Ziel jetzt die .NET 4.0-Laufzeit.   
  
## <a name="see-also"></a>Siehe auch  
 [Entwicklerhandbuch (Analysis Services)](../../analysis-services/analysis-services-developer-documentation.md)   
 [Programmierung von tabellarischen Modellen für Kompatibilitätsgrad Ebenen 1050 bis 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)   
 [Technische Referenz für den](../../analysis-services/powershell/technical-reference-ssas.md)[Aktualisieren von Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)  
 [Kompatibilitätsgrade für tabellarische Modelle und Datenbanken](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)  
  
  
