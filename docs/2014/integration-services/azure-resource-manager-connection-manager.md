---
title: Azure Resource Manager-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPARMCM.F1
- SQL11.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: a2380258-0418-4a8c-a731-5071a44ddf1e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1dce4def11f14072295dbf3cde9d5ab77304fe74
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439347"
---
# <a name="azure-resource-manager-connection-manager"></a>Azure Resource Manager-Verbindungs-Manager
Der **Azure Resource Manager-Verbindungs-Manager** ermöglicht einem SSIS-Paket, Azure-Ressourcen mithilfe eines [Dienstprinzipals](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) zu verwalten.

Zum Erstellen und Konfigurieren eines **Azure Resource Manager-Verbindungs-Managers** führen Sie die folgenden Schritte aus:

1. Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **AzureResourceManager** aus, und klicken Sie auf **Hinzufügen**.
2. Geben Sie im Dialogfeld **Azure Resource Manager-Verbindungs-Manager-Editor** die **Anwendungs-ID**, den **Anwendungsschlüssel** und die **Mandanten-ID** für den Dienstprinzipal ein. Einzelheiten zu diesen Eigenschaften finden Sie in [diesem](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) Artikel.
3. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.
4. Die Eigenschaften des Verbindungs-Managers, die Sie im Fenster **Eigenschaften** erstellt haben, werden angezeigt.
