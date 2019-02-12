---
title: Erstellen und Verwalten von freigegebenen Datenquellen (Reporting Services im integrierten SharePoint-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], shared data sources
- shared data sources [Reporting Services]
ms.assetid: 2d3428e4-a810-4e66-a287-ff18e57fad76
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 3253c8c13b950f661ee7ddc7925aac19221d3173
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56011181"
---
# <a name="create-and-manage-shared-data-sources-reporting-services-in-sharepoint-integrated-mode"></a>Erstellen und Verwalten von freigegebenen Datenquellen (Reporting Services im integrierten SharePoint-Modus)
  Beim Ausführen eines Berichts aus einer SharePoint-Bibliothek können die Verbindungsinformationen innerhalb des Berichts oder in einer externen Datei definiert werden, die mit dem Bericht verknüpft ist. Falls die Verbindungsinformationen in den Bericht eingebettet sind, wird die Datenquelle als benutzerdefinierte Datenquelle bezeichnet. Sind die Verbindungsinformationen in einer externen Datei definiert, wird sie als freigegebene Datenquelle bezeichnet. Bei der externen Datei kann es sich um eine RSDS-Datei (Report Server Data Source, Berichtsserver-Datenquellendatei) oder um eine Office Data Connection-Datei (ODC-Datei) handeln.  
  
 Eine RSDS-Datei ist mit einer RDS-Datei vergleichbar, aber sie weist ein anderes Schema auf. Zum Erstellen einer RSDS-Datei können Sie eine RDS-Datei aus dem Berichts-Designer oder dem Modell-Designer in einer SharePoint-Bibliothek veröffentlichen (aus der ursprünglichen RDS-Datei wird eine neue RSDS-Datei erstellt). Alternativ können Sie eine neue Datei in einer Bibliothek auf einer SharePoint-Website erstellen.  
  
 Nachdem Sie eine freigegebene Datenquelle erstellt oder veröffentlicht haben, können Sie die Verbindungseigenschaften bearbeiten oder die Datei löschen, wenn sie nicht mehr verwendet wird. Bevor Sie eine freigegebene Datenquelle löschen, sollten Sie bestimmen, ob sie von Berichten oder Berichtsmodellen verwendet wird. Zeigen Sie dazu abhängige Elemente an, die auf die freigegebene Datenquelle verweisen.  
  
 Obwohl Sie in der Liste der abhängigen Elemente Informationen erhalten, ob auf die freigegebene Datenquelle verwiesen wird, erfahren Sie nicht, ob sie aktiv verwendet wird. Um zu bestimmen, ob die freigegebene Datenquelle oder das Modell aktiv verwendet wird, können Sie die Protokolldateien auf dem Berichtsservercomputer überprüfen. Wenn Sie keinen Zugriff auf die Protokolldateien haben oder wenn die Dateien die gewünschten Informationen nicht enthalten, können Sie den Bericht während der Statusbestimmung in einen Ordner verschieben, auf den kein Zugriff besteht.  
  
### <a name="to-create-a-shared-data-source-rsds-file-sharepoint-2010"></a>So erstellen Sie eine freigegebene Datenquellendatei (RSDS-Datei) in Sharepoint 2010  
  
1.  Klicken Sie auf dem Bibliothekmenüband auf die Registerkarte **Dokumente** .  
  
2.  Klicken Sie im Menü **Neues Dokument** auf **Berichtsdatenquelle**.  
  
    > [!NOTE]  
    >  Wenn das Element **Berichtsdatenquelle** nicht im Menü angezeigt wird, wurde der Inhaltstyp für Berichtsdatenquellen noch nicht aktiviert. Weitere Informationen finden Sie unter [hinzufügen Berichtsserver-Inhaltstypen zu einer Bibliothek &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).  
  
3.  Geben Sie unter **Name**einen beschreibenden Namen für die RSDS-Datei ein.  
  
