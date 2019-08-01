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
ms.openlocfilehash: 8a115dafb386323bc1f4738720e7576657d22543
ms.sourcegitcommit: 2efb0fa21ff8093384c1df21f0e8910db15ef931
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "68316690"
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
