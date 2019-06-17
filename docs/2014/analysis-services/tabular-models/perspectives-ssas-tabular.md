---
title: Perspektiven (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1f78c3a1-ce2c-4e7f-a277-71a657692bea
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fcd6e438327d88b79a88b5026f28e24e19fffb5e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66066877"
---
# <a name="perspectives-ssas-tabular"></a>Perspektiven (SSAS – tabellarisch)
  In tabellarischen Modellen definiert eine Perspektive sichtbare Teilmengen eines Modells, die fokussierte, unternehmensspezifische oder anwendungsspezifische Blickpunkte des Modells bereitstellen.  
  
 Abschnitte in diesem Thema:  
  
-   [Vorteile](#bkmk_understanding)  
  
-   [Testen von Perspektiven](#bkmk_testpersp)  
  
-   [Verwandte Aufgaben](#bkmk_related_tasks)  
  
##  <a name="bkmk_understanding"></a> Vorteile  
 Die Suche in tabellarischen Modellen kann sich für den Benutzer als sehr schwierig erweisen. In einem einzelnen Modell kann der Inhalt eines vollständigen Data Warehouses mit vielen Tabellen, Measures und Dimensionen abgebildet sein. Eine solche Komplexität kann entmutigend für Benutzer sein, die oft nur mit einem kleinen Teil des Modells interagieren müssen, um ihre Business Intelligence- und Berichterstellungsanforderungen zu erfüllen.  
  
 In einer Perspektive werden Tabellen, Spalten und Measures (einschließlich KPIs) als Feldobjekte definiert. Sie können die Anzeigefelder für jede Perspektive auswählen. Ein einzelnes Modell kann beispielsweise Produkt-, Vertriebs-, Finanz-, Mitarbeiter- und geografische Daten vereinen. Eine Vertriebsabteilung arbeitet in erster Linie mit Produkt-, Vertriebs-, Marketing- und geografischen Daten, während Mitarbeiter- und Finanzdaten eher nicht benötigt werden. Entsprechend sind für eine Personalabteilung Daten über Verkaufswerbungen und Vertriebsgebiete nicht von Belang.  
  
 Wenn ein Benutzer eine Verbindung mit einem Modell (als Datenquelle) herstellt, für das Perspektiven definiert sind, kann er die gewünschte Perspektive auswählen. Wenn Mitarbeiter der Personalabteilung eine Verbindung mit einer Modelldatenquelle in Excel herstellen, können sie im Datenverbindungs-Assistenten auf der Seite Tabellen und Sichten auswählen beispielsweise die Perspektive Human Ressources auswählen. In der PivotTable-Feldliste werden nur die für die Perspektive Human Resources definierten Felder (Tabellen, Spalten und Measures) angezeigt.  
  
 Perspektiven sollen nicht als Sicherheitsmechanismus verwendet werden, sondern als Tool zur Verbesserung der Benutzerfreundlichkeit. Die gesamte Sicherheit einer bestimmten Perspektive wird vom zugrunde liegenden Modell geerbt. Perspektiven gewähren keinen Zugriff auf Modellobjekte, auf die ein Benutzer nicht bereits Zugriff hat. Die Sicherheit der Modelldatenbank muss geklärt werden, damit der Zugriff auf Objekte im Modell durch eine Perspektive ermöglicht werden kann. Sicherheitsrollen können verwendet werden, um Modellmetadaten und Daten zu sichern. Weitere Informationen finden Sie unter [Rollen &#40;SSAS – tabellarisch&#41;](roles-ssas-tabular.md).  
  
##  <a name="bkmk_testpersp"></a> Testen von Perspektiven  
 Bei der Modellerstellung können Sie die Funktion In Excel analysieren im Modell-Designer verwenden, um die Wirksamkeit der definierten Perspektiven zu testen. Wenn Sie im Menü **Modell** im Modell-Designer auf **In Excel analysieren**klicken, bevor Excel geöffnet wird, wird das Dialogfeld **Anmeldeinformationen und Perspektive auswählen** angezeigt. In diesem Dialogfeld können Sie den aktuellen Benutzernamen, einen anderen Benutzer, eine Rolle und eine Perspektive angeben, um darüber eine Verbindung mit der Arbeitsbereichsdatenbank des Modells als Datenquelle herzustellen und Daten anzuzeigen.  
  
##  <a name="bkmk_related_tasks"></a> Verwandte Aufgaben  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Erstellen und Verwalten von Perspektiven &#40;SSAS – tabellarisch&#41;](perspectives-ssas-tabular.md)|Beschreibt, wie Sie Perspektiven über das Dialogfeld Perspektiven im Modell-Designer erstellen und verwalten.|  
  
## <a name="see-also"></a>Siehe auch  
 [Rollen &#40;SSAS – tabellarisch&#41;](roles-ssas-tabular.md)   
 [Hierarchien &#40;SSAS – tabellarisch&#41;](hierarchies-ssas-tabular.md)  
  
  
