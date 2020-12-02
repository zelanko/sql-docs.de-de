---
description: Azure Resource Manager-Verbindungs-Manager
title: Azure Resource Manager-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPARMCM.F1
- SQL14.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: 8ce8024f-153f-4066-b607-0d36fefc79ed
author: Lingxi-Li
ms.author: lingxl
ms.openlocfilehash: 84b9c97935d0bcf89a4741304bb9a1e6b3576605
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96130134"
---
# <a name="azure-resource-manager-connection-manager"></a>Azure Resource Manager-Verbindungs-Manager

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


Der **Azure Resource Manager-Verbindungs-Manager** ermöglicht einem SSIS-Paket, Azure-Ressourcen mithilfe eines [Dienstprinzipals](/azure/azure-resource-manager/resource-group-create-service-principal-portal) zu verwalten.

Der **Azure Resource Manager-Verbindungs-Manager** ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Zum Erstellen und Konfigurieren eines **Azure Resource Manager-Verbindungs-Managers** führen Sie die folgenden Schritte aus:

1. Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **AzureResourceManager** aus, und klicken Sie auf **Hinzufügen**.
2. Geben Sie im Dialogfeld **Azure Resource Manager-Verbindungs-Manager-Editor** die **Anwendungs-ID**, den **Anwendungsschlüssel** und die **Mandanten-ID** für den Dienstprinzipal ein. Einzelheiten zu diesen Eigenschaften finden Sie in [diesem](/azure/azure-resource-manager/resource-group-create-service-principal-portal) Artikel.
3. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.
4. Die Eigenschaften des Verbindungs-Managers, die Sie im Fenster **Eigenschaften** erstellt haben, werden angezeigt.