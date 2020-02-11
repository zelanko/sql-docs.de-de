---
title: Hinzufügen oder Entfernen von Tabellen oder Sichten in einer Datenquellen Sicht (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: da7169cc95b768324e18f1ab5fd7b0a33615f99a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66077468"
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>Hinzufügen oder Entfernen von Tabellen oder Sichten in einer Datenquellensicht (Analysis Services)
  Nachdem Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]eine Datenquellensicht (Data Source View, DSV) erstellt haben, können Sie sie im Datenquellensicht-Designer ändern, indem Sie Tabellen und Spalten hinzufügen oder entfernen. Dies schließt auch Tabellen und Spalten aus einer anderen Datenquelle ein.  
  
 Um die DSV im Datenquellensicht-Designer zu öffnen, doppelklicken Sie im Projektmappen-Explorer auf die DSV. Sobald die DSV geöffnet ist, können Sie sie mit dem Befehl **Tabellen hinzufügen/entfernen** auf der Schaltflächenleiste oder im Menü ändern oder erweitern. Sie können auch mit den Objekten im Diagramm arbeiten. Sie können z. B. ein Objekt auswählen und es dann mit der ENTF-TASTE auf der Tastatur entfernen.  
  
> [!WARNING]  
>  Gehen Sie beim Entfernen einer Tabelle mit Bedacht vor. Beim Entfernen einer Tabelle werden alle zugeordneten Spalten und Beziehungen aus der DSV gelöscht und alle an die Tabelle gebundenen Objekte ungültig.  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>Auswählen von Tabellen oder Sichten für das Hinzufügen oder Entfernen  
 Im Dialogfeld **Tabellen hinzufügen/entfernen** können Sie Tabellen oder Sichten zwischen den Listen **Verfügbare Objekte** und **Eingeschlossene Objekte** verschieben. Die Liste **Verfügbare Objekte** enthält zunächst alle Tabellen oder Sichten der Primärdatenquelle, die nicht bereits in der Datenquellensicht enthalten sind. Falls die primäre Datenquelle die `OPENROWSET`-Funktion unterstützt, können Sie auch Tabellen oder Sichten aus anderen Datenquellen des Projekts oder der Datenbank hinzufügen.  
  
 Wenn in einer DSV eine Tabelle hinzugefügt oder entfernt wird, wird die Tabelle ebenfalls im aktuell ausgewählten Diagramm in der DSV hinzugefügt bzw. entfernt. Weitere Informationen finden Sie unter [Verwenden von Diagrammen im Datenquellensicht-Designer &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md).  
  
 Nach dem Verschieben einer Tabelle in die Liste **Eingeschlossene Objekte** des Dialogfelds **Tabellen hinzufügen/entfernen** können Sie alle verknüpften Tabellen hinzufügen. Durch diesen Vorgang werden der Datenquelle Tabellen nach Maßgabe von Fremdschlüsseleinschränkungen (soweit vorhanden) hinzugefügt. Sind keine Fremdschlüsseleinschränkungen vorhanden, können Sie mithilfe der `NameMatchingCriteria`-Eigenschaft der Datenquellensicht Beziehungen festlegen, indem Sie ein Kriterium für die Zuordnung von Spaltennamen in Tabellen zur Generierung möglicher Beziehungen angeben. Wenn die `NameMatchingCriteria`Eigenschaft für die Datenquellen Sicht angegeben ist, klicken Sie auf verknüpfte **Tabellen hinzufügen** , um Tabellen aus der Datenquelle hinzuzufügen, die über übereinstimmende Spaltennamen verfügen. Weitere Informationen zum Festlegen der `NameMatchingCriteria` -Eigenschaft finden Sie unter [Datenquellen Sichten in mehrdimensionalen Modellen](data-source-views-in-multidimensional-models.md).  
  
> [!NOTE]  
>  Das Hinzufügen oder Entfernen von Objekten in einer Datenquellensicht hat keine Auswirkungen auf die zugrunde liegende Datenquelle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellen Sichten in mehrdimensionalen Modellen](data-source-views-in-multidimensional-models.md)   
 [Arbeiten mit Diagrammen im Datenquellen Sicht-Designer &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
