---
title: Fortschritt des Upgrade Advisors | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], analysis progress status
- analyzing system [Upgrade Advisor], progress information
- SQL Server Upgrade Advisor, analysis progress status
- monitoring analysis progress
- progress information [Upgrade Advisor]
- status information [Upgrade Advisor]
ms.assetid: a9e3d1c8-d492-4beb-93c7-f1bc40d4a910
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 697f70d4435213a991e55adecb51a98120d8df1b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66091563"
---
# <a name="upgrade-advisor-progress"></a>Upgrade Advisor-Status
  Die Analyse des Upgrade Advisor wird mit einem dedizierten Analyseprogramm gestartet, das eine Analyse jeder von Ihnen ausgewählten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponente durchführt. Wenn Komponenten analysiert werden, **wird der Fortschritt im** Dialogfeld "Status" angezeigt.  
  
## <a name="options"></a>Optionen  
 **Aktion**  
 Gibt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponente an, die für die Analyse ausgewählt wird.  
  
 **Status**  
 Zeigt den von der Statusschnittstelle der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponente zurückgegebenen Statuswert an.  
  
 **Meldung**  
 Zeigt Meldungen zu Fehlern und über den Erfolg bzw. das Fehlschlagen von Vorgängen. Die Meldungen werden vom jeweiligen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Analyzer zurückgegeben.  
  
> [!NOTE]  
>  Wenn die Analyse zu lange dauert, können Sie sie anhalten, den Analyse-Assistenten von Upgrade Advisor beenden und den Assistenten dann erneut ausführen. Um die Analysezeit zu reduzieren, wählen Sie weniger Komponenten zum Scannen aus.  
  
 Wenn die Analyse abgeschlossen wurde, wird der Bericht in eine Datei geschrieben. Sie können den Bericht anzeigen, indem Sie auf **Bericht starten** klicken, um den Berichts-Viewer auf dieser Seite zu starten. Wenn Sie den Bericht zu einem späteren Zeitpunkt anzeigen möchten, können Sie den **Berichts-Viewer des Upgrade Advisors** auf der Startseite des Upgrade Advisors öffnen.  
  
> [!NOTE]  
>  Vorherige Berichte werden jedes Mal gespeichert, wenn Sie einen Server analysieren. Die Berichte werden mit dem Zeitstempel für den Dateinamen gespeichert. Der Berichts-Viewer zeigt die letzten fünf gespeicherten Berichte an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Starten des Upgrade Advisors](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [Vorgehensweise: Ausführen des Analyse-Assistenten des Upgrade Advisors](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [SQL Server Komponenten](../../../2014/sql-server/install/sql-server-components.md)   
 [Referenz zur Benutzeroberfläche des Upgrade Advisors](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
