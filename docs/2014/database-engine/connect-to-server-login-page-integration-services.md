---
title: Verbinden mit SQL Server Integration Services (Seite Anmeldung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodtsserver.login.f1
- sql12.swb.connecttodts.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3f6ead7090e0ffc3efaa3fbf979d4012d2a43388
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934621"
---
# <a name="connect-to-server-login-page-integration-services"></a>Verbinden mit SQL Server Integration Services (Seite Anmeldung)
  Mit dieser Registerkarte können Sie die folgenden Optionen anzeigen oder angeben, wenn Sie eine Verbindung mit herstellen [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
## <a name="options"></a>Tastatur  
 **Servertyp**  
 Wenn Sie einen Server über den Objekt-Explorer registrieren, wählen Sie den Typ des Servers aus, mit dem eine Verbindung hergestellt wird: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services oder Integration Services. Im verbleibenden Bereich des Dialogfelds werden nur die Optionen angezeigt, die auf den ausgewählten Servertyp zutreffen. Wenn Sie einen Server über „Registrierte Server“ registrieren, ist das Feld **Servertyp** schreibgeschützt, wobei der Feldeintrag mit dem in der Komponente „Registrierte Server“ angezeigten Servertyp übereinstimmt. Zum Registrieren eines anderen Servertyps wählen Sie auf der Symbolleiste "Registrierte Server" die Option [!INCLUDE[ssDE](../includes/ssde-md.md)], "Analysis Services", "Reporting Services" oder "Integration Services" aus. Anschließend können Sie mit der Registrierung eines neuen Servers beginnen.  
  
 **Servername**  
 Wählen Sie den Server für die Verbindungsherstellung aus. Standardmäßig wird die Serverinstanz angezeigt, mit der zuletzt eine Verbindung bestanden hat.  
  
> [!NOTE]  
>  Verwenden Sie nicht *\<servername>* \\ *\<instancename>* , da [!INCLUDE[ssIS](../includes/ssis-md.md)] nicht mehrere Instanzen auf einem Computer unterstützt.  
  
 **Authentifizierung**  
 Für [!INCLUDE[msCoName](../includes/msconame-md.md)] steht nur die [!INCLUDE[ssIS](../includes/ssis-md.md)]Windows-Authentifizierung zur Verfügung. Der Windows Authentifizierungsmodus ermöglicht Benutzern die Verbindung über ein Windows-Benutzerkonto.  
  
 **Benutzername**  
 Diese Option ist nicht verfügbar, da für [!INCLUDE[ssIS](../includes/ssis-md.md)]nur die Windows-Authentifizierung zur Verfügung steht.  
  
 **Kennwort**  
 Diese Option ist nicht verfügbar, da für [!INCLUDE[ssIS](../includes/ssis-md.md)]nur die Windows-Authentifizierung zur Verfügung steht.  
  
 **Kennwort speichern**  
 Diese Option ist nicht verfügbar, da für [!INCLUDE[ssIS](../includes/ssis-md.md)]nur die Windows-Authentifizierung zur Verfügung steht.  
  
 **Herstellen einer Verbindung**  
 Stellt eine Verbindung zu dem oben ausgewählten Server her.  
  
 **Optionen**  
 Klicken Sie hier, um die Anzeige des Dialogfelds zu ändern und die zusätzlichen Serververbindungsoptionen, z. B. Speichern des Kennworts, auszublenden.  
  
  
