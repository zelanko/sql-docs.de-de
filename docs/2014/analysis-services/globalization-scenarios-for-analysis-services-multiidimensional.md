---
title: Globalisierungs Szenarien für Analysis Services mehrdimensional | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- multiple language support [Analysis Services]
- languages [Analysis Services]
- SSAS, international considerations
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- SQL Server Analysis Services, international considerations
- Analysis Services, international considerations
ms.assetid: e8af85ff-ef33-4659-a003-bb34578eb2a2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e7b0d6e4d99c08556cefb31c33deb5238f33c636
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75225388"
---
# <a name="globalization-scenarios-for-analysis-services-multiidimensional"></a>Globalisierungsszenarien für Analysis Services Multidimensional
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]speichert und bearbeitet mehrsprachige Daten und Metadaten in tabellarischen und mehrdimensionalen Datenmodellen. Die Datenspeicherung erfolgt in Unicode (UTF-16) in Zeichensätzen, die Unicode-Codierung verwenden. Wenn Sie ANSI-Daten in ein Datenmodell laden, werden Zeichen mit entsprechenden Unicode-Codepunkten gespeichert.  
  
 Die Auswirkungen der Unicode-Unterstützung sehen so aus, dass [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Daten in allen von den Windows-Client- und -Serverbetriebssystemen unterstützten Sprachen speichern kann, sodass Daten in jedem auf einem Windows-Computer verwendeten Zeichensatz gelesen, geschrieben, sortiert und verglichen werden können. BI-Clientanwendungen, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Daten nutzen, können Daten in der vom Benutzer gewünschten Sprache darstellen, vorausgesetzt, die Daten sind in der jeweiligen Sprache im Modell vorhanden.  
  
 Sprachunterstützung kann für verschiedene Benutzer unterschiedliche Bedeutungen haben. In der folgenden Liste werden einige häufig gestellte Fragen im Zusammenhang mit der Sprachunterstützung in Analysis Services behandelt.  
  
-   Daten werden, wie erwähnt, in einem beliebigen, in einem Windows-Clientbetriebssystem vorhandenen Unicode-codierten Zeichensatz gespeichert.  
  
-   Metadaten, wie z. B. Objektnamen, Bezeichner und Beschreibungen, können ebenfalls in jeder Unicode-Sprache und jedem Unicode-Skript vorliegen. Dies gilt auch, wenn die Tools und die Umgebung in einer anderen Sprache sind. Beispiel: In einer Entwicklungsumgebung, die die englische Sprache und eine lateinische Sortierung im gesamten Stapel verwendet, können Sie in Ihr Modell ein Objekt einschließen, das kyrillische Zeichen im Namen verwendet.  
  
     Ausschließlich für mehrdimensionale Modelle können Beschriftungen und Attributelemente als Übersetzungen ausgedrückt werden. Sie können eine oder mehrere Übersetzungen definieren und dann einen Gebietsschemabezeichner verwenden, um zu bestimmen, welche Übersetzung an den Client zurückgegeben wird. Weitere Informationen finden Sie unten unter [Features](#bkmk_features) .  
  
-   Fehler-, Warn- und Informationsmeldungen, die von der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Engine (msmdsrv) zurückgegeben werden, sind in den 43 Sprachen lokalisiert, die von Office und Office 365 unterstützt werden. Es ist keine Konfiguration erforderlich, um Meldungen in einer bestimmten Sprache abzurufen. Das Gebietsschema der Clientanwendung bestimmt, welche Zeichenfolgen zurückgegeben werden.  
  
-   Die Konfigurationsdatei (msmdsrv.ini) und AMO PowerShell sind nur in Englisch verfügbar.  
  
-   Protokolldateien enthalten eine Mischung aus englischen und lokalisierten Meldungen, vorausgesetzt, Sie haben auf dem Windows-Server, auf dem Analysis Services ausgeführt wird, ein Language Pack installiert.  
  
-   Dokumentation und Tools, wie etwa [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] und [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)], wurden in diese Sprachen übersetzt: Chinesisch vereinfacht, Chinesisch traditionell, Französisch, Deutsch, Italienisch, Japanisch, Koreanisch, Portugiesisch (Brasilien), Russisch und Spanisch. Um eine sprachspezifische Version der Tools zu verwenden, installieren Sie eine sprachspezifische Version von SQL Server (z. B. die deutsche Version von SQL Server, um Management Studio auf Deutsch zu erhalten), oder führen Sie das eigenständige Setup in der Zielsprache für [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)]aus.  
  
 Mit Analysis Services können Sie Sprache, Sortierung und Übersetzungen unabhängig voneinander in der gesamten Objekthierarchie festlegen.  
  
 Zu über Sprache, Sortierungen und Übersetzungen ermöglichten Szenarien gehören:  
  
