---
title: Verbinden mit SQL Server-Datenbank-Engine (Eigenschaftenseite Verbindung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttosqlserver.connectionproperties.f1
ms.assetid: edc1143c-6a47-4b02-92ab-441bdea8ea8a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 30382bcb0c70fb985c88866602cb997988b88569
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "70153753"
---
# <a name="connect-to-server-connection-properties-page-database-engine"></a>Verbinden mit SQL Server-Datenbank-Engine (Eigenschaftenseite Verbindung)
  Auf dieser Registerkarte können Optionen für Verbindungen mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] angezeigt oder angegeben werden, oder Sie können mit dieser Registerkarte [!INCLUDE[ssDE](../../includes/ssde-md.md)] in **Registrierte Server**registrieren. **Connect** und **Optionen** werden nur in diesem Dialogfeld angezeigt, wenn eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]Instanz von hergestellt wird. Beim Registrieren **** [!INCLUDE[ssDE](../../includes/ssde-md.md)]wird nur **Test** und speichern in diesem Dialogfeld angezeigt.  
  
## <a name="options"></a>Tastatur  
 **Herstellen einer Verbindung mit der Datenbank**  
 Wählen Sie eine Datenbank aus der Liste aus, zu der eine Verbindung hergestellt werden soll. Wenn Sie ** \<Standard>** auswählen, wird eine Verbindung mit der Standarddatenbank für den Server hergestellt. Wenn Sie die Option ** \<durchsuchen Server>** auswählen, können Sie den Server nach der Datenbank durchsuchen, mit der eine Verbindung hergestellt werden soll.  
  
 Beim Herstellen einer Verbindung mit einer Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des Datenbank-Engine [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]über müssen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwenden und im Dialogfeld Verbindung **mit Server herstellen** auf der Registerkarte **Verbindungs Eigenschaften** eine Datenbank angeben. Stellen Sie sicher, dass Sie das Kontrollkästchen **Verbindung verschlüsseln** aktivieren.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt standardmäßig eine Verbindung mit der **master**-Datenbank her. Wenn Sie eine Benutzerdatenbank angeben, wird im Objekt-Explorer nur diese Datenbank mit den zugehörigen Objekten angezeigt. Wenn Sie eine Verbindung mit der **master**-Datenbank herstellen, werden alle Datenbanken angezeigt. Weitere Informationen finden Sie in der [Übersicht über die Azure SQL-Datenbank](/azure/sql-database/sql-database-technical-overview).  
  
 **Netzwerkprotokoll**  
 Wählen Sie ein Protokoll aus der Liste aus. Die verfügbaren Clientprotokolle sind diejenigen, die Sie mithilfe der Netzwerkkonfiguration des Clients in der Computerverwaltung konfiguriert haben.  
  
 **Netzwerk Paketgröße**  
 Geben Sie die Größe der zu sendenden Netzwerkpakete ein. Der Standardwert ist 4096 (Bytes).  
  
 **Verbindungs Timeout**  
 Geben Sie die Anzahl der Sekunden ein, die auf das Herstellen einer Verbindung gewartet werden soll, bevor ein Timeout eintritt. Der Standardwert ist 15 Sekunden.  
  
 **Ausführungs Timeout**  
 Geben Sie an, wie lange (in Sekunden) auf den Abschluss eines Tasks auf dem Server gewartet werden soll. Der Standardwert beträgt null Sekunden, d. h. es wird kein Timeout verwendet.  
  
 **Verschlüsseln der Verbindung**  
 Erzwingt die Verschlüsselung der Verbindung.  
  
 **Benutzerdefinierte Farbe verwenden**  
 Wählen Sie diese Option aus, um die Hintergrundfarbe für die Statusleiste in einem [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor-Fenster anzugeben. Um die Farbe anzugeben, klicken Sie auf **Auswählen**. Wählen Sie im Dialogfeld **Farbe** eine vordefinierte Farben aus der Tabelle **Grundfarben** aus, oder klicken Sie auf **Benutzerdefinierte Farben** , um eine benutzerdefinierte Farbe zu definieren und zu verwenden.  
  
-   Wenn Sie eine Farbe für einen Servereintrag im Bereich **Objekt-Explorer** angeben, wird diese Farbe verwendet, wenn Sie ein Abfrage-Editor-Fenster öffnen. Um ein Abfrage-Editor-Fenster zu öffnen, klicken Sie entweder mit der rechten Maustaste auf den Servereintrag, und wählen Sie **Neue Abfrage**, oder – wenn der Bereich **Objekt-Explorer** aktiv und auf diesen Server fokussiert ist – klicken Sie auf der Symbolleiste auf **Neue Abfrage** .  
  
-   Wenn Sie eine Farbe für einen Servereintrag im Bereich **Registrierte Server** angeben, wird diese Farbe verwendet, wenn Sie ein Abfrage-Editor-Fenster öffnen. Um ein Abfrage-Editor-Fenster zu öffnen, klicken Sie entweder mit der rechten Maustaste auf den Servereintrag, und wählen Sie **Neue Abfrage**, oder – wenn der Bereich **Registrierte Server** aktiv und auf diesen Server fokussiert ist – klicken Sie auf der Symbolleiste auf **Neue Abfrage** .  
  
-   Wenn Sie im Menü **Datei** auf **Neu** und dann auf **Datenbank-Engine-Abfrage** klicken, wird die Farbe, die Sie im Dialogfeld **Verbindung mit Server herstellen** angeben, für dieses Abfrage-Editor-Fenster übernommen.  
  
 **Alle zurücksetzen**  
 Ersetzt alle manuell eingegebenen Verbindungseigenschaftswerte durch die Standardwerte.  
  
 **Herstellen einer Verbindung**  
 Versucht, mithilfe der aufgelisteten Werte eine Verbindung herzustellen.  
  
 **Optionen**  
 Klicken Sie hier, um die Anzeige des Dialogfelds zu ändern und die zusätzlichen Serververbindungsoptionen, z. B. Speichern des Kennworts, auszublenden.  
  
 **Test**  
 Klicken Sie hier, um beim Registrieren von [!INCLUDE[ssDE](../../includes/ssde-md.md)] in **Registrierte Server**die Verbindung zu testen.  
  
 **Sicher**  
 Speichert die Einstellungen in **Registrierte Server**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verbindungseigenschaften (Dialogfeld)](../../database-engine/connection-properties-dialog-box.md)  
  
  
