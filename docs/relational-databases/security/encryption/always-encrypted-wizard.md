---
title: Konfigurieren der Spaltenverschlüsselung mit dem Always Encrypted-Assistenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/30/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql13.swb.alwaysencryptedwizard.encryption.f1
- sql13.swb.alwaysencryptedwizard.f1
- sql13.swb.alwaysencryptedwizard.masterkey.f1
helpviewer_keywords:
- Wizard, Always Encrypted
ms.assetid: 68daddc9-ce48-49aa-917f-6dec86ad5af5
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 71df93e5e7d628fadf5839e980f42a92138a5e0c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "73594503"
---
# <a name="configure-column-encryption-using-always-encrypted-wizard"></a>Konfigurieren der Spaltenverschlüsselung mit dem Always Encrypted-Assistenten
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Der Always Encrypted-Assistent ist ein leistungsstarkes Tool, mit dem Sie die gewünschte [Always Encrypted](always-encrypted-database-engine.md)-Konfiguration für ausgewählte Datenbankspalten festlegen können. Der Assistent kann Spalten je nach aktueller Konfiguration und gewünschter Zielkonfiguration verschlüsseln, entschlüsseln (die Verschlüsselung entfernen) oder erneut verschlüsseln (z. B. mithilfe eines neuen Spaltenverschlüsselungsschlüssels oder eines anderen Verschlüsselungstyps als dem aktuellen, der für die Spalte konfiguriert ist). Während einer einzigen Ausführung des Assistenten können mehrere Spalten konfiguriert werden.

Mit dem Assistenten können Sie Spalten mit vorhandenen Spaltenverschlüsselungsschlüsseln verschlüsseln, einen neuen Spaltenverschlüsselungsschlüssel generieren oder zusätzlich zu diesem auch einen neuen Spaltenhauptschlüssel generieren. 

Dabei verschiebt der Assistent Daten aus der Datenbank und führt kryptografische Vorgänge innerhalb des SSMS-Prozesses aus. Der Assistent erstellt eine oder mehrere neue Tabellen mit der gewünschten Verschlüsselungskonfiguration in der Datenbank, lädt alle Daten aus den ursprünglichen Tabellen, führt die angeforderten kryptografischen Vorgänge aus, lädt die Daten in die neuen Tabellen hoch und vertauscht dann die ursprünglichen mit den neuen Tabellen.

> [!NOTE]
> Das Ausführen kryptografischer Vorgänge kann einige Zeit in Anspruch nehmen. Während dieser Zeit steht die Datenbank nicht zum Schreiben von Transaktionen zur Verfügung. PowerShell wird als Tool für kryptografische Vorgänge in größeren Tabellen empfohlen. Informationen hierzu finden Sie unter [Konfigurieren der Spaltenverschlüsselung mithilfe von Always Encrypted mit PowerShell](configure-column-encryption-using-powershell.md).

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

> [!NOTE]
> Wenn Sie [!INCLUDE [sssqlv15-md](../../../includes/sssqlv15-md.md)] verwenden und Ihre SQL Server-Instanz mit Secure Enclave konfiguriert ist, können Sie kryptografische Vorgänge direkt ausführen, ohne Daten aus der Datenbank zu verschieben. Informationen hierzu finden Sie unter [Konfigurieren einer direkten Spaltenverschlüsselung mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-configure-encryption.md). Beachten Sie, dass der Assistent keine direkte Verschlüsselung unterstützt.

::: moniker-end

