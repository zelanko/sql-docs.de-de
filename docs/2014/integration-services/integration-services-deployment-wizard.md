---
title: Bereitstellungs-Assistent für Integration Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 721953c31a44a2ea02f480c9830e6347adfd4eb3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058010"
---
# <a name="integration-services-deployment-wizard"></a>Bereitstellungs-Assistent für Integration Services
  Der Bereitstellungs-Assistent für [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt Projekte im SSISDB-Katalog auf einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz bereit, die das Projektbereitstellungsmodell verwendet.  
  
 Um den Bereitstellungs-Assistenten in einem geöffneten [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Projekt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]in zu starten **, wählen Sie** im Menü **Projekt** die Option bereitstellen aus. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]Um den Assistenten in zu starten, erweitern Sie den Knoten **Integration Services Kataloge** > **ssisdb** in Objekt-Explorer, klicken Sie mit der rechten Maustaste auf den Ordner **Projekte** , und klicken Sie dann auf **Projekt**bereitstellen.  
  
 Der Assistent führt Sie die folgenden vier Schritte aus. Klicken Sie auf **weiter** , um zum nächsten Schritt zu wechseln **, oder zurück, um zum** vorherigen Schritt zurückzukehren.  
  
1.  **Quelle auswählen** : Wählen Sie [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] das Projekt aus, das Sie bereitstellen möchten.  
  
2.  **Ziel auswählen** : Wählen Sie das Projektziel aus.  
  
3.  **Review** : zeigt Ihre Auswahl an.  
  
4.  Bereitstellen **/Ergebnisse** : stellt das Projekt bereit und zeigt die Ergebnisse an.  
  
## <a name="select-source"></a>Auswählen der Quelle  
 Um eine von Ihnen erstellte Projekt Bereitstellungs Datei bereitzustellen, wählen Sie **Projekt Bereitstellungs Datei** aus, und geben Sie den Pfad zur ispac-Datei ein, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oder klicken Sie auf **Durchsuchen** , um Sie im Projektordner zu suchen Um ein Projekt bereitzustellen, das sich im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Katalog befindet, wählen Sie **Integration Services-Katalog**aus und geben dann den Servernamen und den Pfad zum Projekt im Katalog ein.  
  
 Wenn Sie den Assistenten in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] starten, dann wählt der Assistent standardmäßig das geöffnete Projekt als Quelle aus und überspringt diesen Schritt. Wenn Sie zu diesem Schritt zurückkehren und eine andere Quelle auswählen möchten, klicken Sie auf zurück **, oder klicken** Sie im linken Bereich auf **Quelle auswählen** .  
  
## <a name="select-destination"></a>Ziel auswählen  
 Um den Zielordner für das Projekt im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Katalog auszuwählen, geben Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz ein, oder klicken Sie auf **Durchsuchen** , um aus einer Liste von Servern auszuwählen. Geben Sie den Projektpfad in SSISDB ein, oder klicken Sie auf **Durchsuchen** , um ihn auszuwählen.  
  
 Wenn Sie den Assistenten in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] starten, dann wählt der Assistent standardmäßig die verbundene Serverinstanz aus und gibt den Pfad für das ausgewählte Projekt ein. Sie können diese Werte ändern, um das Projekt an einem anderen Speicherort bereitzustellen.  
  
## <a name="review"></a>Überprüfung  
 Mit dem Assistenten können Sie die von Ihnen ausgewählten Einstellungen überprüfen, bevor Sie das Projekt bereitstellen. Sie können Ihre Auswahl ändern, indem Sie auf **Zurück**klicken oder indem Sie auf einen der Schritte im linken Bereich klicken.  
  
## <a name="deployresults"></a>Bereitstellen/Ergebnisse  
 Wenn Sie auf der Seite **überprüfen** auf Bereitstellen klicken, wird das Projekt bereitgestellt, **und auf der** Seite **Ergebnisse** wird der Erfolg oder Misserfolg der einzelnen Aktionen angezeigt. Ist die Aktion fehlerhaft, klicken Sie auf **Fehler** in der Spalte **Ergebnis** , um eine Erklärung über den Fehler anzuzeigen. Klicken Sie auf **Bericht speichern...** , um die Ergebnisse in einer XML-Datei zu speichern.  
  
 Klicken Sie auf **Schließen**, um den Assistenten zu beenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereitstellen von Projekten auf Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md)   
 [Bereitstellung von Projekten und Paketen](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
