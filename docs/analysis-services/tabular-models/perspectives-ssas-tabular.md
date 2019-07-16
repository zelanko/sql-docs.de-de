---
title: Perspektiven in tabellenmodellen von Analysis Services | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dc6b574702f71a70de842c3a3b51110e8eed9814
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207617"
---
# <a name="perspectives-in-tabular-models"></a>Perspektiven in tabellenmodellen
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  In tabellarischen Modellen definiert eine Perspektive sichtbare Teilmengen eines Modells, die fokussierte, unternehmensspezifische oder anwendungsspezifische Blickpunkte des Modells bereitstellen.  
  
##  <a name="bkmk_understanding"></a> Vorteile  
 Die Suche in tabellarischen Modellen kann sich für den Benutzer als sehr schwierig erweisen. In einem einzelnen Modell kann der Inhalt eines vollständigen Data Warehouses mit vielen Tabellen, Measures und Dimensionen abgebildet sein. Eine solche Komplexität kann entmutigend für Benutzer sein, die oft nur mit einem kleinen Teil des Modells interagieren müssen, um ihre Business Intelligence- und Berichterstellungsanforderungen zu erfüllen.  
  
 In einer Perspektive werden Tabellen, Spalten und Measures (einschließlich KPIs) als Feldobjekte definiert. Sie können die Anzeigefelder für jede Perspektive auswählen. Ein einzelnes Modell kann beispielsweise Produkt-, Vertriebs-, Finanz-, Mitarbeiter- und geografische Daten vereinen. Eine Vertriebsabteilung arbeitet in erster Linie mit Produkt-, Vertriebs-, Marketing- und geografischen Daten, während Mitarbeiter- und Finanzdaten eher nicht benötigt werden. Entsprechend sind für eine Personalabteilung Daten über Verkaufswerbungen und Vertriebsgebiete nicht von Belang.  
  
 Wenn ein Benutzer eine Verbindung mit einem Modell (als Datenquelle) herstellt, für das Perspektiven definiert sind, kann er die gewünschte Perspektive auswählen. Wenn Mitarbeiter der Personalabteilung eine Verbindung mit einer Modelldatenquelle in Excel herstellen, können sie im Datenverbindungs-Assistenten auf der Seite Tabellen und Sichten auswählen beispielsweise die Perspektive Human Ressources auswählen. In der PivotTable-Feldliste werden nur die für die Perspektive Human Resources definierten Felder (Tabellen, Spalten und Measures) angezeigt.  
  
 Perspektiven sollen nicht als Sicherheitsmechanismus verwendet werden, sondern als Tool zur Verbesserung der Benutzerfreundlichkeit. Die gesamte Sicherheit einer bestimmten Perspektive wird vom zugrunde liegenden Modell geerbt. Perspektiven gewähren keinen Zugriff auf Modellobjekte, auf die ein Benutzer nicht bereits Zugriff hat. Die Sicherheit der Modelldatenbank muss geklärt werden, damit der Zugriff auf Objekte im Modell durch eine Perspektive ermöglicht werden kann. Sicherheitsrollen können verwendet werden, um Modellmetadaten und Daten zu sichern. Weitere Informationen finden Sie unter [Rollen](../../analysis-services/tabular-models/roles-ssas-tabular.md).  
  
##  <a name="bkmk_testpersp"></a> Testing perspectives  
 Bei der Modellerstellung können Sie die Funktion In Excel analysieren im Modell-Designer verwenden, um die Wirksamkeit der definierten Perspektiven zu testen. Wenn Sie im Menü **Modell** im Modell-Designer auf **In Excel analysieren**klicken, bevor Excel geöffnet wird, wird das Dialogfeld **Anmeldeinformationen und Perspektive auswählen** angezeigt. In diesem Dialogfeld können Sie den aktuellen Benutzernamen, einen anderen Benutzer, eine Rolle und eine Perspektive angeben, um darüber eine Verbindung mit der Arbeitsbereichsdatenbank des Modells als Datenquelle herzustellen und Daten anzuzeigen.  
  
##  <a name="bkmk_related_tasks"></a> Related tasks  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Erstellen und Verwalten von Perspektiven](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)|Beschreibt, wie Sie Perspektiven über das Dialogfeld Perspektiven im Modell-Designer erstellen und verwalten.|  
  
## <a name="see-also"></a>Siehe auch  
 [Rollen](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [Hierarchien](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)  
  
  
