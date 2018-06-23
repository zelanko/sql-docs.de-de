---
title: Konfigurieren von Datenquelleneigenschaften für einen Bericht (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data sources [Reporting Services], embedded
ms.assetid: 27af5195-c845-40e0-9a9c-efe569424022
caps.latest.revision: 43
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 61c928862ea4ea46b8422f820addf1c31ef868d4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061315"
---
# <a name="configure-data-source-properties-for-a-report--report-manager"></a>Konfigurieren von Datenquelleneigenschaften für einen Bericht (Berichts-Manager)
  Bei der Ausführung eines Berichts ruft der Berichtsserver Eigenschaftsinformationen ab, um festzulegen, wie die Verbindung mit einer Datenquelle hergestellt werden soll. Dabei werden der Typ der Datenquelle, die Verbindungszeichenfolge sowie Anmeldeinformationen auf den Eigenschaftenseiten für die Datenquelle des veröffentlichten Berichts angegeben. Sie können die Eigenschaften festlegen, um andere Informationen für die Verbindungsherstellung mit der Datenquelle anzugeben als bei der Erstellung des Berichts genannt wurden.  
  
 Alternativ können Sie stattdessen die freigegebene Datenquelle angeben, wenn Sie über eine vordefinierte freigegebene Datenquelle verfügen, in der bereits die gewünschten Verbindungsinformationen festgelegt sind. Klicken Sie zur Verwendung einer freigegebenen Datenquelle auf der Eigenschaftenseite für die Datenquelle des Berichts auf **Eine freigegebene Datenquelle** .  
  
### <a name="to-configure-an-embedded-data-source"></a>So konfigurieren Sie eine eingebettete Datenquelle  
  
1.  Starten Sie [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Navigieren Sie im Berichts-Manager zur Seite **Inhalt** . Navigieren Sie zu dem Bericht, für den Sie eine berichtsspezifische Datenquelle konfigurieren möchten, und öffnen Sie den Bericht.  
  
3.  Klicken Sie auf die Registerkarte **Eigenschaften** . Die Eigenschaftenseite **Allgemein** wird geöffnet.  
  
4.  Klicken Sie auf die Registerkarte **Datenquellen** . Hiermit wird die Eigenschaftenseite der Datenquelle des Berichts aufgerufen.  
  
5.  Klicken Sie auf **Eine benutzerdefinierte Datenquelle** , um Verbindungsinformationen für die Datenquelle innerhalb des Berichts anzugeben.  
  
6.  Geben Sie in der Liste **Verbindungstyp** die Datenverarbeitungserweiterung an, die zum Verarbeiten von Daten aus der Datenquelle verwendet wird.  
  
7.  Geben Sie in das Feld **Verbindungszeichenfolge**die Verbindungszeichenfolge an, die vom Berichtsserver zum Herstellen der Verbindung zur Datenquelle verwendet wird. Es wird empfohlen, dass Sie keine Anmeldeinformationen in der Verbindungszeichenfolge angeben.  
  
     Das folgende Beispiel zeigt eine Verbindungszeichenfolge, mit der eine Verbindung zur lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank hergestellt wird:  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  Geben Sie für **Verbindung herstellen über**an, wie die Anmeldeinformationen bei Ausführung des Berichts abgerufen werden:  
  
    -   Wenn der Benutzer zur Eingabe eines Anmeldenamens und eines Kennworts aufgefordert werden soll, klicken Sie auf **Bereitgestellte Anmeldeinformationen vom Benutzer, der den Bericht ausführt**.  
  
    -   Wenn Sie die Datenquelle mit Berichten verwenden möchten, die Abonnements oder andere geplante Vorgänge (z.B. automatisierte Berichtsverlaufgenerierung) unterstützen, klicken Sie auf **Anmeldeinformationen, die sicher auf dem Berichtsserver gespeichert sind**.  
  
    -   Wenn der Berichtsserver die Anmeldeinformationen des auf den Bericht zugreifenden Benutzers an den Server übergeben soll, der die externe Datenquelle hostet, klicken Sie auf **Integrierte Sicherheit von Windows**. In diesem Fall wird der Benutzer nicht aufgefordert, einen Benutzernamen oder ein Kennwort einzugeben.  
  
    -   Klicken Sie auf **Anmeldeinformationen sind nicht erforderlich**, wenn Sie eine Datenquelle verwenden, die nicht mit Anmeldeinformationen arbeitet (z.B. wenn es sich bei der Datenquelle um eine XML-Datei handelt, auf die vom Dateisystem zugegriffen wird). Diesen Typ Anmeldeinformationen sollten Sie nur dann angeben, wenn er von der Datenquelle unterstützt wird. Wenn Sie diese Option für eine Datenquelle aktivieren, die Authentifizierung erfordert, schlägt die Verbindungsherstellung fehl. Vergewissern Sie sich bei der Auswahl dieser Option, dass Sie das unbeaufsichtigte Ausführungskonto konfigurieren, mit dem der Berichtsserver eine Verbindung zu anderen Computern herstellen kann, um Daten oder Dateien abzurufen, wenn keine Anmeldeinformationen zur Verfügung stehen.  
  
 Weitere Informationen zum Konfigurieren von Anmeldeinformationen finden Sie unter [angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](specify-credential-and-connection-information-for-report-data-sources.md). Weitere Informationen zum Konto für die unbeaufsichtigte Ausführung finden Sie unter [Konfigurieren des unbeaufsichtigten Ausführungskontos (SSRS-Konfigurations-Manager)](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Inhalt der Seite &#40;Berichts-Manager&#41;](../contents-page-report-manager.md)   
 [Neue Datenquelle (Seite, Berichts-Manager)](../new-data-source-page-report-manager.md)   
 [Erstellen, ändern und Löschen von freigegebenen Datenquellen &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md)   
 [Verwalten von Berichtsdatenquellen](manage-report-data-sources.md)   
 [Erstellen, löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Datenquellen-Eigenschaftenseite (Berichts-Manager)](../data-sources-properties-page-report-manager.md)  
  
  