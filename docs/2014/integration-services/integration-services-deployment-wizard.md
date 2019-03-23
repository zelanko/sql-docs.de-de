---
title: Integration Services-Bereitstellungs-Assistent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b091518f61944b3eb62f8abdc02f0270e086538a
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58389138"
---
# <a name="integration-services-deployment-wizard"></a>Bereitstellungs-Assistent für Integration Services
  Der Bereitstellungs-Assistent für [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt Projekte im SSISDB-Katalog auf einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz bereit, die das Projektbereitstellungsmodell verwendet.  
  
 Starten der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Bereitstellungs-Assistenten aus einem geöffneten Projekt im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Option **bereitstellen** aus der **Projekt** im Menü. Um den Assistenten zu starten, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], erweitern Sie die **Integration Services-Kataloge** > **SSISDB** mit der rechten Maustaste der Knoten im Objekt-Explorer die **Projekte** Ordner, und klicken Sie dann auf **-Projekt bereitstellen**.  
  
 Der Assistent führt Sie die folgenden vier Schritte aus. Klicken Sie auf **Weiter** mit dem nächsten Schritt, verschieben oder **zurück** zum vorherigen Schritt zurückgegeben.  
  
1.  **Wählen Sie Quelle** - Option der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt, das Sie bereitstellen möchten.  
  
2.  **Wählen Sie Ziel** -wählen Sie das Projektziel.  
  
3.  **Überprüfen Sie** -angezeigt.  
  
4.  **Bereitstellen/Ergebnisse** – stellt das Projekt bereit und zeigt die Ergebnisse an.  
  
## <a name="select-source"></a>Quellen auswählen  
 Um eine projektbereitstellungsdatei bereitzustellen, die Sie erstellt haben, wählen **projektbereitstellungsdatei** und geben Sie den Pfad zur ispac-Datei, oder klicken Sie auf **Durchsuchen** finden sie in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projektordner. Um ein Projekt bereitzustellen, das sich im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Katalog befindet, wählen Sie **Integration Services-Katalog**aus und geben dann den Servernamen und den Pfad zum Projekt im Katalog ein.  
  
 Wenn Sie den Assistenten in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] starten, dann wählt der Assistent standardmäßig das geöffnete Projekt als Quelle aus und überspringt diesen Schritt. Um zu diesem Schritt zurückzukehren und eine andere Quelle auszuwählen, klicken Sie auf **zurück** oder klicken Sie auf **Quelle auswählen** im linken Bereich.  
  
## <a name="select-destination"></a>Ziel auswählen  
 Um den Zielordner für das Projekt im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Katalog auszuwählen, geben Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz ein, oder klicken Sie auf **Durchsuchen** , um aus einer Liste von Servern auszuwählen. Geben Sie den Projektpfad in SSISDB ein, oder klicken Sie auf **Durchsuchen** , um ihn auszuwählen.  
  
 Wenn Sie den Assistenten in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] starten, dann wählt der Assistent standardmäßig die verbundene Serverinstanz aus und gibt den Pfad für das ausgewählte Projekt ein. Sie können diese Werte ändern, um das Projekt an einem anderen Speicherort bereitzustellen.  
  
## <a name="review"></a>Lesen Sie  
 Mit dem Assistenten können Sie die von Ihnen ausgewählten Einstellungen überprüfen, bevor Sie das Projekt bereitstellen. Sie können Ihre Auswahl ändern, indem Sie auf **Zurück**klicken oder indem Sie auf einen der Schritte im linken Bereich klicken.  
  
## <a name="deployresults"></a>Bereitstellen/Ergebnisse  
 Beim Klicken auf **bereitstellen** aus der **Review** Seite das Projekt bereitgestellt wird und die **Ergebnisse** Seite zeigt den Erfolg oder Misserfolg der einzelnen Aktionen. Ist die Aktion fehlerhaft, klicken Sie auf **Fehler** in der Spalte **Ergebnis** , um eine Erklärung über den Fehler anzuzeigen. Klicken Sie auf **Bericht speichern...**  um die Ergebnisse als XML-Datei zu speichern.  
  
 Klicken Sie auf **Schließen**, um den Assistenten zu beenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Projekten auf dem Integration Services-Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md)   
 [Bereitstellung von Projekten und Paketen](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