Die Verwendung von PowerShell wird für die folgenden Szenarios empfohlen: 

 - Eine End-to-End-Vorgehensweise, die das Konfigurieren von Always Encrypted mit dem Assistenten sowie die Verwendung von Always Encrypted in einer Clientanwendung veranschaulicht, finden Sie in den folgenden Tutorials zu Azure SQL-Datenbank:
    - [Schützen von sensiblen Daten in Azure SQL-Datenbank mit Always Encrypted und Spaltenhauptschlüsseln im Windows-Zertifikatspeicher](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted/)
    - [Schützen von sensiblen Daten in Azure SQL-Datenbank mit Always Encrypted und Spaltenhauptschlüsseln in Azure Key Vault](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault)

 - Ein Video, das die Verwendung des Assistenten erläutert, finden Sie unter [Keeping Sensitive Data Secure with Always Encrypted](https://channel9.msdn.com/events/DataDriven/SQLServer2016/AlwaysEncrypted)(Sensible Daten mit Always Encrypted schützen). Weitere Informationen finden Sie auch im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Security-Teamblog [SSMS Encryption Wizard - Enabling Always Encrypted in a Few Easy Steps](https://techcommunity.microsoft.com/t5/SQL-Server/SSMS-Encryption-Wizard-Enabling-Always-Encrypted-in-a-Few-Easy/ba-p/384545).  
 - Informationen zu Always Encrypted-Schlüsseln finden Sie unter [Übersicht über die Schlüsselverwaltung für Always Encrypted](overview-of-key-management-for-always-encrypted.md).
 - Informationen zu Verschlüsselungstypen, die in Always Encrypted unterstützt werden, finden Sie unter [Auswählen der deterministischen oder zufälligen Verschlüsselung](always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).
 
 ## <a name="permissions"></a>Berechtigungen
Zum Ausführen von kryptografischen Vorgängen mithilfe des Assistenten müssen Sie über die Berechtigungen **VIEW ANY COLUMN MASTER KEY DEFINITION** und **VIEW ANY COLUMN ENCRYPTION KEY DEFINITION** verfügen. Zudem müssen Sie über Zugriffsberechtigungen für die von Ihnen verwendeten Spaltenhauptschlüssel in den Schlüsselspeichern verfügen, die die Schlüssel enthalten:
- **Zertifikatspeicher – Lokaler Computer**: Sie benötigen einen Lesezugriff auf das Zertifikat, das als Spaltenhauptschlüssel verwendet wird, oder Administratorrechte auf dem Computer.
- **Azure Key Vault**: Sie benötigen die Berechtigungen „get“, „unwrapKey“, und „verify“ für den Tresor, der den Spaltenhauptschlüssel enthält.
- **Schlüsselspeicheranbieter (CNG)** : Bei der Verwendung eines Schlüsselspeichers oder Schlüssels werden Sie möglicherweise aufgefordert, die erforderlichen Berechtigungen und Anmeldeinformationen anzugeben, welche von der Konfiguration des Speichers und des KSP abhängen.
- **Kryptografiedienstanbieter (Kryptografie-API)** : Bei der Verwendung eines Schlüsselspeichers oder Schlüssels werden Sie möglicherweise aufgefordert, die erforderlichen Berechtigungen und Anmeldeinformationen anzugeben, welche von der Konfiguration des Speichers und des CSP abhängen.

Zudem müssen Sie beim Erstellen von neuen Schlüsseln mit dem Assistenten über weitere Berechtigungen verfügen, die unter [Bereitstellen von Spaltenhauptschlüsseln mit dem Dialogfeld „Neuer Spaltenhauptschlüssel“](configure-always-encrypted-keys-using-ssms.md#provision-column-master-keys-with-the-new-column-master-key-dialog) und [Bereitstellen von Spaltenverschlüsselungsschlüsseln mit dem Dialogfeld „Neuer Spaltenverschlüsselungsschlüssel“](configure-always-encrypted-keys-using-ssms.md#provision-column-encryption-keys-with-the-new-column-encryption-key-dialog) aufgelistet sind.

## <a name="open-the-always-encrypted-wizard"></a>Öffnen des Always Encrypted-Assistenten
Der Assistent kann auf drei verschiedenen Ebenen gestartet werden: 
- Auf Datenbankebene zum Verschlüsseln mehrerer Spalten, die sich in verschiedenen Tabellen befinden.
- Auf Tabellenebene zum Verschlüsseln mehrerer Spalten, die sich in derselben Tabelle befinden.
- Auf Spaltenebene zum Verschlüsseln einer bestimmten Spalte.
 
 1. Stellen Sie eine Verbindung mit Ihrem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Objekt-Explorer-Komponente von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]her.  
   
 2. Führen Sie je nach gewünschter Verschlüsselung einen den folgenden Schritte aus:
     1. Wenn Sie mehrere Spalten in unterschiedlichen Tabellen einer Datenbank verschlüsseln möchten, klicken Sie mit der rechten Maustaste auf die Datenbank, zeigen Sie auf **Aufgaben**, und klicken Sie dann auf **Spalten verschlüsseln**.
     1. Wenn Sie mehrere Spalten in derselben Tabelle verschlüsseln möchten, navigieren Sie zu der Tabelle, klicken Sie mit der rechten Maustaste darauf, und klicken Sie dann auf **Spalten verschlüsseln**.
     1. Wenn Sie eine einzelne Spalte verschlüsseln möchten, navigieren Sie zu der Spalte, klicken Sie mit der rechten Maustaste darauf, und klicken Sie dann auf **Spalten verschlüsseln**.


   
 ## <a name="column-selection-page"></a>Die Seite „Spaltenauswahl“
Auf dieser Seite können Sie Spalten auswählen, die Sie verschlüsseln, erneut verschlüsseln oder entschlüsseln möchten. Anschließend definieren Sie die Konfiguration der Zielverschlüsselung für die ausgewählten Spalten.

Wählen Sie zum Verschlüsseln einer Klartextspalte (einer nicht verschlüsselten Spalte) einen Verschlüsselungstyp (**Deterministisch** oder **Zufällig**) und einen Verschlüsselungsschlüssel für die Spalte aus. 

Wenn Sie einen Verschlüsselungstyp ändern oder einen Spaltenverschlüsselungsschlüssel für eine bereits verschlüsselte Spalte rotieren lassen (ändern), wählen Sie den gewünschten Verschlüsselungstyp und den Schlüssel aus. 

Wählen Sie zum Verschlüsseln oder erneuten Verschlüsseln einer oder mehrerer Spalten mit einem neuen Spaltenverschlüsselungsschlüssel durch den Assistenten einen Schlüssel aus, dessen Name **(Neu)** enthält. Der Assistent generiert den Schlüssel.

Wählen Sie zum Entschlüsseln einer derzeit verschlüsselten Spalte als Verschlüsselungstyp **Klartext** aus.


> [!NOTE]
> Der Assistent unterstützt keine kryptografischen Vorgänge in temporalen und In-Memory-Tabellen. Erstellen Sie hierfür leere temporale oder In-Memory-Tabellen mit Transact-SQL, und fügen Sie Daten mithilfe Ihrer Anwendung ein.

## <a name="master-key-configuration-page"></a>Die Seite „Konfigurieren des Hauptschlüssels“
Wenn Sie auf der vorherigen Seite einen automatisch generierten Spaltenverschlüsselungsschlüssel für eine beliebige Spalte ausgewählt haben, müssen Sie auf dieser Seite entweder einen vorhandenen Spaltenhauptschlüssel auswählen oder einen neuen Spaltenhauptschlüssel konfigurieren, mit dem der Spaltenverschlüsselungsschlüssel verschlüsselt wird. 

Wenn Sie einen neuen Spaltenhauptschlüssel konfigurieren, können Sie entweder einen vorhandenen Schlüssel im Windows-Zertifikatspeicher oder in Azure Key Vault auswählen und mit dem Assistenten nur ein Metadatenobjekt für den Schlüssel in der Datenbank erstellen, oder Sie generieren sowohl den Schlüssel als auch das Metadatenobjekt, das den Schlüssel in der Datenbank beschreibt. 

Weitere Informationen zum Erstellen und Speichern von Spaltenhauptschlüsseln im Windows-Zertifikatspeicher, in Azure Key Vault oder in anderen Schlüsselspeichern finden Sie unter [Erstellen und Speichern von Spaltenhauptschlüsseln für Always Encrypted](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md).

> [!TIP]
> Mit dem Assistenten können Sie Schlüssel nur im Windows-Zertifikatspeicher und in Azure Key Vault suchen und erstellen. Außerdem werden die Namen der neuen Schlüssel und der Metadatenobjekte, die die Schlüssel in der Datenbank beschreiben, automatisch generiert. Wenn Sie mehr Kontrolle über die Bereitstellungsweise der Schlüssel wünschen (und mehr Auswahlmöglichkeiten beim Schlüsselspeicher für Ihren Spaltenhauptschlüssel), können Sie mithilfe der Dialogfelder **Neuer Spaltenhauptschlüssel** und **Neuer Spaltenverschlüsselungsschlüssel** zunächst die Schlüssel erstellen und anschließend den Assistenten ausführen, um die erstellten Schlüssel auszuwählen. Weitere Informationen finden Sie unter [Bereitstellen von Spaltenhauptschlüsseln mit dem Dialogfeld „Neuer Spaltenhauptschlüssel“](configure-always-encrypted-keys-using-ssms.md#provision-column-master-keys-with-the-new-column-master-key-dialog) und [Bereitstellen von Spaltenverschlüsselungsschlüsseln mit dem Dialogfeld „Neuer Spaltenverschlüsselungsschlüssel“](configure-always-encrypted-keys-using-ssms.md#provision-column-encryption-keys-with-the-new-column-encryption-key-dialog). 

## <a name="next-steps"></a>Nächste Schritte
- [Abfragen von Spalten mit Always Encrypted und SQL Server Management Studio](always-encrypted-query-columns-ssms.md)
- [Entwickeln von Anwendungen mit Always Encrypted](always-encrypted-client-development.md)

## <a name="see-also"></a>Weitere Informationen  
 - [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
 - [Übersicht über die Schlüsselverwaltung für Always Encrypted](overview-of-key-management-for-always-encrypted.md) 
 - [Konfigurieren von Always Encrypted mithilfe von SQL Server Management Studio](configure-always-encrypted-using-sql-server-management-studio.md)
 - [Bereitstellen von Always Encrypted-Schlüsseln mithilfe von PowerShell](configure-always-encrypted-keys-using-powershell.md)
 - [Konfigurieren der Spaltenverschlüsselung mithilfe von Always Encrypted mit PowerShell](configure-column-encryption-using-powershell.md)
 - [Konfigurieren der Spaltenverschlüsselung unter Verwendung von Always Encrypted mit einem DAC-Paket](configure-always-encrypted-using-dacpac.md)
