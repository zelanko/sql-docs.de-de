---
title: Reference Data Services in DQS
ms.date: 10/01/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ef217717-6d05-443e-af26-44dc745a349d
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 6d3c4f15dcb62e36918c81baa5f2bd40c38b7c6a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75244138"
---
# <a name="reference-data-services-in-dqs"></a>Reference Data Services in DQS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Verweisdaten beziehen sich auf einen genauen und vollständigen Satz verwandter oder kategorisierter globaler Daten (jenseits der Begrenzungen eines Unternehmens), die auf vertrauenswürdigen öffentlichen Domänen oder von erstklassigen kommerziellen Inhaltsanbietern verfügbar sind.  
  
 Die Funktion Reference Data Service in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) ermöglicht es Ihnen, Reference Data Service-Drittanbieter zu abonnieren und Ihre Geschäftsdaten durch das Überprüfen gegen hochwertige Daten dieser Anbieter leicht zu bereinigen und zu erweitern. Sie können Dienste von führenden Data Quality Service-Anbietern innerhalb von DQS verwenden, um Ihre Daten während des Bereinigungsprozesses zu standardisieren, zu korrigieren und zu erweitern. Sie können z. B. eine Liste mit Postleitzahlen gegen die Verweisdaten abgleichen, um Adressen Ihrer Kunden zu überprüfen.  
  
 Die Funktion Reference Data Service hat die folgenden Vorteile:  
  
-   Verweisdaten ermöglichen es Ihnen, die Qualität der Daten sicherzustellen, indem Sie sie mit den garantierten Daten eines Drittanbieters vergleichen.  
  
-   Der Verweisdatenprozess wird in die Erstellung einer DQS-Wissensdatenbank und in ein Data Quality-Projekt integriert und ermöglicht es Ihnen, einen umfassenden Data Quality-Prozess einzuführen.  
  
-   Unterstützt die Verwendung von Verweis Daten sowohl aus Azure Marketplace als auch direkt von Verweis Datenanbietern von Drittanbietern.  
  
