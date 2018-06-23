---
title: Integration Services-Bereitstellungs-Assistenten | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 60bc9f05f7a00075efbda2972cf78d9d169c55d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047645"
---
# <a name="integration-services-deployment-wizard"></a>Bereitstellungs-Assistent für Integration Services
  Der Bereitstellungs-Assistent für [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt Projekte im SSISDB-Katalog auf einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz bereit, die das Projektbereitstellungsmodell verwendet.  
  
 Starten der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Bereitstellungs-Assistent aus einem geöffneten Projekt im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Option **bereitstellen** aus der **Projekt** Menü. So starten Sie den Assistenten in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], erweitern Sie die **Integration Services-Kataloge** > **SSISDB** Maustaste Knoten im Objekt-Explorer die **Projekte** Ordner, und klicken Sie dann auf **Projekt bereitstellen**.  
  
 Der Assistent führt Sie die folgenden vier Schritte aus. Klicken Sie auf **Weiter** mit dem nächsten Schritt verschieben oder **vorherige** zum vorherigen Schritt zurückgegeben.  
  
1.  **Wählen Sie die Quelle** – wählen Sie die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt, das Sie bereitstellen möchten.  
  
2.  **Wählen Sie Ziel** – wählen Sie das Projektziel.  
  
3.  **Überprüfen Sie** – zeigt Ihre Auswahl.  
  
4.  **Bereitstellen/Ergebnisse** – stellt das Projekt bereit und zeigt die Ergebnisse an.  
  
## <a name="select-source"></a>Quellen auswählen  
 Um eine projektbereitstellungsdatei bereitzustellen, die Sie erstellt haben, wählen Sie **projektbereitstellungsdatei** und geben Sie den Pfad zur ispac-Datei, oder klicken Sie auf **Durchsuchen** finden sie in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projektordner. Um ein Projekt bereitzustellen, das sich im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Katalog befindet, wählen Sie **Integration Services-Katalog**aus und geben dann den Servernamen und den Pfad zum Projekt im Katalog ein.  
  
 Wenn Sie den Assistenten in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] starten, dann wählt der Assistent standardmäßig das geöffnete Projekt als Quelle aus und überspringt diesen Schritt. Um zu diesem Schritt zurückzukehren, und eine andere Quelle auszuwählen, klicken Sie auf **vorherige** oder klicken Sie auf **Quelle auswählen** im linken Bereich.  
  
## <a name="select-destination"></a>Ziel auswählen  
 Um den Zielordner für das Projekt im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Katalog auszuwählen, geben Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz ein, oder klicken Sie auf **Durchsuchen** , um aus einer Liste von Servern auszuwählen. Geben Sie den Projektpfad in SSISDB ein, oder klicken Sie auf **Durchsuchen** , um ihn auszuwählen.  
  
 Wenn Sie den Assistenten in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] starten, dann wählt der Assistent standardmäßig die verbundene Serverinstanz aus und gibt den Pfad für das ausgewählte Projekt ein. Sie können diese Werte ändern, um das Projekt an einem anderen Speicherort bereitzustellen.  
  
## <a name="review"></a>Überprüfen Sie  
 Mit dem Assistenten können Sie die von Ihnen ausgewählten Einstellungen überprüfen, bevor Sie das Projekt bereitstellen. Sie können Ihre Auswahl ändern, indem Sie auf **Zurück**klicken oder indem Sie auf einen der Schritte im linken Bereich klicken.  
  
## <a name="deployresults"></a>Bereitstellen/Ergebnisse  
 Beim Klicken auf **bereitstellen** aus der **Überprüfung** ", das Projekt bereitgestellt wird und die **Ergebnisse** Seite zeigt den Erfolg oder Misserfolg der einzelnen Aktionen aufgeführt. Ist die Aktion fehlerhaft, klicken Sie auf **Fehler** in der Spalte **Ergebnis** , um eine Erklärung über den Fehler anzuzeigen. Klicken Sie auf **Bericht speichern...**  um die Ergebnisse als XML-Datei zu speichern.  
  
 Klicken Sie auf **Schließen**, um den Assistenten zu beenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Projekten mit Integration Services-Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md)   
 [Bereitstellung von Projekten und Paketen](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  