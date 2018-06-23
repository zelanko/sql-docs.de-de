---
title: Projekt-Assistent zum Importieren von | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.importprojectwizard.f1
ms.assetid: 9247ad6c-4bd1-43ab-b347-583181cb9917
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c4e18295d08797e4fa6b475d32ea2d688e187d91
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163364"
---
# <a name="import-project-wizard"></a>Assistent zum Importieren von Projekten
  Verwenden Sie den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Assistenten zum Importieren von Projekten, um ein neues Integration Services-Projekt auf der Grundlage eines vorhandenen Projekts zu erstellen. Importieren Sie Projekte, die bereits im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Katalog bereitgestellt wurden, oder importieren Sie Projekte aus einer Projektbereitstellungsdatei (mit der Erweiterung „.ispac“).  
  
### <a name="to-create-a-project-based-on-a-project-in-ispac-file-or-in-catalog"></a>So erstellen Sie ein Projekt auf Grundlage eines Projekts in einer ISPAC-Datei oder im Katalog  
  
1.  Klicken Sie auf **Datei**, zeigen Sie auf **Neu**, und klicken Sie auf das Projekt.  
  
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
  
9. Klicken Sie auf **Schließen** , um den Assistenten zu schließen.  
  
  