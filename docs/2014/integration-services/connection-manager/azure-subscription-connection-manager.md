---
title: Azure-Abonnementverbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.afpsubscrconn.f1
- sql11.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 878f8fc674659d91a732549fcd68da134cdf5fc4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162317"
---
# <a name="azure-subscription-connection-manager"></a>Azure-Abonnementverbindungs-Manager
  Der Azure HDInsight-Verbindungs-Manager ermöglicht einem SSIS-Paket zum Herstellen einer Verbindung mit einem Azure-Abonnement mithilfe der Werte, die Sie angeben, für die Eigenschaften: Azure-Abonnement-ID und das Verwaltungszertifikat.  
  
1.  Wählen Sie im oben angezeigten Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **Azure-Abonnement**aus, und klicken Sie auf **Hinzufügen**.  Das Dialogfeld **Azure-Abonnementverbindungs-Manager-Editor** wird geöffnet.  
  
     ![SSIS-AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "SSIS-AzureSubscriptionManager")  
  
2.  Geben Sie Ihre Azure-Abonnement-ID, die ein Azure-Abonnement eindeutig identifiziert, in **Azure-Abonnement-ID**ein.  Der Wert befindet sich im [Azure-Verwaltungsportal](https://manage.windowsazure.com) auf der Seite **Einstellungen** :  
  
     ![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")  
  
3.  Wählen Sie **Verwaltungszertifikatspeicherort** und **Verwaltungszertifikatspeichername** aus den Dropdownlisten aus.  
  
4.  Geben Sie den **Fingerabdruck des Verwaltungszertifikats** ein, oder klicken Sie auf **Durchsuchen...**, um im ausgewählten Store ein Zertifikat auszuwählen. Das Zertifikat muss als Verwaltungszertifikat für das Abonnement hochgeladen werden. Klicken Sie hierzu auf der folgenden Seite des Azure-Portals auf **Hochladen** (in diesem [MSDN-Beitrag](https://msdn.microsoft.com/library/azure/gg551722.aspx) finden Sie weitere Informationen).  
  
     ![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")  
  
5.  Klicken Sie auf **Verbindung testen** , um die Verbindung zu testen.  
  
6.  Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
  