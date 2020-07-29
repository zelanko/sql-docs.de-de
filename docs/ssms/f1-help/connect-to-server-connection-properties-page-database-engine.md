---
title: Verbinden mit SQL Server-Datenbank-Engine (Eigenschaftenseite Verbindung)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.connecttoce.connectionproperties.f1
- sql13.swb.connecttosqlserver.connectionproperties.f1
ms.assetid: edc1143c-6a47-4b02-92ab-441bdea8ea8a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 08/14/2017
ms.openlocfilehash: d1136d29ee8ee62648922f008042266a59632475
ms.sourcegitcommit: d855def79af642233cbc3c5909bc7dfe04c4aa23
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2020
ms.locfileid: "87123071"
---
# <a name="connect-to-server-connection-properties-page-database-engine"></a>Verbinden mit SQL Server-Datenbank-Engine (Eigenschaftenseite Verbindung)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Auf dieser Registerkarte können Optionen für Verbindungen mit einer [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]-Instanz angezeigt oder angegeben werden, oder Sie können [!INCLUDE[ssDE](../../includes/ssde_md.md)] unter **Registrierte Server** registrieren. Die Felder**Verbinden** und **Optionen** werden nur beim Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde_md.md)]in diesem Dialogfeld angezeigt. Die Felder**Testen** und **Speichern** werden nur beim Registrieren von [!INCLUDE[ssDE](../../includes/ssde_md.md)]in diesem Dialogfeld angezeigt.  
  
**Verbindung mit Datenbank herstellen**  
Wählen Sie eine Datenbank aus der Liste aus, zu der eine Verbindung hergestellt werden soll. Wenn Sie **<default>** auswählen, wird eine Verbindung zur Standarddatenbank des Servers hergestellt. Wenn Sie **<Browse server>** auswählen, können Sie den Server nach der Datenbank durchsuchen, mit der Sie eine Verbindung herstellen möchten.  
  
Wenn Sie über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Verbindung mit einer Instanz der [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]-Datenbank-Engine herstellen, müssen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwenden und im Dialogfeld **Verbindung mit Server herstellen** auf der Registerkarte **Verbindungseigenschaften** eine Datenbank angeben. Das Kontrollkästchen **Verbindung verschlüsseln** muss aktiviert sein.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt standardmäßig eine Verbindung mit der **master**-Datenbank her. Wenn Sie eine Benutzerdatenbank beim Verbinden mit [!INCLUDE[ssSDS](../../includes/sssds-md.md)] angeben, wird im Objekt-Explorer nur diese Datenbank mit den zugehörigen Objekten angezeigt. Wenn Sie eine Verbindung mit der **master**-Datenbank herstellen, werden alle Datenbanken angezeigt. Weitere Informationen finden Sie in der [Übersicht zu Microsoft Azure SQL-Datenbank](/azure/sql-database/sql-database-technical-overview).  
  
**Netzwerkprotokoll**  
Wählen Sie ein Protokoll aus der Liste aus. Die verfügbaren Clientprotokolle werden mithilfe der Netzwerkkonfiguration des Clients in der Computerverwaltung konfiguriert.  
  
**Netzwerkpaketgröße**  
Geben Sie die Größe der zu sendenden Netzwerkpakete ein. Der Standardwert ist 4096 (Bytes).  
  
**Verbindungstimeout**  
Geben Sie an, wie lange (in Sekunden) versucht werden soll, eine Verbindung herzustellen, bevor ein Timeout eintritt. Der Standardwert beträgt 15 Sekunden.  
  
**Ausführungstimeout**  
Geben Sie an, wie lange (in Sekunden) auf den Abschluss eines Tasks auf dem Server gewartet werden soll. Der Standardwert beträgt null Sekunden, d. h. es wird kein Timeout verwendet.  
  
**Verschlüsseln der Verbindung**  
Erzwingt die Verschlüsselung der Verbindung.  
  
**Benutzerdefinierte Farbe verwenden**  
Wählen Sie diese Option aus, um die Hintergrundfarbe für die Statusleiste in einem [!INCLUDE[ssDE](../../includes/ssde_md.md)] -Abfrage-Editor-Fenster anzugeben. Um die Farbe anzugeben, klicken Sie auf **Auswählen**. Wählen Sie im Dialogfeld **Farbe** eine vordefinierte Farben aus der Tabelle **Grundfarben** aus, oder klicken Sie auf **Benutzerdefinierte Farben** , um eine benutzerdefinierte Farbe zu definieren und zu verwenden.  
  
-   Wenn Sie eine Farbe für einen Servereintrag im Bereich **Objekt-Explorer** angeben, wird diese Farbe verwendet, wenn Sie ein Abfrage-Editor-Fenster öffnen. Um ein Abfrage-Editor-Fenster zu öffnen, klicken Sie entweder mit der rechten Maustaste auf den Servereintrag, und wählen Sie **Neue Abfrage**, oder – wenn der Bereich **Objekt-Explorer** aktiv und auf diesen Server fokussiert ist – klicken Sie auf der Symbolleiste auf **Neue Abfrage** .  
  
-   Wenn Sie eine Farbe für einen Servereintrag im Bereich **Registrierte Server** angeben, wird diese Farbe verwendet, wenn Sie ein Abfrage-Editor-Fenster öffnen. Um ein Abfrage-Editor-Fenster zu öffnen, klicken Sie entweder mit der rechten Maustaste auf den Servereintrag, und wählen Sie **Neue Abfrage**, oder – wenn der Bereich **Registrierte Server** aktiv und auf diesen Server fokussiert ist – klicken Sie auf der Symbolleiste auf **Neue Abfrage** .  
  
-   Wenn Sie im Menü **Datei** auf **Neu** und dann auf **Datenbank-Engine-Abfrage** klicken, wird die Farbe, die Sie im Dialogfeld **Verbindung mit Server herstellen** angeben, für dieses Abfrage-Editor-Fenster übernommen.  
  
**AD-Domänenname und Mandanten-ID**  
Wenn Sie eine Verbindung mit der **Active Directory – Universelle MFA** herstellen, geben Sie die authentifizierende Domäne an. Diese Option ist nur verfügbar, wenn Sie SSMS Version 17.2 oder höher verwenden. 

**Alles zurücksetzen**  
Ersetzt alle manuell eingegebenen Verbindungseigenschaftswerte durch die Standardwerte.  
  
**Herstellen einer Verbindung**  
Versucht, mithilfe der aufgelisteten Werte eine Verbindung herzustellen.  
  
**Optionen**  
Klicken Sie hier, um die Anzeige des Dialogfelds zu ändern und die zusätzlichen Serververbindungsoptionen, z. B. Speichern des Kennworts, auszublenden.  
  
**Test**  
Klicken Sie hier, um beim Registrieren von [!INCLUDE[ssDE](../../includes/ssde_md.md)] in **Registrierte Server**die Verbindung zu testen.  
  
**Speichern**  
Speichert die Einstellungen in **Registrierte Server**.  
  
## <a name="see-also"></a>Weitere Informationen  
[Verbindungseigenschaften (Dialogfeld)](../../ssms/f1-help/connection-properties-dialog-box.md)  
  
