---
title: Identifizieren Sie die richtige Azure SQL-Datenbank-SKU für Ihre lokale Datenbank (Data Migration Assistant) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Data Migration Assistant mit um der rechten Seite Azure SQL-Datenbank-SKU für Ihre lokale Datenbank zu identifizieren.
ms.custom: ''
ms.date: 05/06/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 1ea0afb015bb457b067f1011bd3b602bf4142e09
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65106083"
---
# <a name="identify-the-right-azure-sql-databasemanaged-instance-sku-for-your-on-premises-database"></a>Identifizieren Sie das Recht Azure SQL-Datenbank/verwaltete Instanz SKU für Ihre lokale Datenbank

Migrieren von Datenbanken in die Cloud können kompliziert, sein, insbesondere, wenn versucht wird, die beste Azure-Datenbank-Ziel und die SKU für Ihre Datenbank auszuwählen. Unser Ziel mit der Database Migration Assistant (DMA) ist, können Sie diese Fragen zu beheben, und stellen Ihre Datenbankmigration, die durch die Bereitstellung dieser SKU-Empfehlungen in einer benutzerfreundlichen Ausgabe erleichtern.

Dieser Artikel konzentriert sich auf DMAs-Azure SQL-Datenbank-SKU-Empfehlungen-Funktion. Azure SQL-Datenbank verfügt über mehrere Bereitstellungsoptionen zur Verfügung, einschließlich:

- Einzeldatenbank
- Pools für elastische Datenbanken
- verwaltete Instanz

Die Funktion, die Sie sowohl den empfohlenen Azure SQL-einzeldatenbanken identifizieren kann die SKU-Empfehlungen oder die verwaltete Instanz abhängig von den Computern, auf dem Ihre Datenbanken gehostet erfassten Leistungsindikatoren von SKU. Das Feature bietet Empfehlungen in Bezug auf Preise, Ebenen, computeebene, maximale Datengröße, sowie und geschätzte Kosten pro Monat. Darüber hinaus die Möglichkeit, einzelne Bulk Bereitstellen von Datenbanken und verwaltete Instanzen in Azure für alle empfohlenen Datenbanken.

> [!NOTE]
> Diese Funktion ist derzeit nur über die Befehlszeilenschnittstelle (CLI) verfügbar.

