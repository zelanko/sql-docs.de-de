---
title: Allgemein (Eigenschaftenseite) freigegebene Datenquellen (Berichts-Manager) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b344449-6f7c-47d2-a737-972d88c0faf8
caps.latest.revision: 29
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 0a570567691692f008f6f71966b5ee0b01921dab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056881"
---
# <a name="general-properties-page-shared-data-sources-report-manager"></a>Allgemein (Eigenschaftenseite) (Freigegebene Datenquellen, Berichts-Manager)
  Auf der Seite Allgemeine Eigenschaften können Sie Eigenschaften eines freigegebenen Datenquellenelements anzeigen oder ändern. Die von Ihnen an den Eigenschaften vorgenommenen Änderungen gelten für alle Berichte, die auf dieses Element verweisen, sobald Sie auf die Schaltfläche **Anwenden**klicken.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-general-properties-page-for-a-shared-data-source"></a>So öffnen Sie die Seite Allgemeine Eigenschaften für eine freigegebene Datenquelle  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie die freigegebene Datenquelle, für die Sie Eigenschaften anzeigen möchten.  
  
2.  Zeigen Sie auf die Datenquelle, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für die freigegebene Datenquelle geöffnet.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Gibt einen Namen für die freigegebene Datenquelle an, der zum Identifizieren des Elements innerhalb des Berichtsserver-Namespaces verwendet wird.  
  
 **Beschreibung**  
 Stellt Informationen zur freigegebenen Datenquelle bereit. Diese Beschreibung wird auf der Seite Inhalt angezeigt.  
  
 **In Listenansicht ausblenden**  
 Wählen Sie diese Option aus, um die freigegebene Datenquelle für Benutzer auszublenden, die den Listenansichtsmodus im Berichts-Manager verwenden. Der Listenansichtsmodus ist das Standardanzeigeformat beim Durchsuchen der Ordnerhierarchie auf dem Berichtsserver. In der Listenansicht erstrecken sich Namen und Beschreibungen über die Seite. Das alternative Format ist die Detailsansicht. Detailansichten lassen Beschreibungen aus, enthalten jedoch andere Informationen zum Element. Obwohl Sie ein Element in der Listenansicht ausblenden können, kann es in der Detailansicht nicht ausgeblendet werden. Wenn Sie den Zugriff auf ein Element einschränken möchten, müssen Sie eine Rollenzuweisung erstellen.  
  
 **Diese Datenquelle aktivieren**  
 Mit dieser Option können Sie die freigegebene Datenquelle aktivieren oder deaktivieren. Sie können die freigegebene Datenquelle deaktivieren, um die Verarbeitung aller Berichte, Berichtsmodelle und datengesteuerten Abonnements zu verhindern, die auf dieses Element verweisen.  
  
 **Datenquellentyp**  
 Gibt die Datenverarbeitungserweiterung an, die zum Verarbeiten von Daten aus der Datenquelle verwendet wird. Der Berichtsserver enthält datenverarbeitungserweiterungen für [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], Oracle, XML, SAP, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], ODBC- und OLE DB. Weitere Datenverarbeitungserweiterungen können von Drittanbietern zur Verfügung stehen.  
  
 Beachten Sie, dass Sie bei Verwendung von [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] Edition with Advanced Services nur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenquellen auswählen können.  
  
 **Verbindungszeichenfolge**  
 Geben Sie die Verbindungszeichenfolge an, die vom Berichtsserver zum Herstellen der Verbindung mit der Datenquelle verwendet wird. Der Verbindungstyp bestimmt die Syntax, die Sie verwenden sollten. So ist z.B. eine Verbindungszeichenfolge für die XML-Datenverarbeitungserweiterung eine URL zu einem XML-Dokument. In den meisten Fällen gibt eine typische Verbindungszeichenfolge den Datenbankserver und die Datendatei an. Das folgende Beispiel zeigt eine Verbindungszeichenfolge zur Verbindung mit der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] Datenbank:  
  
