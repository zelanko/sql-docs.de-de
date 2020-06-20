---
title: Aktivieren verschlüsselter Verbindungen mit dem Datenbank-Engine (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e6e45b1f49c348e6cce329fb918479e92edbe9ae
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935337"
---
# <a name="enable-encrypted-connections-to-the-database-engine-sql-server-configuration-manager"></a>Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie verschlüsselte Verbindungen für eine Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] durch Angeben eines Zertifikats für die [!INCLUDE[ssDE](../../includes/ssde-md.md)] mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers aktivieren können. Für den Servercomputer muss ein Zertifikat bereitgestellt worden sein, und der Clientcomputer muss so eingerichtet sein, dass er die Stammzertifizierungsstelle des Zertifikats als vertrauenswürdig einstuft. Zertifikate werden bereitgestellt, indem sie mithilfe eines Importvorgangs in Windows installiert werden.  
  
 Das Zertifikat muss für die **Serverauthentifizierung**ausgegeben sein. Der Name des Zertifikats muss der vollqualifizierte Domänenname (FQDN) des Computers sein.  
  
 Zertifikate werden lokal für diesen Benutzer auf dem Computer gespeichert. Um ein Zertifikat zur Verwendung durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu installieren, müssen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager unter dem gleichen Benutzerkonto ausführen wie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst. Nur wenn der Dienst als LocalSystem, NetworkService oder LocalService ausgeführt wird, kann ein administratives Konto verwendet werden.  
  
 Der Client muss in der Lage sein, den Besitzer des vom Server verwendeten Zertifikats zu überprüfen. Wenn der Client über das Zertifikat für öffentliche Schlüssel der Zertifizierungsstelle verfügt, die das Serverzertifikat signiert hat, sind keine weiteren Konfigurationsschritte erforderlich. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows enthält die Zertifikate für öffentliche Schlüssel von vielen Zertifizierungsstellen. Wenn das Serverzertifikat von einer öffentlichen oder privaten Zertifizierungsstelle signiert wurde, für die der Client kein öffentliches Schlüsselzertifikat besitzt, müssen Sie das Zertifikat für öffentliche Schlüssel der Zertifizierungsstelle installieren, die das Serverzertifikat signiert hat.  
  
> [!NOTE]  
>  Wenn Sie die Verschlüsselung bei einem Failovercluster verwenden möchten, müssen Sie das Serverzertifikat mit dem vollqualifizierten DNS-Namen des virtuellen Servers auf allen Knoten im Failovercluster installieren. Wenn Sie z. b. über einen Cluster mit zwei Knoten verfügen, der Knoten mit dem Namen *\<your company>* test1. com und test2. *\<your company>* . com, und Sie verfügen über einen virtuellen Server mit dem Namen virorql. Sie müssen ein Zertifikat für virationql *\<your company>* installieren. com auf beiden Knoten. Sie können den Wert der Option **ForceEncryption**auf **Yes**.  
  
 **In diesem Thema**  
  
-   **So aktivieren Sie verschlüsselte Verbindungen**  
  
     [Bereitstellen (Installieren) eines Zertifikats auf dem Server](#Provision)  
  
     [Exportieren des Serverzertifikats](#Export)  
  
     [Konfigurieren des Servers zum Annehmen verschlüsselter Verbindungen](#ConfigureServerConnections)  
  
     [Konfigurieren des Clients zum Anfordern verschlüsselter Verbindungen](#ConfigureClientConnections)  
  
     [Verschlüsseln einer Verbindung in SQL Server Management Studio](#EncryptConnection)  
  
##  <a name="SSMSProcedure"></a>  
  
###  <a name="to-provision-install-a-certificate-on-the-server"></a><a name="Provision"></a> So stellen Sie ein Zertifikat auf dem Server bereit bzw. installieren Sie ein Zertifikat  
  
1.  Klicken Sie im **Startmenü** auf **Ausführen**, geben Sie im Feld **Öffnen** ein, `MMC` und klicken Sie dann auf **OK**.  
  
2.  Klicken Sie in der MMC-Konsole im Menü **Datei** auf **Snap-In hinzufügen/entfernen**.  
  
3.  Klicken Sie im Dialogfeld **Snap-In hinzufügen/entfernen** auf **Hinzufügen**.  
  
4.  Klicken Sie im Dialogfeld **Eigenständiges Snap-In hinzufügen** auf **Zertifikate**, und klicken Sie dann auf **Hinzufügen**.  
  
5.  Klicken Sie im **Dialogfeld Zertifikate-Snap-In** auf **Computerkonto**, und klicken Sie dann auf **Fertig stellen**.  
  
6.  Klicken Sie im Dialogfeld **Eigenständiges Snap-In hinzufügen** auf **Schließen**.  
  
7.  Klicken Sie im Dialogfeld **Snap-In hinzufügen/entfernen** auf **OK**.  
  
8.  Erweitern Sie im Dialogfeld **Zertifikate-Snap-In** die Option **Zertifikate**, erweitern Sie **Eigene Zertifikate**, und klicken Sie dann mit der rechten Maustaste auf **Zertifikate**, zeigen Sie auf **Alle Aufgaben**, und klicken Sie anschließend auf **Importieren**.  
  
9. Ergänzen Sie die Angaben im **Zertifikatimport-Assistenten**, um dem Computer ein Zertifikat hinzuzufügen, und schließen Sie dann die MMC-Konsole. Weitere Informationen zum Hinzufügen von Zertifikaten zu einem Computer finden Sie in der Windows-Dokumentation.  
  
###  <a name="to-export-the-server-certificate"></a><a name="Export"></a> So exportieren Sie das Serverzertifikat  
  
1.  Erweitern Sie im **Zertifikate** -Snap-In den Ordner **Zertifikate** / **Eigene Zertifikate** , klicken Sie mit der rechten Maustaste auf das **Zertifikat**, zeigen Sie auf **Alle Tasks**, und klicken Sie dann auf **Exportieren**.  
  
2.  Führen Sie den **Zertifikatexport-Assistenten**aus, und speichern Sie die Zertifikatsdatei in einem geeigneten Speicherort.  
  
###  <a name="to-configure-the-server-to-accept-encrypted-connections"></a><a name="ConfigureServerConnections"></a> So konfigurieren Sie den Server zum Annehmen verschlüsselter Verbindungen  
  
1.  Erweitern **SQL Server Configuration Manager**Sie in SQL Server-Konfigurations-Manager **SQL Server Netzwerkkonfiguration**, klicken Sie mit der rechten Maustaste auf **Protokolle für** _\<server instance>_ , und wählen Sie dann**Eigenschaften**aus.  
  
2.  Wählen Sie im Dialogfeld **Protokolle für** _\<instance name>_ **Eigenschaften** auf der Registerkarte **Zertifikat** das gewünschte Zertifikat aus der Dropdown-Leiste für das Feld **Zertifikat** aus, und klicken Sie dann auf **OK**.  
  
3.  Aktivieren Sie auf der Registerkarte **Flags** im Feld **ForceEncryption** die Option **Ja**, und klicken Sie dann auf **OK** , um das Dialogfeld zu schließen.  
  
4.  Starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst neu.  
  
###  <a name="to-configure-the-client-to-request-encrypted-connections"></a><a name="ConfigureClientConnections"></a> So konfigurieren Sie den Client zum Anfordern verschlüsselter Verbindungen  
  
1.  Kopieren Sie entweder das Originalzertifikat oder die exportierte Zertifikatsdatei auf den Clientcomputer.  
  
2.  Installieren Sie auf dem Clientcomputer mithilfe des **Zertifikate** -Snap-Ins entweder das Stammzertifikat oder die exportierte Zertifikatsdatei.  
  
3.  Klicken Sie im Konsolenbereich mit der rechten Maustaste auf **SQL Server Native Client-Konfiguration**, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Klicken Sie auf der Seite **Flags** im Feld **Protokollverschlüsselung erzwingen** auf **Ja**.  
  
###  <a name="to-encrypt-a-connection-from-sql-server-management-studio"></a><a name="EncryptConnection"></a> So verschlüsseln Sie eine Verbindung in SQL Server Management Studio  
  
1.  Klicken Sie auf der Symbolleiste des Objekt-Explorers auf **Verbinden**, und klicken Sie dann auf **Datenbank-Engine**.  
  
2.  Vervollständigen Sie im Dialogfeld **Verbindung mit Server herstellen** die Verbindungseinstellungen, und klicken Sie dann auf **Optionen**.  
  
3.  Klicken Sie auf der Registerkarte **Verbindungseigenschaften** auf **Verbindung verschlüsseln**.  
  
  
