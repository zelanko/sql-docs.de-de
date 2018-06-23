---
title: Serverkonfigurations-Hilfsprogramm (Data Mining-Add-ins für Excel) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 28435f86-5cec-4a1e-9b7d-b2069c1ddddb
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c51ea6b4e492bc238fee5ea3fea763f0fd5cb439
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058782"
---
# <a name="server-configuration-utility-data-mining-add-ins-for-excel"></a>Serverkonfigurations-Hilfsprogramm (Data Mining-Add-Ins für Excel)
  Beim Installieren der Data Mining-Add-Ins für Excel wird auch ein Serverkonfigurations-Hilfsprogramm installiert. Dieses wird beim erstmaligen Öffnen der Add-Ins ausgeführt. In diesem Thema wird beschrieben, wie Sie mit dem Hilfsprogramm eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] herstellen und eine Datenbank für das Verwenden von Data Mining-Modellen einrichten.  
  

  
##  <a name="bkmk_step1"></a> Schritt 1: Herstellen der Verbindung mit Analysis Services  
 Wählen Sie den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server aus, der die Data Mining-Algorithmen bereitstellt und auf dem die Data Mining-Modelle gespeichert werden.  
  
 Beim Erstellen einer Verbindung zum Ermöglichen des Data Mining sollten Sie einen Server auswählen, auf dem Sie mit Data Mining-Modellen experimentieren können. Es empfiehlt sich, dass Sie eine neue Datenbank auf dem Server erstellen und die neue Datenbank für das Data Mining reservieren. Sie können sich auch an Ihren Administrator wenden, damit dieser einen Data Mining-Server für Sie vorbereitet. Auf diese Weise können Sie Modelle erstellen, ohne dass die Leistung anderer Dienste beeinträchtigt wird.  
  
 Beachten Sie, dass der für das Data Mining genutzte [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server sich nicht unbedingt auf demselben Server wie die Quelldaten befinden muss.  
  
 **Servername**  
 Geben Sie den Namen des Servers ein, auf dem sich die Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] befindet, die für das Data Mining verwendet werden soll.  
  
 **Authentifizierung**  
 Geben Sie die Authentifizierungsmethoden an. Die Windows-Authentifizierung ist für Verbindungen mit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] erforderlich, es sei denn, der Administrator hat den Zugriff auf den Server über die HTTPPump konfiguriert.  
  
##  <a name="bkmk_step2"></a> Schritt 2: Erstellen temporärer Miningmodelle zulassen  
 Bevor Sie die Add-Ins verwenden können, muss eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Servereigenschaft geändert werden, um das Erstellen temporärer Miningmodelle zuzulassen.  
  
 Temporäre Miningmodelle werden auch als bezeichnet *sitzungsmodelle*. Das liegt daran, dass die Modelle nur gespeichert werden, solange die aktuelle Sitzung geöffnet ist. Wenn Sie die Verbindung mit dem Server schließen, wird die Sitzung beendet, und alle während der Sitzung verwendeten Modelle werden gelöscht.  
  
 Das Verwenden von Sitzungsminingmodellen wirkt sich nicht auf den Speicherplatz des Servers aus. Die höhere Auslastung beim Erstellen von Data Mining-Modellen wirkt sich jedoch möglicherweise auf die Serverleistung aus.  
  
 Der Assistent erkennt zuerst die Einstellungen auf dem Server, den Sie angegeben haben. Wenn der Server bereits temporäre Miningmodelle zulässt, können Sie klicken **Weiter** um den Vorgang fortzusetzen. Der Assistent bietet zudem Anweisungen zum Aktivieren temporärer Miningmodelle auf dem angegebenen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server sowie zum Senden von Anforderungen an den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Administrator.  
  
##  <a name="bkmk_step3"></a> Schritt 3: Erstellen der Datenbank für Add-in-Benutzern  
 Auf dieser Seite des Setup- und Konfigurations-Assistenten können Sie eine neue Datenbank erstellen, die für das Data Mining reserviert ist. Sie können aber auch eine vorhandene [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank auswählen.  
  
> [!WARNING]  
>  Data Mining erfordert eine Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], die im mehrdimensionalen Modus ausgeführt wird. Das Data Mining wird im Tabellenmodus nicht unterstützt.  
  
 Es empfiehlt sich, eine separate Datenbank zu erstellen, die für das Data Mining reserviert ist. Dadurch können Sie mit Data Mining-Modellen experimentieren, ohne dass andere Objekte der Projektmappe beeinträchtigt werden.  
  
 Wenn Sie eine vorhandene Datenbank in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]auswählen, beachten Sie Folgendes: Vorhandene Modelle können überschrieben werden, wenn Sie mit den Add-Ins ein Modell erstellen und ein gleichnamiges Modell bereits vorhanden ist.  
  
 **Neue Datenbank erstellen**  
 Wählen Sie diese Option aus, um eine neue Datenbank auf dem ausgewählten Server zu erstellen. In einer Data Mining-Datenbank werden die Datenquellen, Miningstrukturen und Miningmodelle gespeichert.  
  
 **Datenbankname**  
 Geben Sie den Namen der neuen Datenbank ein. Wenn der Name nicht bereits verwendet wird, wird er automatisch erstellt.  
  
 **Vorhandene Datenbank verwenden**  
 Wählen Sie diese Option aus, um eine vorhandene [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank zu verwenden.  
  
 **Datenbank**  
 Wenn Sie die Option zum Verwenden einer vorhandenen Datenbank ausgewählt haben, müssen Sie den Datenbanknamen in der Liste auswählen.  
  
##  <a name="bkmk_step4"></a> Schritt 4: Erteilen von Add-in-Benutzern entsprechende Berechtigungen  
 Sie müssen sicherstellen, dass Sie (und alle anderen Benutzer, die die Add-Ins verwenden) über die erforderlichen Berechtigungen zum Durchsuchen, Bearbeiten, Verarbeiten oder Erstellen von Data Mining-Strukturen und -Modellen verfügen.  
  
 Standardmäßig ist die integrierte Windows-Authentifizierung erforderlich, um die Add-Ins zu verwenden.  
  
 **Erteilen Sie Add-in-Benutzern Administratorberechtigungen für die Datenbank.**  
 Wählen Sie diese Option aus, um den aufgeführten Benutzern administrativen Zugriff auf die Datenbank zu gewähren.  
  
> [!NOTE]  
>  Diese Berechtigungen gelten nur für die Datenbank aufgelistet, die der **Datenbankname** Feld.  
  
 **Datenbankname**  
 Zeigt den Namen der ausgewählten Datenbank an.  
  
 **Geben Sie Benutzer oder Gruppen hinzufügen**  
 Wählen Sie die Anmeldenamen aus, die über Zugriff auf die für Data Mining verwendete Datenbank verfügen sollen.  
  
 **Hinzufügen**  
 Klicken Sie auf diese Option, um ein Dialogfeld zu öffnen und Benutzer oder Gruppen hinzuzufügen.  
  
 **Entfernen**  
 Klicken Sie auf diese Option, um den ausgewählten Benutzer oder die ausgewählte Gruppe aus der Liste der Benutzer mit Administratorberechtigungen zu entfernen.  
  
  