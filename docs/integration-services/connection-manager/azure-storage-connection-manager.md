---
title: Azure Storage-Verbindungs-Manager | Microsoft-Dokumentation
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
author: janinezhang
ms.author: janinez
ms.openlocfilehash: f171499471f8f94ad970446d31cf796f4ab55fb7
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028772"
---
# <a name="azure-storage-connection-manager"></a>Azure Storage-Verbindungs-Manager

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

  Der **Azure Storage-Verbindungs-Manager** ermöglicht einem SSIS-Paket, die Verbindung mit einem Azure Storage-Konto herzustellen.
   
 Der **Azure Storage-Verbindungs-Manager** ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **AzureStorage**aus, und klicken Sie auf **Hinzufügen**.  
  
Die folgenden Eigenschaften sind verfügbar.

- **Dienst:** Gibt den Speicherdienst an, mit dem eine Verbindung hergestellt werden soll.
- **Kontoname:** Gibt den Speicherkontonamen an.
- **Authentifizierung:** Gibt die zu verwendende Authentifizierungsmethode an. **AccessKey**- und **ServicePrincipal**-Authentifizierung werden unterstützt.
    - **AccessKey:** Geben Sie für diese Authentifizierungsmethode den **Kontoschlüssel** an.
    - **ServicePrincipal:** Geben Sie für diese Authentifizierungsmethode die **Anwendungs-ID**, den **Anwendungsschlüssel** und die **Mandanten-ID** des Dienstprinzipals an.
      Damit die **Testverbindung** funktioniert, müssen Sie dem Dienstprinzipal für das Speicherkonto mindestens die Rolle **Storage Blob Data Reader** (Storage-Blobdatenleser) zuweisen.
      Details dazu finden Sie auf [dieser](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac-portal#assign-rbac-roles-using-the-azure-portal) Seite.
- **Umgebung:** Gibt die Cloudumgebung an, die das Speicherkonto hostet.

## <a name="managed-identities-for-azure-resources-authentication"></a>Verwaltete Identitäten für die Authentifizierung von Azure-Ressourcen
Beim Ausführen von SSIS-Paketen in [Azure-SSIS Integration Runtime in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime) können Sie die [verwaltete Identität](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-database#managed-identity), die Ihrer Data Factory zugeordnet ist, zur Authentifizierung des Azure-Speichers verwenden. Die angegebene Factory kann mithilfe dieser Identität auf Daten in Ihrem Speicherkonto zugreifen und Daten daraus oder dort hinein kopieren.

Weitere Informationen zur Azure Storage-Authentifizierung im Allgemeinen finden Sie unter [Autorisieren des Zugriffs auf Azure-Blobs und -Warteschlangen mit Azure Active Directory](https://docs.microsoft.com/azure/storage/common/storage-auth-aad). Damit Sie die Authentifizierung der verwalteten Identität für Azure-Speicher verwenden können, führen Sie die folgenden Schritte zum Konfigurieren des Speicherkontos aus:

1. **[Suchen Sie die verwaltete Identität für Data Factory im Azure-Portal](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity)** . Wechseln Sie zu den **Eigenschaften** der Data Factory. Kopieren Sie die **Anwendungs-ID der verwalteten Identität** (NICHT die **Objekt-ID der verwalteten Identität**).

1. **Erteilen Sie die richtige Berechtigung für die verwaltete Identität in Ihrem Speicherkonto**. Weitere Informationen zu den Rollen finden Sie unter [Gewähren von Zugriff auf Azure-Blob- und -Warteschlangendaten mit RBAC](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac-portal).

    - Erteilen Sie ihr **als Quelle** in der Zugriffssteuerung (IAM) mindestens die Rolle **Storage-Blobdatenleser**.
    - Erteilen Sie ihr **als Ziel** in der Zugriffssteuerung (IAM) mindestens die Rolle **Mitwirkender an Storage-Blobdaten**.

**Konfigurieren Sie dann die Authentifizierung der verwalteten Identität** für den Azure Storage-Verbindungs-Manager. Es gibt dafür zwei Möglichkeiten.

1. Konfigurieren zur Entwurfszeit. Doppelklicken Sie im SSIS-Designer auf den Azure Storage-Verbindungs-Manager, um den **Azure Storage-Verbindungs-Manager-Editor** zu öffnen, und aktivieren Sie die Option **Verwaltete Identität zur Authentifizierung bei Azure verwenden**.
    > [!NOTE]
    >  Derzeit hat diese Option KEINE Auswirkung (Angabe, dass die Authentifizierung der verwalteten Identität nicht funktioniert) beim Ausführen des SSIS-Pakets im SSIS-Designer oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.
    
1. Konfigurieren zur Laufzeit. Beim Ausführen des Pakets über [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) oder die [Aktivität „SSIS-Paket ausführen“ von Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity) suchen Sie den Azure Storage-Verbindungs-Manager, und aktualisieren Sie die Eigenschaft  **ConnectUsingManagedIdentity** auf den Wert **True**.
    > [!NOTE]
    >  In Azure-SSIS Integration Runtime werden alle anderen Authentifizierungsmethoden (z. B. Zugriffsschlüssel, Dienstprinzipal), die im Azure Storage-Verbindungs-Manager vorkonfiguriert sind, **überschrieben**, wenn die Authentifizierung der verwalteten Identität für Speichervorgänge verwendet wird.

> [!NOTE]
>  Zum Konfigurieren der Authentifizierung der verwalteten Identität bei vorhandenen Paketen sollten Sie das SSIS-Projekt mindestens einmal mit dem [neuesten SSIS-Designer](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) neu erstellen und dieses SSIS-Projekt in der Azure-SSIS Integration Runtime erneut bereitstellen, damit die neue Eigenschaft **ConnectUsingManagedIdentity** des Verbindungs-Managers automatisch allen Azure Storage-Verbindungs-Managern im SSIS-Projekt hinzugefügt wird. Die alternative Methode besteht darin, die Eigenschaft direkt mit dem Eigenschaftenpfad **\Package.Connections[{Name Ihres Verbindungs-Managers}].Properties[ConnectUsingManagedIdentity]** zur Runtime zu verwenden.

## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Verbindungen &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)
