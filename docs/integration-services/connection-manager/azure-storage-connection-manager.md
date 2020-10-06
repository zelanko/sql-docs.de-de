---
title: Azure Storage-Verbindungs-Manager | Microsoft-Dokumentation
description: Der Azure Storage-Verbindungs-Manager ermöglicht einem SSIS-Paket, die Verbindung mit einem Azure Storage-Konto herzustellen.
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 44193053e6a5f09b2864b95ded9c5ac933c4cf95
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726021"
---
# <a name="azure-storage-connection-manager"></a>Azure Storage-Verbindungs-Manager

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Der Azure Storage-Verbindungs-Manager ermöglicht einem SQL Server Integration Services (SSIS)-Paket, die Verbindung mit einem Azure Storage-Konto herzustellen. Der Verbindungs-Manager ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Optionen **AzureStorage** > **Hinzufügen** aus.  
  
Die folgenden Eigenschaften sind verfügbar:

- **Dienst:** Gibt den Speicherdienst an, mit dem eine Verbindung hergestellt werden soll.
- **Kontoname:** Gibt den Speicherkontonamen an.
- **Authentifizierung:** Gibt die zu verwendende Authentifizierungsmethode an. „AccessKey“-, „ServicePrincipal“- und „SharedAccessSignature“-Authentifizierung werden unterstützt.
    - **AccessKey:** Geben Sie für diese Authentifizierungsmethode den **Kontoschlüssel** an.
    - **ServicePrincipal:** Geben Sie für diese Authentifizierungsmethode die **Anwendungs-ID**, den **Anwendungsschlüssel** und die **Mandanten-ID** des Dienstprinzipals an.
      Damit die **Testverbindung** funktioniert, müssen Sie dem Dienstprinzipal für das Speicherkonto mindestens die Rolle **Storage-Blobdatenleser** zuweisen.
      Weitere Informationen finden Sie unter [Gewähren von Zugriff auf Azure-Blob- und -Warteschlangendaten mit RBAC über das Azure-Portal](/azure/storage/common/storage-auth-aad-rbac-portal#assign-rbac-roles-using-the-azure-portal).
    - **SharedAccessSignature:** Geben Sie für diese Authentifizierungsmethode mindestens das **Token** der Shared Access Signature an.
      Zum Testen der Verbindung geben Sie zusätzlich den Ressourcenbereich an, der getestet werden soll. Möglicherweise handelt es sich um **Dienst**, **Container** oder **Blob**.
      Geben Sie für **Container** und **Blob** den Containernamen bzw. den Blobpfad an.
      Weitere Informationen finden Sie unter [Azure Storage SAS (Shared Access Signature) – Übersicht](/azure/storage/common/storage-sas-overview).
- **Umgebung:** Gibt die Cloudumgebung an, die das Speicherkonto hostet.

## <a name="managed-identities-for-azure-resources-authentication"></a>Verwaltete Identitäten für die Authentifizierung von Azure-Ressourcen
Beim Ausführen von SSIS-Paketen in [Azure-SSIS Integration Runtime in Azure Data Factory](/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime) können Sie die [verwaltete Identität](/azure/data-factory/connector-azure-sql-database#managed-identity), die Ihrer Data Factory zugeordnet ist, zur Authentifizierung des Azure-Speichers verwenden. Die angegebene Factory kann mithilfe dieser Identität auf Daten in Ihrem Speicherkonto zugreifen und Daten daraus oder dort hinein kopieren.

Weitere Informationen zur Azure Storage-Authentifizierung im Allgemeinen finden Sie unter [Autorisieren des Zugriffs auf Azure-Blobs und -Warteschlangen mit Azure Active Directory](/azure/storage/common/storage-auth-aad). So verwenden Sie die Authentifizierung der verwalteten Identität für Azure Storage:

1. [Suchen Sie die verwaltete Identität für Data Factory im Azure-Portal](/azure/data-factory/data-factory-service-identity). Wechseln Sie zu den **Eigenschaften** der Data Factory. Kopieren Sie die **Anwendungs-ID der verwalteten Identität** (nicht die **Objekt-ID der verwalteten Identität**).

1. Erteilen Sie die richtige Berechtigung für die verwaltete Identität in Ihrem Speicherkonto. Weitere Informationen zu den Rollen finden Sie unter [Verwalten von Zugriffsrechten auf Azure Storage-Daten mit RBAC](/azure/storage/common/storage-auth-aad-rbac-portal).

    - Erteilen Sie ihr **als Quelle** in der Zugriffssteuerung (IAM) mindestens die Rolle **Storage-Blobdatenleser**.
    - Erteilen Sie ihr **als Ziel** in der Zugriffssteuerung (IAM) mindestens die Rolle **Mitwirkender an Storage-Blobdaten**.

Konfigurieren Sie dann die Authentifizierung der verwalteten Identität für den Azure Storage-Verbindungs-Manager. Es gibt dafür folgende Optionen:

- **Konfigurieren zur Entwurfszeit.** Doppelklicken Sie im SSIS-Designer auf den Azure Storage-Verbindungs-Manager, um den **Azure Storage-Verbindungs-Manager-Editor** zu öffnen. Wählen Sie dort **Verwaltete Identität zur Authentifizierung bei Azure verwenden**.
    > [!NOTE]
    >  Derzeit hat diese Option keine Auswirkung (bedeutet, dass die Authentifizierung der verwalteten Identität nicht funktioniert) beim Ausführen des SSIS-Pakets im SSIS-Designer oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.
    
- **Konfigurieren zur Runtime.** Suchen Sie beim Ausführen des Pakets über [SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md) oder die [Aktivität „SSIS-Paket ausführen“ von Azure Data Factory](/azure/data-factory/how-to-invoke-ssis-package-ssis-activity) den Azure Storage-Verbindungs-Manager. Aktualisieren Sie dessen Eigenschaft `ConnectUsingManagedIdentity` auf `True`.
    > [!NOTE]
    >  In Azure-SSIS Integration Runtime werden alle anderen Authentifizierungsmethoden (z. B. Zugriffsschlüssel, Dienstprinzipal), die im Azure Storage-Verbindungs-Manager vorkonfiguriert sind, überschrieben, wenn die Authentifizierung der verwalteten Identität für Speichervorgänge verwendet wird.

> [!NOTE]
>  Um die Authentifizierung von verwalteten Identitäten für vorhandene Pakete zu konfigurieren, besteht die bevorzugte Methode darin, das SSIS-Projekt mindestens einmal mit dem [neuesten SSIS-Designer](../../ssdt/download-sql-server-data-tools-ssdt.md) neu zu erstellen. Stellen Sie dieses SSIS-Projekt erneut in ihrer Azure-SSIS Integration Runtime bereit, sodass die neue Eigenschaft `ConnectUsingManagedIdentity` des Verbindungs-Managers automatisch allen Azure Storage Verbindungs-Managern in Ihrem SSIS-Projekt hinzugefügt wird. Die alternative Methode besteht darin, eine Eigenschaftsüberschreibung direkt mit dem Eigenschaftenpfad **\Package.Connections[{Name Ihres Verbindungs-Managers}].Properties[ConnectUsingManagedIdentity]** zur Runtime zu verwenden.

## <a name="secure-network-traffic-to-your-storage-account"></a>Sichern von Netzwerkdatenverkehr an Ihr Speicherkonto
Azure Data Factory ist für Azure Storage jetzt ein [vertrauenswürdiger Microsoft-Dienst](/azure/storage/common/storage-network-security#trusted-microsoft-services). Wenn Sie die verwaltete Identitätsauthentifizierung verwenden, können Sie Ihr Speicherkonto schützen, indem Sie den [Zugriff auf ausgewählte Netzwerke beschränken](/azure/storage/common/storage-network-security#change-the-default-network-access-rule) und gleichzeitig Ihrer Data Factory den Zugriff auf Ihr Speicherkonto gestatten. Anweisungen finden Sie unter [Verwalten von Ausnahmen](/azure/storage/common/storage-network-security#managing-exceptions).

## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Verbindungen &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)