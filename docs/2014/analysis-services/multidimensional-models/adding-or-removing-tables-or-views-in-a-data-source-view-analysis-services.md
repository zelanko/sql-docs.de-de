---
title: Hinzufügen oder Entfernen von Tabellen oder Sichten in einer Datenquellensicht (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.tablespane.f1
helpviewer_keywords:
- deleting tables
- tables [Analysis Services]
- removing tables
- adding tables
- data source views [Analysis Services], tables
- tables [Analysis Services], data source views
ms.assetid: 98307d04-6548-4d7d-9244-2371dd165249
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dc78ad1f8a1f49d1a42c5b2ded45a913cdd7e669
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117952"
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>Hinzufügen oder Entfernen von Tabellen oder Sichten in einer Datenquellensicht (Analysis Services)
  Nachdem Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]eine Datenquellensicht (Data Source View, DSV) erstellt haben, können Sie sie im Datenquellensicht-Designer ändern, indem Sie Tabellen und Spalten hinzufügen oder entfernen. Dies schließt auch Tabellen und Spalten aus einer anderen Datenquelle ein.  
  
 Um die DSV im Datenquellensicht-Designer zu öffnen, doppelklicken Sie im Projektmappen-Explorer auf die DSV. Sobald die DSV geöffnet ist, können Sie sie mit dem Befehl **Tabellen hinzufügen/entfernen** auf der Schaltflächenleiste oder im Menü ändern oder erweitern. Sie können auch mit den Objekten im Diagramm arbeiten. Sie können z. B. ein Objekt auswählen und es dann mit der ENTF-TASTE auf der Tastatur entfernen.  
  
> [!WARNING]  
>  Gehen Sie beim Entfernen einer Tabelle mit Bedacht vor. Beim Entfernen einer Tabelle werden alle zugeordneten Spalten und Beziehungen aus der DSV gelöscht und alle an die Tabelle gebundenen Objekte ungültig.  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>Auswählen von Tabellen oder Sichten für das Hinzufügen oder Entfernen  
 Im Dialogfeld **Tabellen hinzufügen/entfernen** können Sie Tabellen oder Sichten zwischen den Listen **Verfügbare Objekte** und **Eingeschlossene Objekte** verschieben. Die Liste **Verfügbare Objekte** enthält zunächst alle Tabellen oder Sichten der Primärdatenquelle, die nicht bereits in der Datenquellensicht enthalten sind. Wenn die primäre unterstützt Datenquelle die `OPENROWSET` -Funktion, Sie können auch Tabellen oder Sichten aus anderen Datenquellen im Projekt oder der Datenbank hinzufügen.  
  
 Wenn in einer DSV eine Tabelle hinzugefügt oder entfernt wird, wird die Tabelle ebenfalls im aktuell ausgewählten Diagramm in der DSV hinzugefügt bzw. entfernt. Weitere Informationen finden Sie unter [Verwenden von Diagrammen im Datenquellensicht-Designer &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md).  
  
 Nach dem Verschieben einer Tabelle in die Liste **Eingeschlossene Objekte** des Dialogfelds **Tabellen hinzufügen/entfernen** können Sie alle verknüpften Tabellen hinzufügen. Durch diesen Vorgang werden der Datenquelle Tabellen nach Maßgabe von Fremdschlüsseleinschränkungen (soweit vorhanden) hinzugefügt. Wenn die foreign Key-Einschränkungen nicht vorhanden sind, können Sie mithilfe der `NameMatchingCriteria` Eigenschaft der Datenquellensicht Beziehungen festlegen, indem Sie ein Kriterium für die Zuordnung von Spaltennamen in Tabellen zur Generierung möglicher Beziehungen angeben. Wenn die `NameMatchingCriteria`für die Datenquellensicht angegeben wird, klicken Sie auf **verknüpfte Tabellen hinzufügen** zum Hinzufügen von Tabellen aus der Datenquelle, die Zuordnung von Spaltennamen. Weitere Informationen zum Einrichten der `NameMatchingCriteria` -Eigenschaft finden Sie unter [Datenquellensichten in mehrdimensionalen Modellen](data-source-views-in-multidimensional-models.md).  
  
> [!NOTE]  
>  Das Hinzufügen oder Entfernen von Objekten in einer Datenquellensicht hat keine Auswirkungen auf die zugrunde liegende Datenquelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellsichten in mehrdimensionalen Modellen](data-source-views-in-multidimensional-models.md)   
 [Verwenden von Diagrammen im Datenquellensicht-Designer &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
