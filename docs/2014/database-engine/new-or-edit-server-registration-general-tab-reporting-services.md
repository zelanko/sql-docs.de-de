---
title: Neue serverregistrierung und Serverregistrierung (Registerkarte "Allgemein") (Reporting Services) bearbeiten | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.registerserver.general.reportserver.f1
ms.assetid: 5f899a8e-52ef-46b5-b7a9-f200ccd9f724
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 17c10bb36de85a7d0ad1d9522d5d54a540d51a61
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060102"
---
# <a name="new-or-edit-server-registration-general-tab-reporting-services"></a>Neue Serverregistrierung und Serverregistrierung bearbeiten (Registerkarte Allgemein) (Reporting Services)
  Auf dieser Registerkarte können Optionen festgelegt werden, wenn eine Instanz von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]registriert wird.  
  
 Um auf die Seite zuzugreifen, klicken Sie auf der Symbolleiste **Registrierte Server** auf **Reporting Services** , klicken Sie mit der rechten Maustaste auf eine registrierte Servergruppe wie **Reporting Services**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **Serverregistrierung**.  
  
## <a name="options"></a>Tastatur  
 **Servertyp**  
 Wenn Sie einen Server über Registrierte Server registrieren, ist das Feld **Servertyp** schreibgeschützt, wobei der Feldeintrag mit dem im Bereich **Registrierte Server** angezeigten Servertyp übereinstimmt. Um einen anderen Servertyp zu registrieren, klicken Sie auf der Symbolleiste **Registrierte Server** auf den gewünschten Server, bevor Sie mit der Registrierung eines neuen Servers beginnen.  
  
 **Servername**  
 Geben Sie die Berichtsserverinstanz an, zu der eine Verbindung hergestellt werden soll. In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]können Sie über den Instanznamen des Berichtsservers auf einen Berichtsserver zugreifen. Für jede SQL Server-Instanz, die Sie installieren, ist eine Berichtsserverinstanz zulässig. Wenn Sie die Standardinstanz verwenden, geben Sie den Namen der SQL Server-Instanz ein. Wenn Sie eine benannte Instanz verwenden, geben Sie zum Verbinden mit dem Berichtsserver die benannte Instanz im Format MSSQL$InstanceName ein.  
  
 **Authentifizierung**  
 Die Authentifizierung bei einem Berichtsserver erfolgt durch Internetinformationsdienste (IIS). Wählen Sie beim Herstellen einer Verbindung mit Reporting Services einen der folgenden Authentifizierungsmodi aus:  
  
 **Windows-Authentifizierungsmodus (Windows-Authentifizierung)**  
 Stellt die Verbindung zur Berichtsserverinstanz mithilfe der Anmeldeinformationen von [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows her.  
  
 **Standardauthentifizierung**  
 Stellen Sie die Verbindung mit **Standardauthentifizierung** her, wenn die Reporting Services-Installation für die Verwendung der Standardauthentifizierung konfiguriert ist.  
  
 **Formularauthentifizierung**  
 Stellen Sie die Verbindung mit **Formularauthentifizierung** her, wenn die Reporting Services-Installation für die Verwendung der Formularauthentifizierung konfiguriert ist.  
  
 **Benutzername**  
 Geben Sie den Benutzernamen ein, der für die Verbindung verwendet werden soll. Diese Option ist nur verfügbar, wenn Sie **Standardauthentifizierung** oder **Formularauthentifizierung**ausgewählt haben.  
  
 **Kennwort**  
 Geben Sie das Kennwort für den Benutzernamen ein. Diese Option kann nur bearbeitet werden, wenn Sie **Standardauthentifizierung** oder **Formularauthentifizierung**ausgewählt haben.  
  
 **Kennwort speichern**  
 Speichert das eingegebene Kennwort. Diese Option ist nur verfügbar, wenn Sie **Standardauthentifizierung** oder **Formularauthentifizierung**ausgewählt haben.  
  
> [!NOTE]  
>  Wenn Sie das Kennwort gespeichert haben und für die Zukunft nicht mehr speichern möchten, deaktivieren Sie das Kontrollkästchen, und klicken Sie auf **Speichern**.  
  
 **Name des registrierten Servers**  
 Der Name, der unter Registrierte Server angezeigt werden soll. Dieser Name muss mit dem Eintrag im Feld **Servername** nicht übereinstimmen.  
  
 **Beschreibung des registrierten Servers**  
 Geben Sie eine optionale Beschreibung des Servers ein.  
  
 **Test**  
 Klicken Sie hier, um die Verbindung mit dem unter **Servername**ausgewählten Server zu testen.  
  
 **Speichern**  
 Klicken Sie hier, um die Einstellungen des registrierten Servers zu speichern.  
  
  