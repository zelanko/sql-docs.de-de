---
title: Azure Data Lake Store-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: douglasl
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.openlocfilehash: 5db5df2a209cf9f291c37f960cdd9b2947966061
ms.sourcegitcommit: 85fd3e1751de97a16399575397ab72ebd977c8e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2018
ms.locfileid: "53531105"
---
# <a name="azure-data-lake-store-connection-manager"></a>Azure Data Lake Store-Verbindungsmanager
Ein SSIS-Paket (SQL Server Integration Services) kann den Azure Data Lake Store-Verbindungs-Manager verwenden, um einen Azure Data Lake Storage Gen1-Konto mit einem der beiden folgenden Authentifizierungstypen zu verbinden:
-   Azure AD-Benutzeridentität
-   Azure AD-Dienstidentität 

Der Azure Data Lake Storage-Verbindungs-Manager ist eine Komponente von [SQL Server Integration Services (SSIS) Feature Pack für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

> [!NOTE]
> Um sicherzustellen, dass der Azure Data Lake Store-Verbindungs-Manager und die Komponenten, die ihn verwenden – das bedeutet Data Lake Storage Gen1 source und Azure Data Lake Storage Gen1 Destination – eine Verbindung zu Diensten herstellen können, stellen Sie sicher, dass Sie die neueste Version von Azure Feature Pack [hier](https://www.microsoft.com/download/details.aspx?id=49492)herunterladen. 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Konfigurieren des Azure Data Lake Store-Verbindungs-Manager

1.  Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** **AzureDataLake** aus, und klicken Sie auf **Hinzufügen**. Das Dialogfeld **Azure Data Lake Store Connection Manager Editor** (Azure Data Lake Store-Verbindungs-Manager-Editor) wird geöffnet.
  
2.  Geben Sie im Dialogfeld **Azure Data Lake Store-Verbindungs-Manager-Editor** im Feld **ADLS-Host** die URL des Data Lake Storage Gen1-Hosts ein. Zum Beispiel: `https://test.azuredatalakestore.net` oder `test.azuredatalakestore.net`.
  
3.  Wählen Sie im Feld **Authentifizierung** den entsprechenden Authentifizierungstyp für den Zugriff auf Daten in Data Lake Storage Gen1 aus.

    1.  Wenn Sie die Authentifizierungsoption **Azure AD-Benutzeridentität** ausgewählt haben, gehen Sie wie folgt vor:
        1. Geben Sie Werte für die Felder **Benutzername** und **Kennwort** an. 
    
        2. Klicken Sie auf **Verbindung testen**, um die Verbindung zu testen. Wenn Sie oder der Mandantenadministrator dem Zugriff von SSIS auf Ihre Data Lake Storage Gen1-Daten nicht zugestimmt haben, klicken Sie bei Aufforderung auf **Zustimmen**. Weitere Informationen über diese Zustimmungsoberfläche finden Sie unter [Integrieren von Anwendungen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        > [!NOTE] 
        > Bei Auswahl der Authentifizierungsoption **Azure AD-Benutzeridentität** werden die mehrstufige Authentifizierung und die Authentifizierung mittels Microsoft-Konto nicht unterstützt.
    
    2. Wenn Sie die Option **Azure AD Service Identity** (Azure AD-Dienstidentität) ausgewählt haben, gehen Sie wie folgt vor:
        1. Erstellen Sie eine AAD-Anwendung (Azure Active Directory) und einen Dienstprinzipal für den Zugriff auf Daten in Data Lake Storage Gen1.
    
        2. Weisen Sie der AAD-Anwendung die entsprechenden Berechtigungen zu, damit diese auf Ihre Data Lake Storage Gen1-Ressourcen zugreifen kann. Weitere Informationen zu dieser Authentifizierungsoption finden Sie unter [Use portal to create Active Directory application and service principal that can access resources (Verwenden von Portal zum Erstellen von Active Directory-Anwendungen und Dienstprinzipal zum Zugriff auf Ressourcen)](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        3. Geben Sie Werte für die Felder **Client-ID**, **Geheimer Schlüssel** und **Mandantenname** an.
    
        4. Klicken Sie auf **Verbindung testen**, um die Verbindung zu testen.  
  
6.  Klicken Sie auf **OK**, um das Dialogfeld **Azure Data Lake Store Connection Manager Editor** (Azure Data Lake Store-Verbindungs-Manager-Editor) zu schließen.  

## <a name="view-the-properties-of-the-connection-manager"></a>Anzeigen der Eigenschaften des Verbindungs-Managers
Die Eigenschaften des Verbindungs-Managers, die Sie im Fenster **Eigenschaften** erstellt haben, werden angezeigt.  
  
  