```  
data source=<a SQL Server instance>;initial catalog=AdventureWorks2012  
```  
  
 **Verbindung herstellen über**  
 Gibt Optionen an, die bestimmen, wie Anmeldeinformationen abgerufen werden.  
  
> [!IMPORTANT]  
>  Falls die Verbindungszeichenfolge Anmeldeinformationen enthält, werden die in diesem Abschnitt festgelegten Optionen und Werte ignoriert. Beachten Sie, dass bei Angabe der Anmeldeinformationen in der Verbindungszeichenfolge die Werte für alle Benutzer, die diese Seite anzeigen, in Klartext angezeigt werden.  
  
 **Bereitgestellte Anmeldeinformationen vom Benutzer den Bericht ausführt**  
 Jeder Benutzer muss einen Benutzernamen und ein Kennwort für den Zugriff auf die Datenquelle eingeben. Sie können den Text der Eingabeaufforderung definieren, in der die Benutzeranmeldeinformationen angefordert werden. Die Standardtextzeichenfolge lautet: "Geben Sie einen Benutzernamen und ein Kennwort für den Zugriff auf die Datenquelle ein".  
  
 Aktivieren Sie das Kontrollkästchen **Als Windows-Anmeldeinformationen verwenden, wenn eine Verbindung mit der Datenquelle hergestellt wird** , wenn es sich bei den durch den Benutzer bereitgestellten Informationen um Anmeldeinformationen der Windows-Authentifizierung handelt. Lassen Sie dieses Kontrollkästchen deaktiviert, wenn Sie die Datenbankauthentifizierung (z. B. die SQL Server-Authentifizierung) verwenden.  
  
 **Anmeldeinformationen sind sicher auf dem Berichtsserver gespeichert.**  
 Speichern Sie einen verschlüsselten Benutzernamen und ein Kennwort in der Berichtsserver-Datenbank. Wählen Sie diese Option aus, um einen Bericht unbeaufsichtigt auszuführen (z. B. Berichte, die durch Zeitpläne initiiert werden oder durch Ereignisse anstelle einer Benutzeraktion). Wenn Sie die Standardsicherheitseinstellungen verwenden, muss der Benutzername ein Windows-Domänenkonto sein. Geben Sie das Konto im folgenden Format: \<Domäne >\\< Benutzername\>. Das von Ihnen angegebene Konto muss über lokale Systemadministratorberechtigungen auf dem Computer verfügen, der die von dem Bericht verwendete Datenquelle hostet.  
  
 Aktivieren Sie das Kontrollkästchen **Als Windows-Anmeldeinformationen verwenden, wenn eine Verbindung mit der Datenquelle hergestellt wird** , wenn es sich bei den Informationen um Anmeldeinformationen der Windows-Authentifizierung handelt. Wählen Sie dieses Kontrollkästchen nicht, wenn Sie die Datenbankauthentifizierung verwenden (z. B. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentifizierung).  
  
 Wenn Sie die Datenbankauthentifizierung verwenden, wählen Sie die Option **Nach dem Herstellen einer Verbindung mit der Datenquelle die Identität des authentifizierten Benutzers annehmen (Verbindung herstellen über)** aus, um die Delegierung von Datenbankanmeldeinformationen zuzulassen. Dies ist jedoch nur möglich, wenn ein Datenbankserver den Identitätswechsel unterstützt. Für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datenbanken, die diese Option wird der SETUSER-Funktion.  
  
 **Integrierte Sicherheit von Windows**  
 Verwenden Sie die Windows-Anmeldeinformationen des aktuellen Benutzers für den Zugriff auf die Datenquelle. Wählen Sie diese Option aus, wenn die für den Zugriff auf die Datenquelle verwendeten Anmeldeinformationen mit denen übereinstimmen, die zum Anmelden an der Netzwerkdomäne verwendet werden. Diese Option kann am besten verwendet werden, wenn Kerberos für die Domäne aktiviert ist oder wenn sich die Datenquelle auf demselben Computer wie der Berichtsserver befindet. Wenn Kerberos nicht aktiviert ist, können die Windows-Anmeldeinformationen an einen anderen Computer weitergegeben werden. Falls weitere Computerverbindungen erforderlich sind, wird eine Fehlermeldung statt der erwarteten Daten zurückgegeben.  
  
 Ein Berichtsserveradministrator kann die Verwendung der integrierten Sicherheit von Windows deaktivieren, um auf Berichtsdatenquellen zugreifen zu können. Wenn dieser Wert ausgegraut ist, ist die Funktion nicht verfügbar.  
  
 Verwenden Sie diese Option nicht, wenn Sie vorhaben, diesen Bericht zu planen oder zu abonnieren. Die geplante oder unbeaufsichtigte Berichtsverarbeitung benötigt Anmeldeinformationen, die ohne Benutzereingaben oder den Sicherheitskontext des aktuellen Benutzers abgerufen werden können. Diese Möglichkeit bieten nur gespeicherte Anmeldeinformationen. Aus diesem Grund hindert Sie der Berichtsserver daran, die Ausführung eines Berichts oder eines Abonnements zu planen, wenn der Bericht für den Anmeldeinformationstyp der integrierten Windows-Sicherheit konfiguriert ist. Wenn Sie diese Option für einen Bericht wählen, der bereits abonniert ist oder geplante Vorgänge aufweist, werden das Abonnement und die geplanten Vorgänge beendet.  
  
 **Anmeldeinformationen sind nicht erforderlich**  
 Geben Sie an, dass keine Anmeldeinformationen für den Zugriff auf die Datenquelle erforderlich sind. Beachten Sie, dass diese Option keine Auswirkungen hat, wenn für die Datenquelle eine Benutzeranmeldung erforderlich ist. Sie sollten diese Option nur auswählen, wenn für die Datenquellenverbindung keine Benutzeranmeldeinformationen erforderlich sind.  
  
 Um diese Option verwenden zu können, müssen Sie vorher das unbeaufsichtigte Ausführungskonto für die Bereitstellung des Berichtsservers konfiguriert haben. Das unbeaufsichtigte Ausführungskonto wird zum Herstellen der Verbindung mit externen Datenquellen verwendet, wenn keine anderen Quellen für Anmeldeinformationen verfügbar sind. Wenn Sie diese Option angeben und das Konto nicht konfiguriert ist, schlägt die Verbindung mit der Berichtsdatenquelle fehl, und der Bericht wird nicht verarbeitet. Weitere Informationen zu diesem Konto finden Sie unter [Konfigurieren des unbeaufsichtigten Ausführungskontos &#40;SSRS-Konfigurations-Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
 **Anwenden**  
 Klicken Sie auf diese Schaltfläche, um die Änderungen zu speichern.  
  
 **Delete**  
 Klicken Sie auf diese Schaltfläche, um die freigegebene Datenquelle zu löschen. Das Löschen einer freigegebenen Datenquelle deaktiviert alle Berichte, Modelle und datengesteuerten Abonnements, die sie verwenden. Um Berichte, Modelle und Abonnements erneut zu aktivieren, müssen Sie alle einzeln öffnen und die entsprechenden Datenquelleneigenschaften so aktualisieren, dass sie eine andere freigegebene Datenquelle verwenden. Für Berichte und Abonnements können Sie Verbindungsinformationen für die Datenquelle als Eigenschaftenwerte der Datenquelle angeben.  
  
 **Verschieben**  
 Klicken Sie auf diese Schaltfläche, um die freigegebene Datenquelle an einen anderen Speicherort im Namespace des Berichtsserverordners zu verschieben.  
  
 **Modell generieren**  
 Klicken Sie auf diese Schaltfläche, um auf der Basis der freigegebenen Datenquelle ein neues Modell zu erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Manager &#40;SSRS im einheitlichen Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Neue Datenquelle (Seite, Berichts-Manager)](../../2014/reporting-services/new-data-source-page-report-manager.md)   
 [Berichts-Manager-F1-Hilfe](../../2014/reporting-services/report-manager-f1-help.md)   
 [Specify Credential and Connection Information for Report Data Sources (Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen)](report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  