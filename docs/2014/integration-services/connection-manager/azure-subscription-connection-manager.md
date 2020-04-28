---
title: Azure-Abonnementverbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpsubscrconn.f1
- sql11.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 31a24acb49abf4965e18443ef4c46ffd9a16f15c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176517"
---
# <a name="azure-subscription-connection-manager"></a>Azure-Abonnementverbindungs-Manager
  Der Azure HDInsight-Verbindungs-Manager ermöglicht die Verbindung eines SSIS-Pakets mit einem Azure-Abonnement, indem die Werte verwendet werden, die Sie für die folgenden Eigenschaften angeben: Azure-Abonnement-ID und das Verwaltungszertifikat.

1.  Wählen Sie im oben angezeigten Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **Azure-Abonnement**aus, und klicken Sie auf **Hinzufügen**.  Das Dialogfeld **Azure-Abonnementverbindungs-Manager-Editor** wird geöffnet.

     ![SSIS-AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "SSIS-AzureSubscriptionManager")

2.  Geben Sie Ihre Azure-Abonnement-ID, die ein Azure-Abonnement eindeutig identifiziert, in **Azure-Abonnement-ID**ein.  Der Wert befindet sich im [Azure-Verwaltungsportal](https://manage.windowsazure.com) auf der Seite **Einstellungen** :

     ![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")

3.  Wählen Sie **Verwaltungszertifikatspeicherort** und **Verwaltungszertifikatspeichername** aus den Dropdownlisten aus.

4.  Geben Sie **Management certificate thumbprint** (Fingerabdruck für as Verwaltungszertifikat) ein, oder klicken Sie auf **Durchsuchen...**, um ein Zertifikat aus dem ausgewählten Store auszuwählen. Das Zertifikat muss als Verwaltungszertifikat für das Abonnement hochgeladen werden. Klicken Sie hierzu auf der folgenden Seite des Azure-Portals auf **Hochladen** (in diesem [MSDN-Beitrag](https://msdn.microsoft.com/library/azure/gg551722.aspx) finden Sie weitere Informationen).

     ![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")

5.  Klicken Sie auf **Verbindung testen** , um die Verbindung zu testen.

6.  Klicken Sie auf **OK** , um das Dialogfeld zu schließen.


