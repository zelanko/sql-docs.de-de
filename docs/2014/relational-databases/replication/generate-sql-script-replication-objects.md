---
title: SQL-Skript generieren (Replikationsobjekte) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.generatesqlscript.f1
helpviewer_keywords:
- Generate SQL Script dialog box
ms.assetid: b7ccc34e-1c22-44b8-8eb5-f6423af3164e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2585452ee31c911ea6e288effc3e5e91fff88a64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721270"
---
# <a name="generate-sql-script-replication-objects"></a>SQL-Skript generieren (Replikationsobjekte)
  Ein Replikationsskript enthält die gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Systemprozeduren, die zur Implementierung der Replikationskomponenten, für die Skripts erstellt wurden, erforderlich sind. Dazu gehören eine Veröffentlichung oder ein Abonnement. Für die Replikationskomponenten in einer Topologie sollten im Rahmen des Plans zur Wiederherstellung im Notfall Skripts erstellt werden; diese können dann auch zur Automatisierung sich wiederholender Tasks verwendet werden. Die Replikation stellt zum Erstellen von Skripts für Replikationsobjekte zwei Dialogfelder bereit:  
  
-   **Generieren**Sie ein SQL-Skript, das über das Kontextmenü des **Replikations** Ordners und aller [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Unterordner in verfügbar ist. In diesem Dialogfeld können Sie Skripts für alle Replikations Objekte [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]einer Instanz von erstellen.  
  
-   **Generieren Sie das \<SQL-Skript ObjectName>**, das über das Kontextmenü für Veröffentlichungen und Abonnements verfügbar ist. Mithilfe dieses Dialogfelds können Sie Skripts für einzelne Objekte erstellen.  
  
 In diesen Dialogfeldern werden Skripts für Objekte einer einzelnen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erstellt; es werden keine Verbindungen mit anderen Instanzen hergestellt, um Skripts für verknüpfte Objekte zu erstellen.  
  
## <a name="generate-sql-script-options"></a>SQL-Skript generieren (Optionen)  
 **Verteilereigenschaften**  
 Wählen Sie diese Option aus, um Skripts für gespeicherte Prozeduren zu erstellen, um: den Verteiler aktivieren oder deaktivieren, mit dem Verteiler verknüpfte Verleger hinzufügen oder löschen sowie die Verteilungsdatenbank erstellen oder löschen zu können.  
  
 **Veröffentlichungen in den folgenden Datenquellen**  
 Wählen Sie diese Option aus, um Skripts für gespeicherte Prozeduren zu erstellen, um: die Veröffentlichung aktivieren oder deaktivieren sowie Veröffentlichungen, Artikel, Pushabonnements und Replikationsaufträge erstellen oder löschen zu können.  
  
 **Abonnements in den folgenden Datenquellen**  
 Durch Auswählen dieser Option können Sie Skripts für gespeicherte Prozeduren erstellen, um Pullabonnements und Replikationsaufträge zu erstellen oder zu löschen.  
  
 So **erstellen oder aktivieren Sie die Komponenten** und **Löschen bzw. deaktivieren Sie die Komponenten**  
 Geben Sie an, ob das Skript Befehle zum Erstellen oder Löschen eines Replikationsobjekts enthalten soll. 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, das Dialogfeld zu verwenden, um eine Reihe von Skripts zum Aktivieren und Deaktivieren von Komponenten zu erstellen.  
  
 **Replikations Aufträge**  
 Wählen Sie diese Option aus, um neben Skripts für Aufrufe gespeicherter Prozeduren auch Skripts für Replikationsaufträge zu erstellen. Diese Option ist nur verfügbar, wenn Skripts von einem Verteiler aus erstellt werden.  
  
 Bei der Ausführung gespeicherter Replikationsprozeduren werden die erforderlichen Aufträge erstellt, d. h., die Option muss nicht ausgewählt werden. Einen Datensatz mit den erstellten Aufträgen zur Verfügung zu haben, kann sich jedoch als nützlich erweisen, falls ein einzelner Auftrag erneut erstellt werden muss.  
  
## <a name="generate-sql-script-objectname-options"></a>Optionen von SQL-Skript \<ObjectName> generieren  
 So **erstellen oder aktivieren Sie die Komponenten** und **Löschen bzw. deaktivieren Sie die Komponenten**  
 Geben Sie an, ob das Skript Befehle zum Erstellen oder Löschen eines Replikationsobjekts enthalten soll. 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, das Dialogfeld zu verwenden, um eine Reihe von Skripts zum Aktivieren und Deaktivieren von Komponenten zu erstellen.  
  
 **Replikations Aufträge**  
 Auf diese Option kann im Dialogfeld **SQL-Skript generieren** zugegriffen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Skripts für die Replikation](scripting-replication.md)  
  
  
