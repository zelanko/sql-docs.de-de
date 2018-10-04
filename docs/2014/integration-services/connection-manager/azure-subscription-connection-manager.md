---
title: Azure-Abonnementverbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpsubscrconn.f1
- sql11.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8bd5b0c92a1f4b089d86660af0766686708c1a06
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183840"
---
# <a name="azure-subscription-connection-manager"></a>Azure-Abonnementverbindungs-Manager
  Der Azure HDInsight-Verbindungs-Manager ermöglicht einem SSIS-Paket zum Verbinden mit einem Azure-Abonnement, indem Sie mit den Werten, die Sie angeben, für die Eigenschaften: Azure-Abonnement-ID und das Verwaltungszertifikat.  
  
1.  Wählen Sie im oben angezeigten Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **Azure-Abonnement**aus, und klicken Sie auf **Hinzufügen**.  Das Dialogfeld **Azure-Abonnementverbindungs-Manager-Editor** wird geöffnet.  
  
     ![SSIS-AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "SSIS-AzureSubscriptionManager")  
  
2.  Geben Sie Ihre Azure-Abonnement-ID, die ein Azure-Abonnement eindeutig identifiziert, in **Azure-Abonnement-ID**ein.  Der Wert befindet sich im [Azure-Verwaltungsportal](https://manage.windowsazure.com) auf der Seite **Einstellungen** :  
  
     ![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")  
  
3.  Wählen Sie **Verwaltungszertifikatspeicherort** und **Verwaltungszertifikatspeichername** aus den Dropdownlisten aus.  
  
4.  Geben Sie den **Fingerabdruck des Verwaltungszertifikats** ein, oder klicken Sie auf **Durchsuchen...**, um im ausgewählten Store ein Zertifikat auszuwählen. Das Zertifikat muss als Verwaltungszertifikat für das Abonnement hochgeladen werden. Klicken Sie hierzu auf der folgenden Seite des Azure-Portals auf **Hochladen** (in diesem [MSDN-Beitrag](https://msdn.microsoft.com/library/azure/gg551722.aspx) finden Sie weitere Informationen).  
  
     ![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")  
  
5.  Klicken Sie auf **Verbindung testen** , um die Verbindung zu testen.  
  
6.  Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
  