Im folgenden werden die Anweisungen, um die Ihnen helfen, bestimmen die Azure SQL-Datenbank-SKU-Empfehlungen und die entsprechenden einzelne Datenbanken oder verwaltete Instanzen in Azure unter Verwendung von DMA bereitstellen.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Herunterladen und installieren Sie die neueste Version des [DMA](https://aka.sm/get-dma). Wenn Sie bereits eine frühere Version des Tools verfügen, öffnen Sie sie aus, und werden Sie aufgefordert, DMA aktualisieren.
- Stellen Sie sicher, dass Ihr Computer verfügt über [PowerShell Version 5.1](https://www.microsoft.com/download/details.aspx?id=54616) oder höher, das Ausführen aller Skripts erforderlich ist. Informationen zu Findoug, welche Version von PowerShell auf Ihrem Computer installiert ist, finden Sie im Artikel [herunterladen und installieren Sie Windows PowerShell 5.1](https://docs.microsoft.com/skypeforbusiness/set-up-your-computer-for-windows-powershell/download-and-install-windows-powershell-5-1).
- Stellen Sie sicher, dass Ihr Computer über das Azure Powershell-Modul installiert verfügt. Weitere Informationen finden Sie im Artikel [Installieren des Azure PowerShell-Moduls](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-1.8.0).
- Überprüfen Sie, ob die PowerShell-Datei **SkuRecommendationDataCollectionScript.ps1**, die erforderlich ist, um das Erfassen der Leistungsindikatoren im Ordner "DMA" installiert ist.
- Stellen Sie sicher, dass der Computer, die auf dem Sie diesen Prozess durchführen, müssen über Administratorberechtigungen auf dem Computer verfügt, die Ihre Datenbanken gehostet werden.

## <a name="collect-performance-counters"></a>Erfassen von Leistungsindikatoren

Der erste Schritt im Prozess wird zum Sammeln von Leistungsindikatoren für Ihre Datenbanken. Sie können Leistungsindikatoren sammeln, durch Ausführen eines PowerShell-Befehls auf dem Computer, der Ihre Datenbanken hostet. DMA bietet Ihnen eine Kopie dieses PowerShell-Datei, aber Sie können auch eine eigene Methode verwenden, um die Leistungsindikatoren auf Ihrem Computer zu aufzeichnen.

Sie müssen diese Aufgabe einzeln für jede Datenbank ausführen. Auf einem Computer erfassten Leistungsindikatoren können verwendet werden, empfehlen die SKU für alle Datenbanken auf dem Computer gehostet wird.

1. Suchen Sie im Ordner "DMA" die PowerShell-Datei SkuRecommendationDataCollectionScript.ps1 aus. Diese Datei ist erforderlich, um die Leistungsindikatoren erfassen.

    ![PowerShell-Datei, die im Ordner "DMA" angezeigt](../dma/media/dma-sku-recommend-data-collection-file.png)

2. Führen Sie das PowerShell-Skript mit den folgenden Argumenten:
    - **ComputerName**: Der Name des Computers, auf dem Ihre Datenbanken gehostet werden soll.
    - **OutputFilePath**: Pfad der Ausgabedatei um die erfassten Leistungsindikatoren zu speichern.
    - **CollectionTimeInSeconds**: Die Zeitspanne, in dem Sie Leistungsindikatordaten sammeln möchten. Erfassen von Leistungsindikatoren für mindestens 40 Minuten, um eine sinnvolle Empfehlung zu erhalten. Je länger die Dauer der Erfassung, desto genauer sind die empfohlen werden. Stellen Sie außerdem sicher, dass die Workloads ausgeführt werden, für die gewünschten Datenbanken aus, um genauere Empfehlungen zu aktivieren.
    - **DbConnectionString**: Die Verbindungszeichenfolge, die auf die master-Datenbank gehostet wird, auf dem Computer, von dem Sie Leistungsindikatordaten erfassen.

    Hier ist ein Beispielaufruf aus:

    ```
    .\SkuRecommendationDataCollectionScript.ps1
     -ComputerName Foobar1
     -OutputFilePath D:\counters2.csv
     -CollectionTimeInSeconds 2400
     -DbConnectionString "Server=localhost;Initial Catalog=master;Integrated Security=SSPI;"
    ```

    Nachdem der Befehl ausgeführt wurde, gibt der Prozess eine Datei, einschließlich der Leistungsindikatoren auf den Speicherort an, die, den Sie angegeben haben. Sie können als Eingabe für den nächsten Teil des Prozesses, in dem die SKU-Empfehlungen für einzeldatenbanken und Optionen für verwaltete Instanzen enthalten sind, diese Datei verwenden.

## <a name="use-the-dma-cli-to-get-sku-recommendations"></a>Verwenden der DMA-CLI zum Abrufen von SKU-Empfehlungen

Verwenden Sie die Leistung Leistungsindikatoren Ausgabedatei, die Sie als Eingabe für diesen Prozess erstellt haben.

Für die einzelnen Datenbank-Option bietet DMA Empfehlungen für die einzelnen Azure SQL-Datenbank-Datenbank Preise Tarif der computeebene und die maximale Datengröße für jede Datenbank auf Ihrem Computer. Wenn Sie mehrere Datenbanken auf Ihrem Computer verfügen, können Sie auch die Datenbanken angeben, für die Empfehlungen werden soll. DMA wird auch Sie die geschätzten monatlichen Kosten für jede Datenbank bereitstellen.

Für die verwaltete Instanz unterstützen die Empfehlungen für ein per Lift & Shift-Szenario. Daher wird Sie DMA mit Empfehlungen für die verwaltete Azure SQL-Datenbank-Instanz, Tarif, der computeebene, und die maximale Datengröße für die Gruppe von Datenbanken auf Ihrem Computer bereitstellen. In diesem Fall, wenn Sie über mehrere Datenbanken auf Ihrem Computer verfügen, können Sie auch die Datenbanken angeben für die Empfehlungen werden soll. DMA wird auch Sie die geschätzten monatlichen Kosten für die verwaltete Instanz bereitstellen.

Um die DMA-CLI verwenden, um SKU-Empfehlungen, an der Eingabeaufforderung zu erhalten, führen Sie dmacmd.exe mit den folgenden Argumenten aus:

- **/Action=SkuRecommendation**: Geben Sie dieses Argument zum Ausführen von SKU-Bewertungen.
- **/SkuRecommendationInputDataFilePath**: Der Pfad zur Leistungsindikatordatei erfasst, im vorherigen Abschnitt.
- **/SkuRecommendationTsvOutputResultsFilePath**: Der Pfad zu die Ausgeben von Ergebnissen im TSV-Format zu schreiben.
- **/SkuRecommendationJsonOutputResultsFilePath**: Der Pfad zu die Ausgabeergebnisse im JSON-Format zu schreiben.
- **/SkuRecommendationHtmlResultsFilePath**: Pfad zu die Ausgeben von Ergebnissen im HTML-Format zu schreiben.

Außerdem wählen Sie eine der folgenden Argumente:

- Zu verhindern, dass Price-Aktualisierung
  - **/SkuRecommendationPreventPriceRefresh**: Wenn auf "true" festgelegt, wird verhindert, dass die Preis-Aktualisierung auftreten und geht davon aus Standardpreise. Verwenden Sie, wenn im offline-Modus ausgeführt wird. Wenn Sie diesen Parameter nicht verwenden, müssen Sie die Parameter unten, um den aktuellen Preisen basierend auf eine bestimmte Region angeben.
- Die aktuellen Preisen zu erhalten
  - **/SkuRecommendationCurrencyCode**: Die Währung, in dem Preise angezeigt werden (z.B.) "USD").
  - **/SkuRecommendationOfferName**: Das Angebot benennen (z.B.) "MS-AZR-0003P"). Weitere Informationen finden Sie unter den [Microsoft Azure-Angebotsdetails](https://azure.microsoft.com/support/legal/offer-details/) Seite.
    - **/SkuRecommendationRegionName**: Der Regionsname (z. B. "USA, Westen").
    - **/SkuRecommendationSubscriptionId**: Die Abonnement-ID.
    - **/AzureAuthenticationTenantId**: Die Authentication-Mandant.
    - **/AzureAuthenticationClientId**: Die Client-ID der AAD-app für die Authentifizierung verwendet werden soll.
    - Eine der folgenden Authentifizierungsoptionen:
      - Interaktiv
        - **AzureAuthenticationInteractiveAuthentication**: Auf "true" für ein Popupfenster Authentifizierung festgelegt ist.
      - Zertifikatbasiert
        - **AzureAuthenticationCertificateStoreLocation**: Legen Sie auf den Speicherort des Zertifikats (z. B. "CurrentUser").
        - **AzureAuthenticationCertificateThumbprint**: Legen Sie auf den Fingerabdruck des Zertifikats.
      - Token-basierte
        - **AzureAuthenticationToken**: Legen Sie auf das Zertifikatstoken.

> [!NOTE]
> Rufen Sie die Client-ID und die Mandanten-ID für die interaktive Authentifizierung müssen Sie eine neue AAD-Anwendung zu konfigurieren. Weitere Informationen zur Authentifizierung und Abrufen dieser Anmeldeinformationen in diesem Artikel [Microsoft Azure Billing-API-Codebeispielen: RateCard-API](https://azure.microsoft.com/resources/samples/billing-python-ratecard-api/), befolgen Sie die Anweisungen unter **Schritt 1: Konfigurieren Sie eine systemeigene Clientanwendung in Ihrem AAD-Mandanten**.

Es ist schließlich ein optionales Argument, die, das Sie verwenden können, zum Angeben der Datenbanken für die Empfehlungen werden soll: 

- **/SkuRecommendationDatabasesToRecommend**: Eine Liste der Datenbanken für die sich Empfehlungen erstellen lassen. Die Datenbank Namen Groß-/Kleinschreibung beachtet werden müssen (1) finden Sie in der CSV-Eingabedateien, (2) jede durch doppelte Anführungszeichen eingeschlossen sein und (3) jeweils durch ein Leerzeichen zwischen Namen getrennt werden (z. B. /SkuRecommendationDatabasesToRecommend "Database1" = "" database2 "" "Database3") . Das Auslassen dieses Parameters stellen Sie sicher, dass Empfehlungen für alle Benutzerdatenbanken, die in der Datei für die CSV-Eingabedateien angegebenen bereitgestellt werden.  

Im folgenden sind einige Beispiel-Aufrufe:

**Beispiel 1: Abrufen von Empfehlungen mit Standard-Preisen. Verwenden Sie bei der Ausführung im Offlinemodus befindet oder wenn Sie keine Anmeldeinformationen für die Authentifizierung verfügen.**

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true
```

**Beispiel 2: Dient zum Abrufen von Empfehlungen mit aktuellen Preisen für den angegebenen Bereich (z. B. "UKWest").**

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationInteractiveAuthentication=true
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
```

**Beispiel 3: Abrufen von Empfehlungen für bestimmte Datenbanken (z.B.) “TPCDS1G,EDW_3G,TPCDS10G”).**

```
.\DmaCmd.exe /Action=SkuRecommendation 
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv" 
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv" 
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json" 
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html" 
/SkuRecommendationCurrencyCode=USD 
/SkuRecommendationOfferName=MS-AZR-0044p 
/SkuRecommendationRegionName=UKWest 
/SkuRecommendationSubscriptionId=<Your Subscription Id> 
/SkuRecommendationDatabasesToRecommend=“TPCDS1G” “EDW_3G” “TPCDS10G” 
/AzureAuthenticationInteractiveAuthentication=true 
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId> 
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
```

Einzeldatenbank Empfehlungen wird die TSV-Ausgabedatei wie folgt aussehen:

![PowerShell-Single-Db-Datei im Ordner "DMA" angezeigt](../dma/media/dma-sku-recommend-single-db-recommendations.png)

Für die verwaltete Instanz Recommendations wird die TSV-Ausgabedatei wie folgt aussehen:

![PowerShell-verwaltete Instanz-Datei im Ordner "DMA" angezeigt](../dma/media/dma-sku-recommend-mi-recommendations.png)

Eine Beschreibung der einzelnen Spalten in der Ausgabedatei folgt.

- **DatabaseName** -der Name der Datenbank.
- **MetricType** -Tier-empfohlen, Azure SQL-Datenbank einzelnen Datenbank/verwaltete Instanz.
- **MetricValue** -SKU-Azure SQL-Datenbank empfohlen, einzelne Datenbank/verwaltete Instanz.
- **PricePerMonth** – die geschätzte Preis pro Monat für die entsprechende SKU.
- **RegionName** – der Name der Region für die entsprechende SKU. 
- **IsTierRecommended** – Wir stellen eine minimale SKU-Empfehlung für jede Ebene. Klicken Sie dann Heuristiken, um zu bestimmen, den richtigen Tarif für Ihre Datenbank angewendet. Dies spiegelt wider, welcher Tarif für die Datenbank empfohlen. 
- **ExclusionReasons** -dieser Wert ist leer, wenn eine Ebene empfohlen wird. Für jede Ebene, die nicht empfohlen, bieten wir die Gründe, warum sie ausgewählt haben, wurde nicht, an.
- **AppliedRules** – eine kurze Notation der Regeln, die angewendet wurden.

Die endgültige empfohlener Tarif (d. h. **MetricType**) und Wert (z. B. **MetricValue**)-gefunden, in denen die **IsTierRecommended** Spalte ist "true" – gibt die Mindest-SKU erforderlich für Ihre Abfragen mit einer Erfolgsrate ähnlich wie Ihre lokalen Datenbanken in Azure ausführen. Für die verwaltete Instanz unterstützt DMA derzeit Empfehlungen für die am häufigsten verwendeten 8vcore zu 40vcore SKUs. Beispielsweise wird ist die empfohlene Mindest-SKU S4 beim Tarif "standard" und dann auf S3 auswählen oder unter dazu führen, dass Abfragen zu einem Timeout oder nicht ausgeführt.

Die HTML-Datei enthält diese Informationen in einem grafischen Format. Es bietet eine benutzerfreundliche Möglichkeit zum Anzeigen der endgültigen Empfehlung aus, und Bereitstellung der nächsten Teils des Prozesses. Weitere Informationen zu der HTML-Ausgabe wird im folgenden Abschnitt.

## <a name="provision-recommended-skus-to-azure"></a>Empfohlene SKUs in Azure bereitstellen

Mit nur wenigen Klicks können Sie die Empfehlungen wurde für das bereitstellen, Ziel-SKUs in Azure, zu denen Sie Ihre Datenbanken migrieren können. Sie können die HTML-Datei verwenden, zur Eingabe der Azure-Abonnement; Auswählen des Tarifs, compute-Ebene und maximale Größe der Daten für Ihre Datenbanken; und generiert ein Skript zum Bereitstellen Ihrer Datenbanken. Sie können dieses Skript mithilfe von PowerShell ausführen.

Können Sie diesen Prozess auf einem einzelnen Computer durchführen, oder Sie können auf mehreren Computern, um zu bestimmen, die SKU-Empfehlungen nach Maß ausführen. DMA erleichtert derzeit eine einfache und skalierbare benutzererfahrung durch die Unterstützung des gesamten Prozesses über die Befehlszeilenschnittstelle.

Geben Sie die Bereitstellungsinformationen, und nehmen Sie Änderungen an die Empfehlungen, aktualisieren Sie die HTML-Datei wie folgt.

**Empfehlungen für einzeldatenbanken**

![Azure SQL-Datenbank-SKU-Empfehlungen-Bildschirm](../dma/media/dma-sku-recommend-single-db-recommendations1.png)

1. Öffnen Sie die HTML-Datei, und geben Sie die folgende Informationen:
    - **Abonnement-ID** – die Abonnement-ID des Azure-Abonnements, die Sie Datenbanken bereitstellen möchten.
    - **Ressourcengruppe** : die Ressourcengruppe, zu dem Sie die Datenbanken bereitstellen möchten. Geben Sie eine Ressourcengruppe, die vorhanden ist.
    - **Region** : die Region, in dem Datenbanken bereitstellen. Stellen Sie sicher, dass Ihr Abonnement die Eintrag Region unterstützt.
    - **Servername** – Azure SQL-Datenbank-Server an, die Datenbanken, die bereitgestellt werden sollen. Wenn Sie einen Servernamen, der nicht vorhanden ist eingeben, wird sie erstellt.
    - **Admin Username** -Admin-Benutzername für den Server.
    - **Administratorkennwort** -das Kennwort für den Server-Administrator. Das Kennwort muss mindestens acht Zeichen und nicht länger als 128 Zeichen lang sein. Das Kennwort muss Zeichen aus drei der folgenden Kategorien enthalten: englische Großbuchstaben, Buchstaben, englische Kleinbuchstaben, Zahlen (0-9) und nicht-alphanumerische Zeichen (!, $, #, % usw..). Das Kennwort darf nicht enthalten, alle oder einen Teil (3 + aufeinander folgenden Buchstaben) aus dem Benutzernamen.

2. Empfehlungen für jede Datenbank, und ändern Sie den Tarif, compute-Ebene und die maximale Datengröße je nach Bedarf. Achten Sie darauf, dass Sie alle Datenbanken deaktivieren, die nicht derzeit bereitgestellt werden sollen.

3. Wählen Sie **Bereitstellung Skript generieren**, speichern Sie das Skript, und führen Sie ihn dann in PowerShell.

    Dieser Prozess sollte alle Datenbanken erstellen, die Sie in der HTML-Seite ausgewählt.

**Für die verwaltete Instanz recommendations**

![Azure SQL-MI-SKU-Empfehlungen-Bildschirm](../dma/media/dma-sku-recommend-mi-recommendations1.png)

1. Öffnen Sie die HTML-Datei, und geben Sie die folgende Informationen:
    - **Abonnement-ID** – die Abonnement-ID des Azure-Abonnements, die Sie Datenbanken bereitstellen möchten.
    - **Ressourcengruppe** : die Ressourcengruppe, zu dem Sie die Datenbanken bereitstellen möchten. Geben Sie eine Ressourcengruppe, die vorhanden ist.
    - **Region** : die Region, in dem Datenbanken bereitstellen. Stellen Sie sicher, dass Ihr Abonnement die Eintrag Region unterstützt.
    - **Instanzname** – die Instanz von Azure verwalteten SQL-Instanz, die Datenbanken migriert werden soll. Der Instanzname darf nur Kleinbuchstaben, Zahlen, und "-", aber nicht beginnen oder enden mit "-" oder mehr als 63 Zeichen lang sein.
    - **Instanzen von Admin Username** : der Administratorbenutzername für die Instanz. Stellen Sie sicher, dass Ihr Anmeldename die folgenden Anforderungen erfüllt: Es ist ein SQL-Bezeichner, und keinen typischen Systemnamen (z. B. Admin, Administrator, sa, Root, Dbmanager, Loginmanager usw.), oder ein integrierter Datenbankbenutzer oder-Rolle (z. B. Dbo, Guest, Public usw.). Stellen Sie sicher, dass Ihr Name keine Leerzeichen, Unicode-Zeichen oder nicht alphabetische Zeichen enthält und dass es nicht mit Zahlen oder Symbolen beginnt. 
    - **Instanzen von Admin-Kennwort** -das Administratorkennwort für die Instanz. Ihr Kennwort muss mindestens 16 Zeichen und nicht länger als 128 Zeichen lang sein. Das Kennwort muss Zeichen aus drei der folgenden Kategorien enthalten: englische Großbuchstaben, Buchstaben, englische Kleinbuchstaben, Zahlen (0-9) und nicht-alphanumerische Zeichen (!, $, #, % usw..). Das Kennwort darf nicht enthalten, alle oder einen Teil (3 + aufeinander folgenden Buchstaben) aus dem Benutzernamen.
    - **Vnet-Name** – die VNet-Name, unter dem die verwaltete Instanz bereitgestellt werden sollen. Geben Sie den Namen einer vorhandenen VNet aus.
    - **Name des Subnetzes** – die Subnetznamen an, die unter dem die verwaltete Instanz bereitgestellt werden sollen. Geben Sie den Subnetnamen einer vorhandenen aus.

2. Empfehlungen für jede Instanz, und ändern Sie den Tarif, die Computeknoten-Ebene und die maximale Datengröße je nach Bedarf. Die Empfehlungen auf 8vcore zu 40vcore SKUs derzeit beschränkt sind, besteht weiterhin die Option zum 64vcore und 80vcore SKUs bereitstellen, falls gewünscht. Achten Sie darauf, dass Sie alle Instanzen deaktivieren, die nicht derzeit bereitgestellt werden sollen.

    Dieser Prozess sollte alle Datenbanken erstellen, die Sie in der HTML-Seite ausgewählt.

    > [!NOTE]
    > Erstellen von verwalteten Instanzen in einem Subnetz (insbesondere bei der ersten) kann mehrere Stunden dauern. Nachdem Sie das Bereitstellungsskript über PowerShell können Sie den Status Ihrer Bereitstellung im Azure-Portal überprüfen.

## <a name="next-step"></a>Nächster Schritt

- Eine vollständige Liste der Befehle für die Ausführung von DMA über die Befehlszeilenschnittstelle, finden Sie im Artikel [ausführen Data Migration Assistant über die Befehlszeile](https://docs.microsoft.com/sql/dma/dma-commandline?view=sql-server-2017).
