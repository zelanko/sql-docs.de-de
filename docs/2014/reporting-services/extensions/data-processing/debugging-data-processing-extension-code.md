---
title: Debuggen von Code für Datenverarbeitungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: adecc79256f49aeca9532e50119675515b9939dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63164365"
---
# <a name="debugging-data-processing-extension-code"></a>Debuggen von Code für Datenverarbeitungserweiterungen
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Bietet mehrere Debugtools, mit denen Sie den Code für die Datenverarbeitungs Erweiterung analysieren und Fehler darin finden [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] können. Welches Tool dafür am besten geeignet ist, hängt von Ihrer Zielsetzung ab. In diesem Beispiel wird [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] verwendet.  
  
#### <a name="to-debug-your-data-processing-extension-code"></a>So debuggen Sie Code für Datenverarbeitungserweiterungen  
  
1.  Starten Sie [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)], und öffnen Sie das Projekt für die Datenverarbeitungserweiterung.  
  
2.  Erstellen Sie das Projekt, und stellen Sie die Assembly der Datenverarbeitungserweiterung und die dazugehörige PDB-Datei im Berichts-Designer bereit. Weitere Informationen zur Bereitstellung finden Sie unter [Vorgehensweise: Bereitstellen einer Datenverarbeitungserweiterung für den Berichts-Designer](deploying-a-data-processing-extension-to-report-designer.md).  
  
3.  Öffnen Sie ein neues Berichtsprojekt in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], ohne vorher den Code für die Datenverarbeitungserweiterungen in einem anderen Fenster von [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zu schließen.  
  
4.  Wechseln Sie zu dem [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]-Fenster, das das Projekt für die Datenverarbeitungserweiterung enthält, und legen Sie einige Breakpoints im Code fest.  
  
5.  Klicken Sie im Menü **Debuggen** auf **An den Prozess anhängen**, während das Fenster des Projekts für die Datenverarbeitungserweiterung noch aktiv ist.  
  
     Das Dialogfeld **An den Prozess anhängen** wird geöffnet.  
  
6.  Wählen Sie aus der Liste der Prozesse den Prozess „devenv.exe“ aus, der dem Berichtsprojekt entspricht, und klicken Sie auf **Anfügen**.  
  
7.  Definieren Sie mithilfe der Registerkarte **Berichtsdaten** des Berichtsprojekts die Berichtsdatenquelle. Sie verwenden wahrscheinlich den generischen Abfrage-Designer, um eine Abfrage für die benutzerdefinierte Datenquelle auszuführen. Dadurch sollte der Debugger aufgerufen und Code den Breakpoints gemäß ausgeführt werden.  
  
8.  Gehen Sie den Code schrittweise mit der F11-Taste durch. Weitere Informationen zum Debuggen mit [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] finden Sie in der Dokumentation zu [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereitstellen von Datenverarbeitungserweiterungen](deploying-a-data-processing-extension.md)   
 [Erweiterungen für Reporting Services](../reporting-services-extensions.md)   
 [Implementieren von Datenverarbeitungserweiterungen](implementing-a-data-processing-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