##  <a name="Marketplace"></a>Verwenden von Verweis Daten aus Azure Marketplace  
 DQS unterstützt das Verwenden von Verweis Daten aus Azure Marketplace, damit Inhaltsanbieter Verweis Datendienste über den Marketplace bereitstellen können. Marketplace ist ein Dienst von Microsoft, der einen Marketplace und einen Bereitstellungskanal für hochwertige Daten und Anwendungen als Clouddienste bereitstellt. Weitere Informationen zum Marketplace finden Sie unter Informationen [zu Microsoft Azure Marketplace](https://azuremarketplace.microsoft.com/about) (https://azuremarketplace.microsoft.com/about)).
  
 Die nahtlose Integration zwischen Marketplace und DQS vereinfacht die Schritte, die für das Ermitteln, Untersuchen und Abrufen von Informationen für Data Quality-Projekte innerhalb von DQS erforderlich sind. Die Daten werden von DQS genutzt und helfen DQS-Benutzern dabei, eine hohe Datenqualität durch das Kombinieren von DQS, Marketplace und Verweisdaten-Dienstanbietern auf innovative Weise zu erreichen.  
  
 Um Verweisdaten vom Marketplace in DQS für die Bereinigungsaktivität zu verwenden, müssen Sie über einen Marketplace-Kontoschlüssel verfügen. Das Erstellen eines Marketplace-Kontoschlüssels ist kostenlos. Sie bezahlen nur, wenn Sie kostenpflichtige Datasets abonnieren. Kostenlose Datasets können ohne anfallende Gebühren abonniert und verwendet werden. Ausführliche Informationen zum Erstellen eines Marketplace-Konto Schlüssels finden [Sie unter Erstellen Ihres Kontos](https://go.microsoft.com/fwlink/?LinkId=212936) (https://go.microsoft.com/fwlink/?LinkId=212936)).  
  
 Darüber hinaus können Sie die folgenden Marketplace-Aktivitäten innerhalb von DQS ausführen:  
  
-   Durchsuchen von Datasets im Marketplace  
  
-   Erstellen eines Marketplace-Kontoschlüssels  
  
-   Verwalten Ihrer Marketplace-Kontodetails, wie z. B. Kontoschlüssel und Abonnements für Datenanbieter  
  
 Sie können diese Aktivitäten auf der Registerkarte **Verweisdaten** des Bildschirms **Konfiguration** in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]ausführen.  
  
##  <a name="Direct"></a>Verwenden von Verweis Daten direkt aus den Verweis Datenanbietern von Drittanbietern  
 Wenn Sie nicht mit dem Internet verbunden sind und daher keinen Marketplace verwenden können, unterstützt DQS auch die direkte Verbindung zu Datenanbietern, die innerhalb des Netzwerks Ihrer Organisation verfügbar sind. Um Verweisdaten von direkten Reference Data Service-Onlinedrittanbietern zu verwenden, müssen Sie in DQS einen Datensatz für den Datenanbieter erstellen.  
  
##  <a name="HowToCleanse"></a>Bereinigen von Daten mithilfe der Verweis Daten  
 Das Bereinigen der Daten in DQS mithilfe von Verweisdaten umfasst die folgenden drei Schritte:  
  
1.  Konfigurieren **der Verweis Datenanbieter Details in DQS**: bevor Sie Verweis Daten in DQS verwenden können, müssen Sie Verweis Datendienst Details in DQS konfigurieren.  
  
    1.  Wenn Sie Marketplace verwenden, geben Sie einen gültigen Marketplace-Kontoschlüssel an, navigieren Sie im Marketplace zur Kategorie [Data Services](https://azuremarketplace.microsoft.com/marketplace/apps/category/azure-active-directory-apps?page=1&subcategories=data-services) Daten, und abonnieren Sie die erforderlichen Anbieter.  
  
    2.  Wenn Sie einen direkten Onlineverweisdatenanbieter verwenden, müssen Sie direkte Verweisdatenanbieterdetails in DQS hinzufügen, bevor Sie den Anbieter verwenden können.  
  
     Das Konfigurieren der Verweisdatenanbieterdetails in DQS muss für jeden Datenanbieter nur ein Mal erfolgen. Nur DQS-Administratoren können Verweisdateneinstellungen in DQS konfigurieren.  
  
2.  Ordnen **Sie eine Domäne/Verbund Domäne in einer Wissensdatenbank dem Verweis Datendienst zu**: Ordnen Sie eine Domäne/Verbund Domäne dem entsprechenden Verweis Datendienst zu, den Sie in Schritt 1 abonniert/hinzugefügt haben.  
  
3.  **Verwenden Sie die zugeordneten Domänen für die Bereinigungs Aktivität in einem Data Quality-Projekt**: Wählen Sie **während der Erstellung** eines Data Quality-Projekts für die Bereinigungs Aktivität die Wissensdatenbank aus, die Domänen/Verbund Domänen enthält, die in Schritt 2 den Verweis Datendiensten zugeordnet sind, und führen Sie  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt, wie DQS zum Verwenden von Verweisdatendiensten vom Marketplace oder von direkten Reference Data Service-Onlinedrittanbietern konfiguriert wird.|[Konfigurieren von DQS zum Verwenden von Verweisdaten](../data-quality-services/configure-dqs-to-use-reference-data.md)|  
|Beschreibt, wie einem Verweisdatendienst eine Domäne/Verbunddomäne in einer Wissensdatenbank zugeordnet wird.|[Anfügen einer Domäne oder Verbunddomäne an Verweisdaten](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md)|  
|Beschreibt, wie Daten mithilfe des Verweisdatendienstes bereinigt werden.|[Bereinigen von Daten mit Verweis Daten &#40;externen&#41; Kenntnissen](../data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)|  
  
  