4.  Wählen Sie unter **Datenquellentyp**den Datenquellentyp aus der Liste aus. Weitere Informationen finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
5.  Geben Sie unter **Connection String**einen Zeiger auf die Datenquelle und alle anderen Einstellungen an, die zum Herstellen einer Verbindung mit der externen Datenquelle erforderlich sind. Die Syntax der Verbindungszeichenfolge wird durch den von Ihnen verwendeten Datenquellentyp bestimmt. Weitere Informationen und Beispiele finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
6.  Geben Sie in **Anmeldeinformationen**an, wie der Berichtsserver Anmeldeinformationen für den Zugriff auf die externe Datenquelle erhält. Anmeldeinformationen können für die unbeaufsichtigte Berichtsverarbeitung gespeichert, angefordert, integriert oder konfiguriert werden.  
  
    -   Wählen Sie **Windows-Authentifizierung (integriert)** aus, wenn der Zugriff auf die Daten mit den Anmeldeinformationen des Benutzers erfolgen soll, der den Bericht geöffnet hat. Wählen Sie diese Option nicht aus, wenn für die SharePoint-Website oder -Farm die Formularauthentifizierung verwendet oder über ein vertrauenswürdiges Konto eine Verbindung mit dem Berichtsserver hergestellt wird. Wählen Sie diese Option nicht aus, wenn Sie eine Abonnement- oder Datenverarbeitung für diesen Bericht planen möchten. Diese Option kann am besten verwendet werden, wenn die Kerberos-Authentifizierung für die Domäne aktiviert ist oder wenn sich die Datenquelle auf demselben Computer wie der Berichtsserver befindet. Wenn die Kerberos-Authentifizierung nicht aktiviert ist, können die Windows-Anmeldeinformationen nur an einen anderen Computer weitergegeben werden. Dies bedeutet, dass statt der erwarteten Daten ein Fehler angezeigt wird, wenn sich die externe Datenquelle auf einem anderen Computer befindet, für den eine zusätzliche Verbindung erforderlich ist.  
  
    -   Wählen Sie **Zur Eingabe der Anmeldeinformationen auffordern** aus, wenn der Benutzer die Anmeldeinformationen bei jeder Ausführung des Berichts eingeben soll. Wählen Sie diese Option nicht aus, wenn Sie eine Abonnement- oder Datenverarbeitung für diesen Bericht planen möchten.  
  
    -   Wählen Sie **Gespeicherte Anmeldeinformationen** aus, wenn der Zugriff auf die Daten mit einem einzigen Satz Anmeldeinformationen erfolgen soll. Die Anmeldeinformationen werden vor der Speicherung verschlüsselt. Sie können Optionen auswählen, die bestimmen, wie die gespeicherten Anmeldeinformationen authentifiziert werden. Wählen Sie Windows-Anmeldeinformationen verwenden aus, wenn die gespeicherten Anmeldeinformationen zu einem Windows-Benutzerkonto gehören. Wählen Sie **Ausführungskontext für dieses Konto festlegen** aus, wenn Sie den Ausführungskontext auf dem Datenbankserver festlegen möchten. Bei [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbanken kann mit dieser Option die SETUSER-Funktion festgelegt werden. Weitere Informationen finden Sie unter [SETUSER (Transact-SQL)](/sql/t-sql/statements/setuser-transact-sql).  
  
    -   Wählen Sie **Anmeldeinformationen sind nicht erforderlich** aus, wenn Sie Anmeldeinformationen in der Verbindungszeichenfolge angeben möchten oder wenn Sie den Bericht mithilfe eines Kontos mit Minimalprivilegien ausführen möchten, das auf dem Berichtsserver konfiguriert ist. Ist das Konto nicht auf dem Berichtsserver konfiguriert, werden die Anmeldeinformationen von den Benutzern angefordert, und geplante Vorgänge, die Sie für den Bericht definieren, werden nicht ausgeführt.  
  
7.  Wählen Sie **Diese Datenquelle aktivieren** aus, wenn die Datenquelle aktiviert sein soll. Wenn die Datenquelle konfiguriert aber nicht aktiv ist, wird Benutzern beim Versuch, einen Bericht auf Grundlage der Datenquelle zu verwenden, eine Fehlermeldung angezeigt.  
  
8.  Klicken Sie auf die Schaltfläche **Verbindung testen** , um die Datenquellenkonfiguration zu überprüfen.  
  
    > [!NOTE]  
    >  Die Schaltfläche zum Testen der Verbindung wird für den XML-Datenquellentyp nicht unterstützt.  
  
9. Klicken Sie auf **OK** , um die freigegebene Datenquelle zu speichern.  
  
### <a name="to-view-dependent-items"></a>So zeigen Sie abhängige Elemente an  
  
1.  Öffnen Sie die Bibliothek, die die RSDS-Datei enthält.  
  
2.  Zeigen Sie auf die freigegebene Datenquelle.  
  
3.  Klicken Sie, um einen Pfeil nach unten anzuzeigen, und wählen Sie **Abhängige Elemente anzeigen**aus.  
  
     Für Berichtsmodelle enthält die Liste der abhängigen Elemente die Berichte, die im Berichts-Generator erstellt wurden. Bei freigegebenen Datenquellen kann die Liste der abhängigen Elemente sowohl Berichte als auch Berichtsmodelle enthalten.  
  
### <a name="to-delete-a-shared-data-source-rsds-file"></a>So löschen Sie eine freigegebene Datenquellendatei (RSDS-Datei)  
  
1.  Öffnen Sie die Bibliothek, die die RSDS-Datei enthält.  
  
2.  Zeigen Sie auf die freigegebene Datenquelle.  
  
3.  Klicken Sie, um einen Pfeil nach unten anzuzeigen, und klicken Sie auf **Löschen**.  
  
 Wenn Sie versehentlich eine freigegebene Datenquelle löschen, die beibehalten werden sollte, können Sie eine neue Datenquelle mit denselben Verbindungsinformationen erstellen. Nachdem Sie die freigegebene Datenquelle erneut erstellt haben, müssen Sie jeden Bericht und jedes Berichtsmodell, von dem diese Datenquelle verwendet wurde, öffnen und die freigegebene Datenquelle auswählen. Der Name, die Anmeldeinformationen und die Syntax der Verbindungszeichenfolge des neuen freigegebenen Datenquellenelements müssen nicht mit denen des gelöschten übereinstimmen. Solange die Verbindung zur selben Datenquelle aufgelöst wird, können Datenquelleneigenschaften von den ursprünglichen Werten abweichen.  
  
 Gehen Sie beim Löschen eines Berichtsmodells umsichtig vor. Wenn Sie ein Modell löschen, können Sie die Berichte, die auf diesem Modell im Berichts-Generator basieren, nicht mehr öffnen und ändern. Wenn Sie versehentlich ein Modell löschen, das von vorhandenen Berichten verwendet wird, müssen Sie das Modell erneut generieren, alle Berichte, von denen das Modell verwendet wird, erneut erstellen und speichern und die zu verwendende Modellelementsicherheit erneut angeben. Es ist nicht möglich, das Modell einfach neu zu generieren und es anschließend einem vorhandenen Bericht anzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  
