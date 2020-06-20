---
title: Modell Eigenschaften (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.fileprop.f1
- sql12.asvs.bidtoolset.wspacedbconfig.f1
ms.assetid: 8ab04656-75a5-485c-9687-7b1ca49f7f80
author: minewiskan
ms.author: owend
ms.openlocfilehash: d4106377f2aadfec9173076ece3cf8bf4bc7d183
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938801"
---
# <a name="model-properties-ssas-tabular"></a>Model Properties (SSAS Tabular)
  In diesem Thema werden Eigenschaften für tabellarische Modelle beschrieben. Jedes Projekt für tabellarische Modelle in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] verfügt über Modelleigenschaften, die Einfluss darauf haben, wie das jeweilige Modell erstellt und gesichert und wie die Arbeitsbereichsdatenbank gespeichert wird. Die hier beschriebenen Modelleigenschaften gelten nicht für Modelle, die bereits bereitgestellt wurden.  
  
 Abschnitte in diesem Thema:  
  
-   [Modell Eigenschaften](#bkmk_model_properties)  
  
-   [So konfigurieren Sie Eigenschafteneinstellungen für Modelle](#bkmk_conf)  
  
##  <a name="model-properties"></a><a name="bkmk_model_properties"></a>Modell Eigenschaften  
 **Erweitert**  
  
|Eigenschaft|Standardeinstellung|Beschreibung|  
|--------------|---------------------|-----------------|  
|**Buildaktion**|Compile|Diese Eigenschaft gibt die Funktion der Datei beim Erstellungs- und Bereitstellungsprozess an. Für diese Eigenschafteneinstellung gibt es die folgenden Optionen:<br /><br /> **Kompilieren** : Es tritt eine normale Buildaktion auf. Definitionen für Modellobjekte werden in die ASDATABASE-Datei geschrieben.<br /><br /> **None** : die Ausgabe an die. asdatabase-Datei ist leer.|  
|**In Ausgabeverzeichnis kopieren**|Nicht kopieren|Diese Eigenschaft gibt an, dass die Quelldatei in das Ausgabeverzeichnis kopiert wird. Für diese Eigenschafteneinstellung gibt es die folgenden Optionen:<br /><br /> **Nicht kopieren** : im Ausgabeverzeichnis wird keine Kopie erstellt.<br /><br /> **Immer kopieren** : eine Kopie wird immer im Ausgabeverzeichnis erstellt.<br /><br /> **Kopieren, wenn neuer** – Im Ausgabeverzeichnis wird nur eine Kopie erstellt, wenn die Datei „model.bim“ geändert wurde.|  
  
 **Verschiedenes**  
  
> [!NOTE]  
>  Manche Eigenschaften werden beim Erstellen des Modells automatisch festgelegt und können nicht geändert werden.  
  
> [!NOTE]  
>  Auf die Eigenschaften Arbeitsbereichsserver, Arbeitsbereich beibehalten und Datensicherung werden beim Erstellen eines neuen Modellprojekts die Standardeinstellungen angewendet. Die Standardeinstellungen für neue Modelle können in den Einstellungen für Analysis-Server im Dialogfeld Extras/Optionen auf der Seite Datenmodellierung geändert werden. Diese und andere Eigenschaften können auch für jedes Modell im Eigenschaftenfenster festgelegt werden. Weitere Informationen finden Sie unter [Konfigurieren von Standarddatenmodellierung und Bereitstellungseigenschaften &#40;SSAS – tabellarisch&#41;](properties-ssas-tabular.md).  
  
|Eigenschaft|Standardeinstellung|BESCHREIBUNG|  
|--------------|---------------------|-----------------|  
|**Sortierung**|Die Standardsortierung für den Computer, für den Visual Studio installiert wurde.|Der Sortierungskennzeichner für das Modell.|  
|**Kompatibilitäts Grad**|Standardmäßiger oder anderer Wert ist beim Erstellen des Projekts ausgewählt.|Gilt für SQL Server 2012 Analysis Services SP1 oder höher. Gibt die für dieses Modell verfügbaren Funktionen und Einstellungen an. Weitere Informationen finden Sie unter [Kompatibilitäts Grad &#40;SSAS-tabellarischen SP1-&#41;](compatibility-level-for-tabular-models-in-analysis-services.md).|  
|**Datensicherung**|Nicht auf Datenträger sichern|Gibt an, ob eine Sicherung der Modelldaten in einer Sicherungsdatei beibehalten wird. Beachten Sie, dass die Standardeinstellung für diese Eigenschaft auf der Seite Datenmodellierung in Analysis-Server Einstellungen im Dialogfeld tools\optionen geändert werden kann. Für diese Eigenschafteneinstellung gibt es die folgenden Optionen:<br /><br /> **Auf Datenträger sichern** – Gibt an, dass eine Sicherung der Modelldaten auf dem Datenträger beibehalten wird. Wenn das Modell gespeichert wird, werden die Daten auch in der Sicherungsdatei (ABF) gespeichert. Wenn diese Option ausgewählt wird, dauert es möglicherweise länger, Modelle zu speichern und zu laden.<br /><br /> **Nicht auf Datenträger sichern** – Gibt an, dass keine Sicherung der Modelldaten auf dem Datenträger beibehalten wird. Diese Option minimiert die Speicher- und Ladezeiten für Modelle.|  
|**Directquery-Modus**|Aus|Gibt an, ob dieses Modell im DirectQuery-Modus ausgeführt wird. Weitere Informationen finden Sie unter [DirectQuery-Modus &#40;SSAS – tabellarisch&#41;](directquery-mode-ssas-tabular.md).|  
|**Dateiname**|Model.bim|Gibt den Namen der BIM-Datei an. Der Dateiname sollte nicht geändert werden.|  
|**Vollständiger Pfad**|Der beim Erstellen des Projekts angegebene Pfad.|Der Speicherort von model.bim. Diese Eigenschaft kann nicht im Eigenschaftenfenster festgelegt werden.|  
|**Sprache**|Englisch|Die Standardsprache des Modells. Die Standardsprache wird durch die für Visual Studio eingestellte Sprache bestimmt. Diese Eigenschaft kann nicht im Eigenschaftenfenster festgelegt werden.|  
|**Arbeitsbereichs Datenbank**|Der Projektname gefolgt von einem Unterstrich und einer GUID.|Der Name der Arbeitsbereichsdatenbank, die zum Speichern und Bearbeiten des Modells im Arbeitsspeicher für die ausgewählte Datei model.bim verwendet wird. Diese Datenbank wird in der in der Eigenschaft Arbeitsbereichsserver angegebenen Analysis Services-Instanz angezeigt. Diese Eigenschaft kann nicht im Eigenschaftenfenster festgelegt werden. Weitere Informationen finden Sie unter [Arbeitsbereichsdatenbank &#40;SSAS – tabellarisch&#41;](workspace-database-ssas-tabular.md).|  
|**Arbeitsbereich beibehalten**|Aus dem Arbeitsspeicher entladen|Gibt an, wie eine Arbeitsbereichsdatenbank beibehalten wird, nachdem ein Modell geschlossen wurde. Eine Arbeitsbereichsdatenbank enthält Modellmetadaten, die in ein Modell importierten Daten und Identitätswechselinformationen (verschlüsselt). In einigen Fällen kann die Arbeitsbereichsdatenbank sehr groß sein und viel Arbeitsspeicher benötigen. Standardmäßig werden Arbeitsbereichsdatenbanken aus dem Arbeitsspeicher entladen. Wenn Sie diese Einstellung ändern, sind die folgenden Überlegungen wichtig: verfügbare Speicherressourcen und wie häufig das Modell bearbeitet werden soll. Beachten Sie, dass die Standardeinstellung für diese Eigenschaft auf der Seite Datenmodellierung in Analysis-Server Einstellungen im Dialogfeld tools\optionen geändert werden kann. Für diese Eigenschafteneinstellung gibt es die folgenden Optionen:<br /><br /> **Im Arbeitsspeicher beibehalten** – Gibt an, dass die Arbeitsbereichsdatenbank im Arbeitsspeicher beibehalten wird, nachdem ein Modell geschlossen wurde. Diese Option erfordert mehr Arbeitsspeicher. Wenn Sie jedoch ein Modell in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]öffnen, werden weniger Ressourcen belegt, und die Arbeitsbereichsdatenbank wird schneller geladen.<br /><br /> **Aus dem Arbeitsspeicher entladen** – Gibt an, dass die Arbeitsbereichsdatenbank auf dem Datenträger, aber nicht im Arbeitsspeicher beibehalten wird, nachdem ein Modell geschlossen wurde. Diese Option erfordert weniger Arbeitsspeicher. Wenn Sie jedoch ein Modell in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]öffnen, werden zusätzliche Ressourcen belegt, und das Laden des Modells dauert länger, als bei einer Arbeitsbereichsdatenbank, die im Arbeitsspeicher beibehalten wird. Verwenden Sie diese Option, wenn die Arbeitsspeicherressourcen beschränkt sind, oder wenn Sie mit einer Remote-Arbeitsbereichsdatenbank arbeiten.<br /><br /> **Arbeitsbereich löschen** – Gibt an, dass die Arbeitsbereichsdatenbank aus dem Arbeitsspeicher gelöscht und nicht auf dem Datenträger beibehalten wird, nachdem das Modell geschlossen wurde. Diese Option erfordert weniger Arbeitsspeicher und Speicherplatz. Wenn Sie jedoch ein Modell in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]öffnen, werden zusätzliche Ressourcen belegt, und das Laden des Modells dauert länger, als bei einer Arbeitsbereichsdatenbank, die im Arbeitsspeicher oder auf dem Datenträger beibehalten wird. Verwenden Sie diese Option, wenn Sie nur gelegentlich an Modellen arbeiten.|  
|**Arbeitsbereichs Server**|localhost|Diese Eigenschaft gibt den Standardserver an, der zum Hosten der Arbeitsbereichsdatenbank verwendet wird, während das Modell in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellt wird. Alle verfügbaren Analysis Services-Instanzen, die auf dem lokalen Computer ausgeführt werden, sind im Listenfeld enthalten.<br /><br /> Hinweis: Es wird empfohlen, dass Sie immer einen lokalen Analysis Services-Server als Arbeitsbereichsserver angeben. Für Arbeitsbereichsdatenbanken auf einem Remoteserver wird das Importieren aus PowerPivot nicht unterstützt. Außerdem können Daten nicht lokal gesichert werden, und bei Abfragen kommt es auf der Benutzeroberfläche möglicherweise zu Latenzen.<br /><br /> Die Standardeinstellung für diese Eigenschaft kann in den Einstellungen für Analysis-Server im Dialogfeld Extras/Optionen auf der Seite Datenmodellierung geändert werden.|  
  
##  <a name="bkmk_conf_model_prop"></a>   
###  <a name="to-configure-model-property-settings"></a><a name="bkmk_conf"></a>So konfigurieren Sie Einstellungen für Modell Eigenschaften  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]in **Projektmappen-Explorer**auf die Datei **Model.bim** .  
  
2.  Klicken Sie im Fenster **Eigenschaften** auf eine Eigenschaft, und geben Sie dann einen Wert ein, oder klicken Sie auf den Pfeil nach unten, um eine Einstellungsoption auszuwählen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Standarddaten Modellierung und Bereitstellungs Eigenschaften &#40;tabellarischen SSAS-&#41;](properties-ssas-tabular.md)   
 [Projekteigenschaften &#40;SSAS – tabellarisch&#41;](project-properties-ssas-tabular.md)  
  
  
