---
title: Azure Resource Manager-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPARMCM.F1
- SQL14.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: 8ce8024f-153f-4066-b607-0d36fefc79ed
caps.latest.revision: 3
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.openlocfilehash: 8a91c4ebea3c135bd17ff4a61f50a78fceb69e70
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35405792"
---
# <a name="azure-resource-manager-connection-manager"></a>Azure Resource Manager-Verbindungs-Manager
Der **Azure Resource Manager-Verbindungs-Manager** ermöglicht einem SSIS-Paket, Azure-Ressourcen mithilfe eines [Dienstprinzipals](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) zu verwalten.

Der **Azure Resource Manager-Verbindungs-Manager** ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Zum Erstellen und Konfigurieren eines **Azure Resource Manager-Verbindungs-Managers** führen Sie die folgenden Schritte aus:

1. Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **AzureResourceManager** aus, und klicken Sie auf **Hinzufügen**.
2. Geben Sie im Dialogfeld **Azure Resource Manager-Verbindungs-Manager-Editor** die **Anwendungs-ID**, den **Anwendungsschlüssel** und die **Mandanten-ID** für den Dienstprinzipal ein. Einzelheiten zu diesen Eigenschaften finden Sie in [diesem](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) Artikel.
3. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.
4. Die Eigenschaften des Verbindungs-Managers, die Sie im Fenster **Eigenschaften** erstellt haben, werden angezeigt.
