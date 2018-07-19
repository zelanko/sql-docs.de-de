---
title: Azure Data Lake Analytics-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/18/2018
ms.prod: sql
ms.prod_service: integration-services
ms.component: connection-manager
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
caps.latest.revision: 7
author: yanancai
ms.author: yanacai
manager: craigg
ms.openlocfilehash: 17b63aad55cf50262d7e1e56267859b1a34cc9d3
ms.sourcegitcommit: 44e9bf62f2c75449c17753ed66bf85c43928dbd5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854412"
---
# <a name="azure-data-lake-analytics-connection-manager"></a>Azure Data Lake Analytics-Verbindungs-Manager

Ein SSIS-Paket (SQL Server Integration Services) kann den Azure Data Lake Analytics-Verbindungs-Manager verwenden, um ein Azure Data Lake Analytics-Konto mit einem der beiden folgenden Authentifizierungstypen zu verbinden:
-   Azure AD-Benutzeridentität
-   Azure AD-Dienstidentität 

Der Azure Data Lake Analytics-Verbindungs-Manager ist eine Komponente von [SQL Server Integration Services (SSIS) Feature Pack für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
 
## <a name="configure-the-azure-data-lake-analytics-connection-manager"></a>Konfigurieren des Azure Data Lake Analytics-Verbindungs-Managers

1.  Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** **AzureDataLakeAnalytics** aus, und klicken Sie auf **Hinzufügen**. Das Dialogfeld **Azure Data Lake Analytics-Verbindungs-Manager-Editor** wird geöffnet.
  
2.  Geben Sie im Dialogfeld **Azure Data Lake Analytics-Verbindungs-Manager-Editor** im Feld **ADLA-Kontoname** den Kontonamen des Azure Data Lake Analytics-Kontos ein. Beispiel: meinADLAKontoname.
  
3.  Wählen Sie im Feld **Authentifizierung** den entsprechenden Authentifizierungstyp für den Zugriff auf Daten in Azure Data Lake Analytics aus.

    1.  Wenn Sie die Authentifizierungsoption **Azure AD-Benutzeridentität** ausgewählt haben, gehen Sie wie folgt vor:
        1. Geben Sie Werte für die Felder **Benutzername** und **Kennwort** an. 
    
        2. Klicken Sie auf **Verbindung testen**, um die Verbindung zu testen. Wenn Sie oder der Mandantenadministrator dem Zugriff von SSIS auf Ihre Azure Data Lake Analytics-Daten nicht zugestimmt haben, klicken Sie bei Aufforderung auf **Zustimmen**. Weitere Informationen über diese Zustimmungsoberfläche finden Sie unter [Integrieren von Anwendungen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        >   [!NOTE] 
        > Bei Auswahl der Authentifizierungsoption **Azure AD-Benutzeridentität** werden die mehrstufige Authentifizierung und die Authentifizierung mittels Microsoft-Konto nicht unterstützt.
    
    2. Wenn Sie die Option **Azure AD Service Identity** (Azure AD-Dienstidentität) ausgewählt haben, gehen Sie wie folgt vor:
        1. Erstellen Sie eine AAD-Anwendung (Azure Active Directory) und einen Dienstprinzipal für den Zugriff auf das Azure Data Lake Analytics-Konto. Weitere Informationen zu dieser Authentifizierungsoption finden Sie unter [Use portal to create Active Directory application and service principal that can access resources (Verwenden von Portal zum Erstellen von Active Directory-Anwendungen und Dienstprinzipal zum Zugriff auf Ressourcen)](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        2. Weisen Sie der AAD-Anwendung die entsprechenden Berechtigungen zu, damit diese auf Ihr Azure Data Lake Analytics-Konto zugreifen kann. Erfahren Sie, wie Sie Berechtigungen für Ihr Azure Data Lake Analytics-Konto [mithilfe des Assistenten zum Hinzufügen eines Benutzers](https://docs.microsoft.com/azure/data-lake-analytics/data-lake-analytics-manage-use-portal#add-a-new-user) gewähren. 
    
        3. Geben Sie Werte für die Felder **Anwendungs-ID**, **Authentifizierungsschlüssel** und **Mandanten-ID** an.
    
        4. Klicken Sie auf **Verbindung testen**, um die Verbindung zu testen.  

4.  Klicken Sie auf **OK**, um das Dialogfeld **Azure Data Lake Analytics-Verbindungs-Manager-Editor** zu schließen.  

## <a name="view-the-properties-of-the-connection-manager"></a>Anzeigen der Eigenschaften des Verbindungs-Managers
Die Eigenschaften des Verbindungs-Managers, die Sie im Fenster **Eigenschaften** erstellt haben, werden angezeigt.  
  
  
