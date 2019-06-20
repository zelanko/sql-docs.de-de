---
title: Wählen Sie Paketverwaltungsoptionen (SSIS-PaketUpgrade-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectpackagemgtoptions.f1
ms.assetid: 810fc020-51cd-43ed-9f35-af99b4f35947
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c71f254b0d0fb79e3ee8135c10d2d9ed715d3437
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66056029"
---
# <a name="select-package-management-options-ssis-package-upgrade-wizard"></a>Paketverwaltungsoptionen auswählen (SSIS Paketupgrade-Assistent)
  Verwenden Sie die Seite **Paketverwaltungsoptionen auswählen** , um Optionen für Paketupgrades anzugeben.  
  
 **So führen Sie den SSIS Paketupgrade-Assistenten aus**  
  
-   [Aktualisieren von Integration Services-Paketen mit dem SSIS-Paketupgrade-Assistenten](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="options"></a>Optionen  
 **Verbindungszeichenfolgen zum Verwenden neuer Anbieternamen aktualisieren**  
 Aktualisieren Sie die Verbindungszeichenfolgen, um für die aktuelle Version von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]die Namen für die folgenden Anbieter zu verwenden:  
  
-   OLE DB-Anbieter für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client  
  
 Der [!INCLUDE[ssIS](../includes/ssis-md.md)] -Paketupgrade-Assistent aktualisiert nur Verbindungszeichenfolgen, die in Verbindungs-Managern gespeichert sind. Der Assistent aktualisiert keine Verbindungszeichenfolgen, die dynamisch mithilfe der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Ausdruckssprache oder mithilfe von Code in einem Skripttask erstellt wurden.  
  
 **Upgradepakete überprüfen**  
 Überprüfen Sie die Upgradepakete, und speichern Sie nur die Upgradepakete, die die Überprüfung bestehen.  
  
 Wenn Sie diese Option nicht aktivieren, überprüft der Assistent keine Upgradepakete. Deshalb speichert der Assistent alle Upgradepakete, unabhängig davon, ob die Pakete gültig sind oder nicht. Der Assistent speichert Upgradepakete unter dem Ziel, das auf der Seite **Zielspeicherort auswählen** des Assistenten angegeben ist.  
  
 Die Überprüfung verlängert die Dauer des Upgradevorgangs. Es wird empfohlen, diese Option für große Pakete, die voraussichtlich erfolgreich aktualisiert werden, nicht zu aktivieren.  
  
 **Neue Paket-IDs erstellen**  
 Erstellen Sie neue Paket-IDs für die Upgradepakete.  
  
 **Upgradeprozess bei fehlerhaftem Paketupgrade fortsetzen**  
 Legen Sie fest, dass der [!INCLUDE[ssIS](../includes/ssis-md.md)] -Paketupgrade-Assistent mit dem Upgrade der restlichen Pakete fortfährt, wenn ein Paket nicht aktualisiert werden kann.  
  
 **Paketnamenskonflikte**  
 Geben Sie an, wie der Assistent Pakete behandeln soll, die denselben Namen haben. Für diese Option sind die in der folgenden Tabelle aufgeführten Werte verfügbar.  
  
 **Vorhandene Paketdateien überschreiben**  
 Ersetzt das vorhandene Paket durch das Upgradepaket desselben Namens.  
  
 **Zum Aktualisieren von Paketnamen numerische Suffixe hinzufügen**  
 Fügt dem Namen des Upgradepakets ein numerisches Suffix hinzu.  
  
 **Kein Upgrade für Pakete durchführen**  
 Unterbricht das Upgrade der Pakete und zeigt einen Fehler an, wenn Sie den Assistenten abschließen.  
  
 Diese Optionen sind nicht verfügbar, wenn Sie die Option **An Quellspeicherort speichern** auf der Seite **Zielspeicherort auswählen** des Assistenten auswählen.  
  
 **Konfigurationen ignorieren**  
 Lädt keine Paketkonfigurationen während des Paketupgrades. Durch Auswahl dieser Option wird weniger Zeit für das Paketupgrade benötigt.  
  
 **Originalpakete sichern**  
 Lassen Sie den Assistenten die Originalpakete in einem **SSISBackupFolder** -Ordner sichern. Der Assistent erstellt den **SSISBackupFolder** -Ordner als Unterordner des Ordners, der die Originalpakete und die Upgradepakete enthält.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn Sie festlegen, dass die Originalpakete und die Upgradepakete im Dateisystem und im selben Ordner gespeichert werden.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Aktualisieren von Integration Services-Paketen mit dem SSIS Paketupgrade-Assistenten](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren von Integration Services-Paketen](install-windows/upgrade-integration-services-packages.md)  
  
  