-   Ein Datenmodell bietet mehrere übersetzte Beschriftungen, sodass Feldnamen und Werte in der Sprache des Benutzers angezeigt werden. Für Unternehmen, die in zweisprachigen Ländern wie Kanada, Belgien oder der Schweiz agieren, ist die Unterstützung mehrerer Sprachen über Client- und Serveranwendungen hinweg eine Standardcodierungsanforderung. Dieses Szenario wird durch Übersetzungen und Währungsumrechnungen ermöglicht. Weitere Informationen und Links finden Sie unten unter [Features](#bkmk_features) .  
  
-   Entwicklungs- und Produktionsumgebungen befinden sich geografisch in verschiedenen Ländern. Es geschieht immer häufiger, dass eine Lösung in einem Land entwickelt und in einem anderen bereitgestellt wird. Zu wissen, wie Sprach- und Sortierungseigenschaften festgelegt werden, ist sehr wichtig, wenn Sie die Aufgabe erhalten, eine in einer Sprache entwickelte Lösung für die Bereitstellung auf einem Server vorzubereiten, der ein anderes Sprachpaket verwendet. Durch Festlegen dieser Eigenschaften können Sie die geerbten Standardeinstellungen überschreiben, die Sie vom ursprünglichen Hostsystem erhalten. Weitere Informationen finden Sie unten unter [Sprachen und Sortierungen &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md) .  
  
##  <a name="bkmk_features"></a>Funktionen zum Entwickeln einer globalisieren mehrdimensionalen Lösung  
 
  [!INCLUDE[applies](../includes/applies-md.md)] Nur mehrdimensionale Datenmodelle  
  
 Auf der Clientebene können globalisierte Anwendungen, die mehrdimensionale [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Daten verwenden oder bearbeiten, die mehrsprachigen und multikulturellen Features in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]verwenden:  
  
-   [Übersetzungen &#40;Analysis Services&#41;](translations-analysis-services.md) werden verwendet, um mehrere Beschriftungen für ein einzelnes Objekt einzubetten, wobei jede übersetzte Zeichenfolge zusammen mit anderen Übersetzungen vorhanden sein kann. Verwenden Sie [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , um die Übersetzungen für die Beschriftung, Beschreibung und Kontotypen für Cubes, Measures, Dimensionen und Attribute zu definieren. Rufen Sie Daten und Metadaten von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekten ab, in denen Übersetzungen automatisch definiert wurden, indem Sie einen Gebietsschemabezeichner beim Herstellen der Verbindung mit einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz angeben.  
  
     Eine Lektion zur Verwendung dieser Funktion finden Sie in [Lektion 9: Definieren von Perspektiven und Übersetzungen](lesson-9-defining-perspectives-and-translations.md) im Tutorial [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
-   [Währungsumrechnungen &#40;Analysis Services&#41;](currency-conversions-analysis-services.md) durch spezielle MDX-Skripts, die Measures mit Währungs Daten konvertieren. Sie können den Business Intelligence-Assistenten in [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] verwenden, um ein MDX-Skript zu generieren, das eine Kombination aus Daten und Metadaten aus Dimensionen, Attributen und Measuregruppen verwendet, um Measures mit Währungsdaten zu konvertieren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Sprachen und Sortierungen &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md)|Geben Sie die Standardsprache und die Windows-Sortierung für eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz an. Ihre Auswahl hat Einfluss auf die von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]verwalteten Daten und Metadaten.|  
|[Übersetzungen &#40;Analysis Services&#41;](translations-analysis-services.md)|Definieren Sie Übersetzungen für eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank und Objekte, die in der Datenbank enthalten sind. In diesem Thema wird erläutert, wie [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Anforderungen von Clientanwendungen nach übersetzten Daten und Metadaten auflöst.|  
|[Währungsumrechnungen &#40;Analysis Services&#41;](currency-conversions-analysis-services.md)|Definieren Sie eine Währungsumrechnung mit dem Business Intelligence-Assistenten.|  
|[Globalisierungs Tipps und bewährte Methoden &#40;Analysis Services&#41;](globalization-tips-and-best-practices-analysis-services.md)|Erläutert verschiedene Entwurfs- und Codierungsmethoden, mit denen Sie Probleme im Zusammenhang mit mehrsprachigen Daten vermeiden können.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Internationalisierung für Windows-Anwendungen](/windows/desktop/Intl/international-support)   
 [Dokumentation zu Microsoft Globalization](/globalization/)   
 [Schreiben von Windows Store-Apps mit Gebiets Schema basiertem adaptiven Design](https://blogs.windows.com/buildingapps/2014/03/06/writing-windows-store-apps-with-locale-based-adaptive-design/)   
 [Entwickeln von universellen Windows-apps mit c# und XAML](https://www.microsoftvirtualacademy.com/training-courses/developing-universal-windows-apps-with-c-and-xaml)  
  
