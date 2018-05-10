---
title: Tabelleneigenschaften | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 10729d80147a49f2c35195956616f0ce7cc0f08e
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2018
---
# <a name="table-properties"></a>Table Properties 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Dieser Artikel beschreibt Tabelleneigenschaften für tabellarische Modelle. Die hier beschriebenen Eigenschaften unterscheiden sich von den Eigenschaften im Dialogfeld Tabelleneigenschaften bearbeiten, mit denen definiert wird, welche Spalten aus der Quelle importiert werden.  
  
 Abschnitte in diesem Thema:  
  
-   [Tabelleneigenschaften](#bkmk_properties)  
  
-   [Konfigurieren der Einstellungen für Tabelleneigenschaften](#bkmk_config_prop)  
  
##  <a name="bkmk_properties"></a> Tabelleneigenschaften  
 **Standard**  
  
|Eigenschaft|Standardeinstellung|Description|  
|--------------|---------------------|-----------------|  
|**Verbindungsname**|\<Verbindungsname >|Der Name der Verbindung mit der Datenquelle der Tabelle.<br /><br /> Klicken Sie auf die Schaltfläche, um die Verbindung zu bearbeiten.|  
|**Hidden**|False|Gibt an, ob die Tabelle in den Feldlisten von Berichtserstellungsclients ausgeblendet wird.|  
|**Partitionen**||Partitionen für die Tabelle können nicht im **Eigenschaftenfenster** angezeigt werden. Klicken Sie zum Anzeigen, Erstellen oder Bearbeiten von Partitionen auf die Schaltfläche, um den Partitions-Manager zu öffnen.|  
|**Quelldaten**||Quelldaten für die Tabelle können nicht im **Eigenschaftenfenster** angezeigt werden. Klicken Sie zum Anzeigen oder Bearbeiten der Quelldaten auf die Schaltfläche, um das Dialogfeld Tabelleneigenschaften bearbeiten zu öffnen.|  
|**Tabellenbeschreibung**||Eine Textbeschreibung für die Tabelle.<br /><br /> Wenn ein Endbenutzer in [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]den Cursor über dieser Tabelle in der Feldliste platziert, wird die Beschreibung als QuickInfo angezeigt.|  
|**Tabellenname**|\<Anzeigename >|Gibt den Anzeigenamen der Tabelle an. Der Tabellenname kann angegeben werden, wenn eine Tabelle mit dem Tabellenimport-Assistenten importiert wird, oder jederzeit nach dem Import. Der Tabellenname im Modell kann sich von der zugeordneten Tabelle am Quellort unterscheiden. Der Anzeigename der Tabelle wird in der Feldliste einer Clientanwendung zur Berichterstellung sowie in der Modelldatenbank in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]angezeigt.|  
  
 **Berichterstellungseigenschaften**  
  
 Ausführliche Beschreibungen und Informationen zur Konfiguration für berichterstellungseigenschaften finden Sie unter [Power View-berichterstellungseigenschaften](../../analysis-services/tabular-models/power-view-reporting-properties-ssas-tabular.md).  
  
|Eigenschaft|Standardeinstellung|Description|  
|--------------|---------------------|-----------------|  
|**Standardfeldsatz**|||  
|Tabellenverhalten|||  
  
##  <a name="bkmk_config_prop"></a> Konfigurieren der Einstellungen für Tabelleneigenschaften  
  
1.  Klicken Sie im Modell-Designer in der Datensicht auf eine Tabelle (Registerkarte) oder in der Diagrammsicht auf einen Tabellenkopf.  
  
2.  Klicken Sie im **Eigenschaftenfenster** auf eine Eigenschaft, und geben Sie einen Wert ein, oder klicken Sie auf die Schaltfläche für weitere Konfigurationsoptionen.  
  
  
