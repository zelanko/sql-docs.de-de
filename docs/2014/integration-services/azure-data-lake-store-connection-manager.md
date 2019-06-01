---
title: Azure Data Lake Store-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSCM.F1
- SQL11.DTS.DESIGNER.AFPADLSCM.F1
ms.assetid: 7f1323f9-9dc3-4378-9c70-bbc65bfeabfd
author: yualan
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9fe7c7cf04767e0536be8d04d99387a091962375
ms.sourcegitcommit: 5905c29b5531cef407b119ebf5a120316ad7b713
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66429007"
---
# <a name="azure-data-lake-store-connection-manager"></a>Azure Data Lake Store-Verbindungsmanager
  Die **Azure Data Lake Store-Verbindungs-Manager** ermöglicht einem SSIS-Paket für die Verbindung mit einem Azure Data Lake Store-Dienst durch zwei Authentifizierungstypen: Azure AD-Benutzeridentität und Azure AD-Dienstidentität.  

## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Konfigurieren des Azure Data Lake Store-Verbindungs-Manager 
  
1.  Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **AzureDataLake**aus, und klicken Sie auf **Hinzufügen**.   
  
2.  Geben Sie im Dialogfeld Azure Data Lake Store-Verbindungsmanager-Editor die URL des Azure Data Lake Store-Host in das Feld **ADLS Host** ein. Zum Beispiel: Https:\//test.azuredatalakestore.net oder test.azuredatalakestore.net.
  
3.  Wählen Sie den entsprechenden Authentifizierungstyp für den Zugriff auf Azure Data Lake Store-Daten aus.

    1.  Wenn Sie die Option **Azure AD User Identity** ausgewählt haben, führen Sie folgendes aus:

        1. Geben Sie Werte für die Felder **Benutzername** und **Kennwort** an. 
    
        2. Klicken Sie auf die Schaltfläche **Verbindung testen** , um die Verbindung zu testen. Wenn Sie und der Mandantenadministrator vorher nicht zugestimmt haben, dass SSIS auf Azure Data Lake Store-Daten zugreift, müssen Sie auf die Schaltfläche **Annehmen** klicken, um im Popout-Dialog die Zustimmung zu erteilen, dass SSIS auf Ihre Azure Data Lake Store-Daten zugreifen darf. Weitere Informationen über diese Zustimmungsoberfläche finden Sie unter [Integrieren von Anwendungen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        > [!NOTE] 
        > Bei der Authentifizierungsoption „Azure AD User Identity“ werden die mehrstufige Authentifizierung und das Microsoft-Konto NICHT unterstützt.
    
    2.  Wenn Sie die Option **Azure AD Service Identity** ausgewählt haben, führen Sie Folgendes durch:
        1. Erstellen Sie eine AAD-Anwendung und ein Dienstprinzipal, die auf Azure Data Lake-Ressourcen zugreifen können.
    
        2. Weisen Sie dieser AAD-Anwendung die entsprechenden Berechtigungen zu, um auf Ihre Azure Data Lake-Ressourcen zuzugreifen. Weitere Informationen zu dieser Authentifizierungsoption finden Sie unter [Use portal to create Active Directory application and service principal that can access resources (Verwenden von Portal zum Erstellen von Active Directory-Anwendungen und Dienstprinzipal zum Zugriff auf Ressourcen)](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        3. Geben Sie Werte für die Felder **Client-ID**, **Geheimer Schlüssel** , und **Mandantenname** an.
    
        4. Klicken Sie auf die Schaltfläche **Verbindung testen** , um die Verbindung zu testen.  
  
4.  Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
    Die Eigenschaften des Verbindungs-Managers, die Sie im Fenster **Eigenschaften** erstellt haben, werden angezeigt.  
  
  
