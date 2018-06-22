---
title: Azure HDInsight-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.DTS.DESIGNER.AFPHDICM.F1
- SQL11.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 850a978d-5dba-45b6-a10e-306aafbc353d
caps.latest.revision: 2
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.openlocfilehash: 3d9486108e7f16870d2bf4e22f05b8a0a288b664
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059665"
---
# <a name="azure-hdinsight-connection-manager"></a>Azure HDInsight-Verbindungs-Manager
Der **Azure HDInsight-Verbindungs-Manager** ermöglicht einem SSIS-Paket, die Verbindung mit einem Azure HDInsight-Cluster herzustellen.

Zum Erstellen und Konfigurieren eines **Azure HDInsight-Verbindungs-Managers** führen Sie die folgenden Schritte aus:

1. Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **AzureHDInsight**aus, und klicken Sie auf **Hinzufügen**.
2. Geben Sie im Dialogfeld **Azure HDInsight-Verbindungs-Manager-Editor** den **Cluster-DNS-Namen** (ohne Protokollpräfix), den **Benutzernamen** und das **Kennwort** für den HDInsight-Cluster ein, mit dem die Verbindung hergestellt werden soll.
3. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.
4. Die Eigenschaften des Verbindungs-Managers, die Sie im Fenster **Eigenschaften** erstellt haben, werden angezeigt.