---
title: Starten von Microsoft SQL Server Management Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 94466dc6c069ced5b2743cbd8a14d98271303477
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53373632"
---
# <a name="start-sql-server-management-studio"></a>Starten von SQL Server Management Studio
  Zu Beginn dieses Lernprogramms geht es hauptsächlich um [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="opening-sql-server-management-studio"></a>Öffnen von SQL Server Management Studio  
  
#### <a name="to-open-sql-server-management-studio"></a>So öffnen Sie SQL Server Management Studio  
  
1.  Zeigen Sie im Menü **Start** auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], und klicken Sie dann auf **SQL Server Management Studio**.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ist nicht standardmäßig installiert. Wenn [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] nicht verfügbar ist, installieren Sie es, indem Sie Setup ausführen. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ist nicht verfügbar, mit [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express kann kostenlos von der [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=37075&clcid=0x409), weist jedoch eine andere Benutzeroberfläche als in diesem Tutorial beschrieben wird.  
  
2.  Überprüfen Sie im Dialogfeld **Verbindung mit dem Server herstellen** die Standardeinstellungen, und klicken Sie dann auf **Verbinden**. Damit die Verbindung hergestellt werden kann, muss das Feld **Servername** den Namen des Computers enthalten, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert ist. Wenn die [!INCLUDE[ssDE](../../includes/ssde-md.md)] eine benannte Instanz, die **Servernamen** Feld sollten auch den Instanznamen im Format enthalten \< *Computer_name* > \\ < *Instance_name*>.  
  
## <a name="management-studio-components"></a>Management Studio-Komponenten  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] stellt seine Informationen in Fenstern bereit, die für die jeweils spezielle Art von Informationen vorgesehen sind. Datenbankinformationen werden im Fenster Objekt-Explorer sowie im Fenster für Dokumente angezeigt.  
  
-   Der Objekt-Explorer enthält eine Strukturansicht aller Datenbankobjekte eines Servers. Diese kann die Datenbanken von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]umfassen. Der Objekt-Explorer umfasst Informationen zu allen Servern, mit denen eine Verbindung besteht. Wenn Sie [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]öffnen, werden Sie aufgefordert, den Objekt-Explorer mit den zuletzt verwendeten Einstellungen zu verbinden. Zum Herstellen einer Verbindung können Sie auf jeden beliebigen Server in der Komponente Registrierte Server doppelklicken. Sie brauchen keinen Server zu registrieren, um eine Verbindung herzustellen.  
  
-   Das Dokumentfenster ist der größte Bestandteil von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Es kann Abfrage-Editoren und Browserfenster umfassen. Standardmäßig wird die Seite Zusammenfassung angezeigt, die mit der Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] auf dem aktuellen Computer verbunden ist.  
  
## <a name="showing-additional-windows"></a>Anzeigen zusätzlicher Fenster  
  
#### <a name="to-show-the-registered-servers-window"></a>So zeigen Sie das Fenster "Registrierte Server" an  
  
1.  Klicken Sie im Menü **Ansicht** auf **Registrierte Server**.  
  
     Das Fenster Registrierte Server wird über dem Objekt-Explorer angezeigt. In der Liste "Registrierte Server" werden die Server aufgelistet, die Sie häufig verwalten. In dieser Liste können Sie Server hinzufügen und entfernen. Als einzige Server werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen auf dem Computer aufgelistet, auf dem [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]ausgeführt wird.  
  
2.  Wenn Ihr Server nicht, in der Liste der registrierten Server angezeigt wird mit der rechten Maustaste **Datenbank-Engine**, und klicken Sie dann auf **lokale Serverregistrierung aktualisieren**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Herstellen einer Verbindung mit registrierten Servern und dem Objekt-Explorer](../object/object-explorer.md)  
  
  
