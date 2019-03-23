---
title: Seite "Allgemein" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Business_Intelligence_Designers.Data_Transformation_Designers.General
ms.assetid: d695690a-923b-4036-945e-7621e8651deb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f27ec0c9fe8078bb11a48114a3d456793271853d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58391758"
---
# <a name="general-page"></a>Seite Allgemein
  Verwenden Sie die Seite **Allgemein** der Seite **Integration Services-Designer** im Dialogfeld **Optionen** , um die Optionen für das Laden, Anzeigen und Aktualisieren von Paketen festzulegen.  
  
 Um die Seite **Allgemein** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]zu öffnen, klicken Sie im Menü **Extras** auf **Optionen**, erweitern **Business Intelligence-Designer**und wählen **Integration Services-Designer**aus.  
  
## <a name="options"></a>Optionen  
 **Digitale Signatur beim Laden eines Pakets überprüfen**  
 Wählen Sie diese Option aus, damit [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] die digitale Signatur beim Laden eines Pakets überprüft. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] überprüft nur, ob die digitale Signatur vorhanden und gültig ist und von einer vertrauenswürdigen Quelle stammt. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] überprüft nicht, ob das Paket seit der Signierung geändert wurde.  
  
 Wenn Sie den **BlockedSignatureStates** -Registrierungswert festlegen, überschreibt dieser Registrierungswert die Option **Digitale Signatur beim Laden eines Pakets überprüfen** . Weitere Informationen finden Sie unter [Implementieren einer Signaturrichtlinie durch Festlegen eines Registrierungswerts](implement-a-signing-policy-by-setting-a-registry-value.md).  
  
 Weitere Informationen zu digitalen Zertifikaten und Paketen finden Sie unter [Identifizieren der Quelle von Paketen mit digitalen Signaturen](security/identify-the-source-of-packages-with-digital-signatures.md).  
  
 **Warnung anzeigen, wenn ein Paket nicht signiert ist**  
 Wählen Sie diese Option aus, wenn beim Laden eines unsignierten Pakets eine Warnung angezeigt werden soll.  
  
 **Bezeichnungen für Rangfolgeneinschränkungen anzeigen**  
 Wählen Sie aus, welche Bezeichnung – Success, Failure oder Completion (Erfolg, Fehler oder Beendet) – bei Rangfolgeneinschränkungen angezeigt werden soll, wenn Sie Pakete in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] anzeigen.  
  
 **"Skriptsprache"**  
 Wählen Sie die Standardskriptsprache für neue Skripttasks und Skriptkomponenten aus.  
  
 **Verbindungszeichenfolgen zum Verwenden neuer Anbieternamen aktualisieren**  
 Wenn Sie [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] -Pakete öffnen oder aktualisieren, werden die Verbindungszeichenfolgen für die aktuelle Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]dahingehend aktualisiert, dass sie die Namen für die folgenden Anbieter verwenden:  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] OLE DB-Anbieter  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client  
  
 Der [!INCLUDE[ssIS](../includes/ssis-md.md)] -Paketupgrade-Assistent aktualisiert nur Verbindungszeichenfolgen, die in Verbindungs-Managern gespeichert sind. Der Assistent aktualisiert keine Verbindungszeichenfolgen, die dynamisch mithilfe der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Ausdruckssprache oder mithilfe von Code in einem Skripttask erstellt wurden.  
  
 **Neue Paket-ID erstellen**  
 Erstellen Sie beim Upgrade von [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] -Paketen neue Paket-IDs für die aktualisierten Versionen der Pakete.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsübersicht &#40;Integration Services&#41;](security/security-overview-integration-services.md)   
 [Erweitern von Paketen mit Skripts](extending-packages-scripting/extending-packages-with-scripting.md)  
  
  
