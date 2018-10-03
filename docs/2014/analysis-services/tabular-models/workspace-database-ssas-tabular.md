---
title: Arbeitsbereichsdatenbank (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 662daf08-a514-44a7-8675-44644aa454a2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 65d4a23044084f18662c3aca1cc68bfd157ea3dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134990"
---
# <a name="workspace-database-ssas-tabular"></a>Arbeitsbereichsdatenbank (SSAS – tabellarisch)
  Die Arbeitsbereichsdatenbank für Tabellenmodelle, die während der Modellerstellung verwendet wird, wird erstellt, wenn Sie ein Projekt für Tabellenmodelle in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]anlegen. Die Arbeitsbereichsdatenbank befindet sich im Arbeitsspeicher auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz, die im tabellarischen Modus ausgeführt wird. In der Regel ist sie auf dem gleichen Computer wie [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] installiert.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Übersicht über arbeitsbereichsdatenbanken](#bkmk_overview)  
  
-   [Eigenschaften von arbeitsbereichsdatenbanken](#bkmk_ws_prop)  
  
-   [Verwenden von SSMS zur Verwaltung von Arbeitsbereichsdatenbanken](#bkmk_use_ssms)  
  
-   [Verwandte Aufgaben](#bkmk_related_tasks)  
  
##  <a name="bkmk_overview"></a> Übersicht über arbeitsbereichsdatenbanken  
 Eine Arbeitsbereichsdatenbank wird auf der von der Eigenschaft Arbeitsbereichsserver angegebenen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz erstellt, wenn ein neues Business Intelligence-Projekt anhand einer der Projektvorlagen für tabellarische Modelle in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]erstellt wird. Jedes tabellarische Modellprojekt verfügt über eine eigene Arbeitsbereichsdatenbank. Sie können [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden, um die Arbeitsbereichsdatenbank auf dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server anzuzeigen. Der Name der Arbeitsbereichsdatenbank umfasst den Projektnamen, gefolgt von einem Unterstrich, dem Benutzernamen, einem weiteren Unterstrich und einer GUID.  
  
 Die Arbeitsbereichsdatenbank befindet sich im Arbeitsspeicher, während das tabellarische Modellprojekt in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]geöffnet ist. Wenn Sie das Projekt schließen, wird die Arbeitsbereichsdatenbank entweder im Arbeitsspeicher beibehalten, auf dem Datenträger gespeichert und aus dem Arbeitsspeicher entfernt (Standardeinstellung) oder aus dem Arbeitsspeicher entfernt und nicht auf dem Datenträger gespeichert. Dies hängt von der Einstellung der Eigenschaft Arbeitsbereich beibehalten ab. Weitere Informationen zur Eigenschaft Arbeitsbereich beibehalten finden Sie weiter unten im Abschnitt [Eigenschaften von Arbeitsbereichsdatenbanken](#bkmk_ws_prop) .  
  
 Nachdem Sie dem Modellprojekt mit dem Tabellenimport-Assistenten oder mit Kopieren/Einfügen Daten hinzugefügt haben, zeigen Sie die Arbeitsbereichsdatenbank an, wenn Sie Tabellen, Spalten und Daten im Modell-Designer anzeigen. Wenn Sie weitere Tabellen, Spalten, Beziehungen usw. hinzufügen, ändern Sie die Arbeitsbereichsdatenbank.  
  
> [!IMPORTANT]  
>  Wenn eine der Tabellen im Modell eine große Anzahl von Zeilen aufweist, erwägen Sie, während der Modellerstellung nur eine Teilmenge der Daten zu importieren. Sie können die Verarbeitungszeit und den Verbrauch von Arbeitsbereichsdatenbank-Serverressourcen reduzieren, indem Sie eine Teilmenge der Daten importieren.  
  
> [!NOTE]  
>  Das Vorschaufenster auf der Seite Tabellen und Sichten auswählen im Tabellenimport-Assistenten im Dialogfeld Tabelleneigenschaften bearbeiten und im Dialogfeld Partitions-Manager enthält die Tabellen, Spalten und Zeilen in der Datenquelle und kann nicht die gleichen Tabellen, Spalten und Zeilen enthalten wie die Arbeitsbereichsdatenbank.  
  
 Wenn Sie ein tabellarisches Modellprojekt bereitstellen, wird die bereitgestellte Modelldatenbank, die letztlich eine Kopie der Arbeitsbereichsdatenbank ist, auf der in der Bereitstellungsserver-Eigenschaft angegebenen Analysis Server-Instanz erstellt. Weitere Informationen zur Bereitstellungsserver-Eigenschaft finden Sie unter [Projekteigenschaften &#40;SSAS – tabellarisch&#41;](properties-ssas-tabular.md).  
  
 Die Arbeitsbereichsdatenbank des Modells befindet sich in der Regel auf "localhost" oder einer lokalen benannten Instanz eines [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Servers. Sie können die Arbeitsbereichsdatenbank mithilfe einer Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] hosten, diese Konfiguration wird jedoch aufgrund der Latenzzeit während Datenabfragen und anderer Einschränkungen nicht empfohlen. Im Idealfall werden die Arbeitsbereichsdatenbanken von der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz auf demselben Computer gehostet wie [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Wenn Modellprojekte auf demselben Computer wie die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz erstellt werden, von der die Arbeitsbereichsdatenbank gehostet wird, kann sich dies leistungssteigernd auswirken.  
  
 Remote-Arbeitsbereichsdatenbanken unterliegen folgenden Einschränkungen:  
  
-   Potenzielle Latenzzeit während der Abfragen.  
  
-   Die Eigenschaft **Datensicherung**kann nicht auf Auf Datenträger sichern festgelegt werden.  
  
-   Sie können keine Daten aus einer PowerPivot-Arbeitsmappe importieren, wenn Sie mit der Projektvorlage für das Importieren von Daten aus PowerPivot ein neues Tabellenmodellprojekt erstellen.  
  
##  <a name="bkmk_ws_prop"></a> Eigenschaften von Arbeitsbereichsdatenbanken  
 Die Eigenschaften von Arbeitsbereichsdatenbanken sind in den Modelleigenschaften enthalten. Um Modelleigenschaften in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]im **Projektmappen-Explorer**anzuzeigen, klicken Sie auf die Datei **Model.bim** . Modelleigenschaften können mit dem **Eigenschaftenfenster** konfiguriert werden. Die Eigenschaften von Arbeitsbereichsdatenbanken umfassen:  
  
> [!NOTE]  
>  Auf die Eigenschaften**Arbeitsbereichsserver**, **Arbeitsbereich beibehalten**und **Datensicherung** werden beim Erstellen eines neuen Modellprojekts die Standardeinstellungen angewendet. Die Standardeinstellungen für neue Modellprojekte können auf der Seite **Datenmodellierung** in den Einstellungen für **Analysis-Server** im Dialogfeld „Extras/Optionen“ geändert werden. Diese und andere Eigenschaften können auch für jedes Modellprojekt im **Eigenschaftenfenster** festgelegt werden. Änderungen an den Standardeinstellungen wirken sich nicht auf bereits erstellte Modellprojekte aus. Weitere Informationen finden Sie unter [Konfigurieren von Standarddatenmodellierung und Bereitstellungseigenschaften &#40;SSAS – tabellarisch&#41;](configure-default-data-modeling-and-deployment-properties-ssas-tabular.md).  
  
|Eigenschaft|Standardeinstellung|Description|  
|--------------|---------------------|-----------------|  
|**Arbeitsbereichsdatenbank**|Der Projektname, gefolgt von einem Unterstrich, dem Benutzernamen, einem weiteren Unterstrich und einer GUID.|Der Name der Arbeitsbereichsdatenbank, die zum Speichern und Bearbeiten des Modells im Arbeitsspeicher verwendet wird. Nachdem ein tabellarisches Modellprojekt erstellt wurde, wird diese Datenbank in der in der Eigenschaft [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Arbeitsbereichsserver **angegebenen** -Instanz angezeigt. Diese Eigenschaft kann nicht im Eigenschaftenfenster festgelegt werden.|  
|**Arbeitsbereich beibehalten**|In Arbeitsspeicher entladen|Gibt an, wie eine Arbeitsbereichsdatenbank beibehalten wird, nachdem ein Modellprojekt geschlossen wurde. Eine Arbeitsbereichsdatenbank enthält Modellmetadaten, die in ein Modell importiert wurden. In einigen Fällen kann die Arbeitsbereichsdatenbank sehr groß sein und viel Arbeitsspeicher benötigen. Wenn Sie ein Modellprojekt in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]schließen, wird die Arbeitsbereichsdatenbank standardmäßig aus dem Arbeitsspeicher entladen. Wenn Sie diese Einstellung ändern, sind die folgenden Überlegungen wichtig: verfügbare Speicherressourcen und wie häufig das Modellprojekt bearbeitet werden soll. Für diese Eigenschafteneinstellung gibt es die folgenden Optionen:<br /><br /> **Im Arbeitsspeicher beibehalten** : Gibt an, dass die Arbeitsbereichsdatenbank im Arbeitsspeicher beibehalten wird, nachdem ein Modellprojekt geschlossen wurde. Diese Option erfordert mehr Arbeitsspeicher. Wenn Sie jedoch ein Modellprojekt in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]öffnen, werden weniger Ressourcen belegt, und die Arbeitsbereichsdatenbank wird schneller geladen.<br /><br /> **Aus dem Arbeitsspeicher entladen** : Gibt an, dass die Arbeitsbereichsdatenbank auf dem Datenträger, aber nicht im Arbeitsspeicher beibehalten wird, nachdem ein Modellprojekt geschlossen wurde. Diese Option belegt weniger Arbeitsspeicher. Wenn Sie jedoch ein Modellprojekt in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]öffnen, muss die Arbeitsbereichsdatenbank erneut angefügt werden. Zusätzliche Ressourcen werden belegt, und das Laden des Modellprojekts dauert länger, als wenn die Arbeitsbereichsdatenbank im Arbeitsspeicher beibehalten wird. Verwenden Sie diese Option, wenn die Arbeitsspeicherressourcen beschränkt sind, oder wenn Sie mit einer Remote-Arbeitsbereichsdatenbank arbeiten.<br /><br /> **Arbeitsbereich löschen** : Gibt an, dass die Arbeitsbereichsdatenbank aus dem Arbeitsspeicher gelöscht und nicht auf dem Datenträger beibehalten wird, nachdem das Modellprojekt geschlossen wurde. Diese Option erfordert weniger Arbeitsspeicher und Speicherplatz. Wenn Sie jedoch ein Modellprojekt in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]öffnen, werden zusätzliche Ressourcen belegt, und das Laden des Modellprojekts dauert länger, als wenn die Arbeitsbereichsdatenbank im Arbeitsspeicher oder auf dem Datenträger beibehalten wird. Verwenden Sie diese Option, wenn Sie nur gelegentlich an Modellprojekten arbeiten.<br /><br /> <br /><br /> Die Standardeinstellung für diese Eigenschaft kann auf der Seite **Datenmodellierung** in den Einstellungen für **Analysis-Server** im Dialogfeld „Extras/Optionen“ geändert werden.|  
|**Arbeitsbereichsserver**|localhost|Diese Eigenschaft gibt den Standardserver an, der zum Hosten der Arbeitsbereichsdatenbank verwendet wird, während das Modellprojekt in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]erstellt wird. Alle verfügbaren [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanzen, die auf dem lokalen Computer ausgeführt werden, sind im Listenfeld enthalten.<br /><br /> Um einen anderen (im tabellarischen Modus ausgeführten) [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server anzugeben, geben Sie den Servernamen ein. Der angemeldete Benutzer muss Administrator auf dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server sein.<br /><br /> Es wird empfohlen, Sie geben Sie einen lokalen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Server als arbeitsbereichsserver. Für Arbeitsbereichsdatenbanken auf einem Remoteserver wird das Importieren aus PowerPivot nicht unterstützt. Außerdem können Daten nicht lokal gesichert werden, und bei Abfragen kommt es auf der Benutzeroberfläche möglicherweise zu Latenzen.<br /><br /> Beachten Sie, dass die Standardeinstellung für diese Eigenschaft auf der Seite Datenmodellierung geändert werden kann [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Einstellungen im Dialogfeld Extras/Optionen.|  
  
##  <a name="bkmk_use_ssms"></a> Verwenden von SSMS zur Verwaltung von Arbeitsbereichsdatenbanken  
 Sie können [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) verwenden, um eine Verbindung mit dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Server herzustellen, auf dem die Arbeitsbereichsdatenbank gehostet wird. In der Regel ist keine Verwaltung der Arbeitsbereichsdatenbank erforderlich. Eine Ausnahme liegt jedoch vor, wenn eine Arbeitsbereichsdatenbank getrennt oder gelöscht werden soll. Diese Schritte müssen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]vorgenommen werden.  
  
> [!WARNING]  
>  Verwenden Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] nicht, um die Arbeitsbereichsdatenbank zu verwalten, während das Projekt im Modell-Designer geöffnet ist. Dies kann zu Datenverlusten führen.  
  
##  <a name="bkmk_related_tasks"></a> Verwandte Aufgaben  
  
|Thema|Description|  
|-----------|-----------------|  
|[Modelleigenschaften &#40;SSAS – tabellarisch&#41;](model-properties-ssas-tabular.md)|Enthält Beschreibungen und Konfigurationsschritte der Arbeitsbereichsdatenbank-Eigenschaften eines Modells.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Standarddatenmodellierung und Bereitstellungseigenschaften &#40;SSAS – tabellarisch&#41;](configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)   
 [Projekteigenschaften &#40;SSAS – tabellarisch&#41;](properties-ssas-tabular.md)  
  
  
