---
title: Assistent zum Importieren von Projekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.importprojectwizard.f1
ms.assetid: 9247ad6c-4bd1-43ab-b347-583181cb9917
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8b9f20115010f2ad51159f29a4b64da195938969
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436647"
---
# <a name="import-project-wizard"></a>Assistent zum Importieren von Projekten
  Verwenden Sie den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Assistenten zum Importieren von Projekten, um ein neues Integration Services-Projekt auf der Grundlage eines vorhandenen Projekts zu erstellen. Importieren Sie Projekte, die bereits im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Katalog bereitgestellt wurden, oder importieren Sie Projekte aus einer Projektbereitstellungsdatei (mit der Erweiterung „.ispac“).  
  
### <a name="to-create-a-project-based-on-a-project-in-ispac-file-or-in-catalog"></a>So erstellen Sie ein Projekt auf Grundlage eines Projekts in einer ISPAC-Datei oder im Katalog  
  
1.  Klicken Sie auf **Datei**, zeigen Sie auf **neu**, und klicken Sie auf Projekt.  
  
2.  Erweitern Sie **Business Intelligence**, und klicken Sie auf **Integration Services**.  
  
3.  Wählen Sie im mittleren Bereich den **Integration Services-Assistent zum Importieren** aus, geben Sie einen **Namen** für die Projektmappe bzw. das Projekt ein, geben Sie den **Ordner** für das Projekt an, und klicken Sie dann auf **OK**.  
  
     Daraufhin sollte der **Integration Services-Assistent zum Importieren von Projekten**angezeigt werden. Dieser Assistent erstellt ein neues Integration Services-Projekt auf der Grundlage eines vorhandenen Projekts.  
  
4.  Klicken Sie auf der Seite **Einführung** auf **Weiter** , um die Seite **Quelle auswählen** anzuzeigen.  
  
5.  Geben Sie an, ob Sie das Projekt aus einer ISPAC-Datei oder einem Katalog importieren möchten.  
  
    -   Wenn Sie die Option **Projektbereitstellungsdatei** aktivieren, geben Sie den Pfad zur ISPAC-Datei an.  
  
    -   Wenn Sie die Option **Integration Services-Katalog** aktivieren, geben Sie den Namen der Datenbankserverinstanz an, auf der der Katalog vorhanden ist, und den Pfad zum Projekt im Katalog.  
  
6.  Klicken Sie auf der Seite **Quelle auswählen** auf **Weiter** , um die Seite **Überprüfen** anzuzeigen. Überprüfen Sie die auf der Seite angezeigten Informationen zum Importvorgang, die der Assistent ausführen wird.  
  
7.  Klicken Sie auf **Importieren** , um ein neues Integration Services-Projekt auf Grundlage des Projekts, das Sie ausgewählt haben, zu erstellen.  
  
8.  Die Seite **Ergebnisse** sollte die Ergebnisse des Importvorgangs anzeigen, den der Assistent ausgeführt hat. Klicken Sie auf **Bericht speichern** , um den Bericht in einer XML-Datei zu speichern.  
  
9. Klicken Sie auf **Schließen**, um den Assistenten zu schließen.  
  
  
