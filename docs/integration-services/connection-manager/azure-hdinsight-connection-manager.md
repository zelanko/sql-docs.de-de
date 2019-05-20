---
title: Azure HDInsight-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPHDICM.F1
- SQL14.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 29d01bd9-8b38-43b1-b937-67f8aea57c0f
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.openlocfilehash: 89bf14fb82516a9bd819431d92962169d56f68ae
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728359"
---
# <a name="azure-hdinsight-connection-manager"></a>Azure HDInsight-Verbindungs-Manager

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Der **Azure HDInsight-Verbindungs-Manager** ermöglicht einem SSIS-Paket, die Verbindung mit einem Azure HDInsight-Cluster herzustellen.

Der **Azure HDInsight-Verbindungs-Manager** ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Zum Erstellen und Konfigurieren eines **Azure HDInsight-Verbindungs-Managers** führen Sie die folgenden Schritte aus:

1. Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **AzureHDInsight**aus, und klicken Sie auf **Hinzufügen**.
2. Geben Sie im Dialogfeld **Azure HDInsight-Verbindungs-Manager-Editor** den **Cluster-DNS-Namen** (ohne Protokollpräfix), den **Benutzernamen** und das **Kennwort** für den HDInsight-Cluster ein, mit dem die Verbindung hergestellt werden soll.
3. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.
4. Die Eigenschaften des Verbindungs-Managers, die Sie im Fenster **Eigenschaften** erstellt haben, werden angezeigt.
