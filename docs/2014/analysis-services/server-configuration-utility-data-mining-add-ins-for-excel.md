---
title: Hilfsprogramm für die Server Konfiguration (Data Mining-Add-Ins für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 28435f86-5cec-4a1e-9b7d-b2069c1ddddb
author: minewiskan
ms.author: owend
ms.openlocfilehash: f8a2006947cf4e4bffee0365ffbbf0b3b1c76bbf
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940731"
---
# <a name="server-configuration-utility-data-mining-add-ins-for-excel"></a>Serverkonfigurations-Hilfsprogramm (Data Mining-Add-Ins für Excel)
  Wenn Sie die Data Mining-Add-Ins für Excel installieren, wird auch ein Server Konfigurationsprogramm installiert, das beim erstmaligen Öffnen der Add-Ins ausgeführt wird. In diesem Thema wird beschrieben, wie das-Hilfsprogramm verwendet wird, um eine Verbindung mit einer Instanz von herzustellen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] und eine Datenbank für die Arbeit mit Data Mining Modellen einzurichten.  
  

  
##  <a name="step-1-connect-to-analysis-services"></a><a name="bkmk_step1"></a>Schritt 1: Herstellen einer Verbindung mit Analysis Services  
 Wählen Sie den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server aus, der die Data Mining-Algorithmen bereitstellt und auf dem die Data Mining-Modelle gespeichert werden.  
  
 Beim Erstellen einer Verbindung zum Ermöglichen des Data Mining sollten Sie einen Server auswählen, auf dem Sie mit Data Mining-Modellen experimentieren können. Es empfiehlt sich, dass Sie eine neue Datenbank auf dem Server erstellen und die neue Datenbank für das Data Mining reservieren. Sie können sich auch an Ihren Administrator wenden, damit dieser einen Data Mining-Server für Sie vorbereitet. Auf diese Weise können Sie Modelle erstellen, ohne dass die Leistung anderer Dienste beeinträchtigt wird.  
  
 Beachten Sie, dass der für das Data Mining genutzte [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server sich nicht unbedingt auf demselben Server wie die Quelldaten befinden muss.  
  
 **Servername**  
 Geben Sie den Namen des Servers ein, auf dem sich die Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] befindet, die für das Data Mining verwendet werden soll.  
  
 **Authentifizierung**  
 Geben Sie die Authentifizierungsmethoden an. Die Windows-Authentifizierung ist für Verbindungen mit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] erforderlich, es sei denn, der Administrator hat den Zugriff auf den Server über die HTTPPump konfiguriert.  
  
##  <a name="step-2-allow-temporary-models"></a><a name="bkmk_step2"></a>Schritt 2: temporäre Modelle zulassen  
 Bevor Sie die Add-Ins verwenden können, muss eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Servereigenschaft geändert werden, um das Erstellen temporärer Miningmodelle zuzulassen.  
  
 Temporäre Mining Modelle werden auch als *Sitzungs Modelle*bezeichnet. Das liegt daran, dass die Modelle nur gespeichert werden, solange die aktuelle Sitzung geöffnet ist. Wenn Sie die Verbindung mit dem Server schließen, wird die Sitzung beendet, und alle während der Sitzung verwendeten Modelle werden gelöscht.  
  
 Das Verwenden von Sitzungsminingmodellen wirkt sich nicht auf den Speicherplatz des Servers aus. Die höhere Auslastung beim Erstellen von Data Mining-Modellen wirkt sich jedoch möglicherweise auf die Serverleistung aus.  
  
 Der Assistent erkennt zuerst die Einstellungen auf dem Server, den Sie angegeben haben. Wenn der Server temporäre Mining Modelle bereits zulässt, klicken Sie auf **weiter, um** den Vorgang fortzusetzen. Der Assistent bietet zudem Anweisungen zum Aktivieren temporärer Miningmodelle auf dem angegebenen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server sowie zum Senden von Anforderungen an den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Administrator.  
  
##  <a name="step-3-create-database-for-add-in-users"></a><a name="bkmk_step3"></a>Schritt 3: Erstellen einer Datenbank für Add-in-Benutzer  
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
  
##  <a name="step-4-give-add-in-users-appropriate-permissions"></a><a name="bkmk_step4"></a>Schritt 4: Add-in-Benutzern entsprechende Berechtigungen geben  
 Sie müssen sicherstellen, dass Sie (und alle anderen Benutzer, die die Add-Ins verwenden) über die erforderlichen Berechtigungen zum Durchsuchen, Bearbeiten, Verarbeiten oder Erstellen von Data Mining-Strukturen und -Modellen verfügen.  
  
 Standardmäßig ist die integrierte Windows-Authentifizierung erforderlich, um die Add-Ins zu verwenden.  
  
 **Add-In-Benutzern Administratorberechtigungen für die Datenbank erteilen**  
 Wählen Sie diese Option aus, um den aufgeführten Benutzern administrativen Zugriff auf die Datenbank zu gewähren.  
  
> [!NOTE]  
>  Diese Berechtigungen gelten nur für die Datenbank, die im Feld **Datenbankname** aufgelistet ist.  
  
 **Datenbankname**  
 Zeigt den Namen der ausgewählten Datenbank an.  
  
 **Hinzuzufügende Benutzer oder Gruppen angeben**  
 Wählen Sie die Anmeldenamen aus, die über Zugriff auf die für Data Mining verwendete Datenbank verfügen sollen.  
  
 **Add (Hinzufügen)**  
 Klicken Sie auf diese Option, um ein Dialogfeld zu öffnen und Benutzer oder Gruppen hinzuzufügen.  
  
 **Entfernen**  
 Klicken Sie auf diese Option, um den ausgewählten Benutzer oder die ausgewählte Gruppe aus der Liste der Benutzer mit Administratorberechtigungen zu entfernen.  
  
  
