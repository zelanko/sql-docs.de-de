---
title: Identifizieren Sie die richtige Azure SQL-Datenbank-SKU für Ihre lokale Datenbank (Data Migration Assistant) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Data Migration Assistant mit um der rechten Seite Azure SQL-Datenbank-SKU für Ihre lokale Datenbank zu identifizieren.
ms.custom: ''
ms.date: 08/18/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 0bd7c1f96bb4ff55a35eda24aa70984e9a359f83
ms.sourcegitcommit: 61212c06b56953ce2e2627d35f7bd69cda786540
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2018
ms.locfileid: "40392569"
---
# <a name="identify-the-right-azure-sql-database-sku-for-your-on-premises-database"></a>Identifizieren Sie die richtige Azure SQL-Datenbank-SKU für Ihre lokale Datenbank

Die Migration Ihrer Datenbanken in der Cloud ist eine kompliziert und zeitaufwendig, im Zusammenhang mit einer Reihe von Variablen. Wählen das richtige Azure Datenbankziel und die SKU für Ihre Datenbank kann eine Herausforderung darstellen. Unser Ziel mit der Database Migration Assistant (DMA) ist, um diese Fragen beantworten und Ihre Datenbankmigration auftreten einfach und effektiv.

Dieser Artikel konzentriert sich hauptsächlich auf DMA Azure SQL-Datenbank-SKU-Empfehlungen Funktion, die Ihnen ermöglicht, identifizieren Sie die empfohlenen Azure SQL-Datenbank-SKU basierend auf Leistungsindikatoren erfasst, die von den Computern, auf dem Ihre Datenbanken gehostet. Dieses Feature bietet Empfehlungen in Bezug auf Preise, Ebenen, computeebene, maximale Datengröße, sowie und geschätzte Kosten pro Monat. Darüber hinaus die Möglichkeit, alle Datenbanken in Azure in einer Massenoperation bereitzustellen.

> [!NOTE] 
> Diese Funktion ist derzeit nur über die Befehlszeilenschnittstelle (CLI) verfügbar. Unterstützung für dieses Feature über die DMA-Benutzeroberfläche wird in einer zukünftigen Version hinzugefügt werden.

Die folgenden Anweisungen können Sie ermitteln, die Azure SQL-Datenbank-SKU-Empfehlungen und zugeordneten Datenbanken in Azure mithilfe von Data Migration Assistant bereitstellen.

## <a name="prerequisites"></a>Erforderliche Komponenten

Herunterladen der Database Migration Assistant v4. 0 oder höher, und installieren Sie es. Wenn Sie bereits haben das Tool installiert haben, schließen und erneut öffnen, und werden Sie aufgefordert, das Tool zu aktualisieren.

## <a name="collect-performance-counters"></a>Erfassen von Leistungsindikatoren

Der erste Schritt im Prozess wird zum Sammeln von Leistungsindikatoren für Ihre Datenbanken. Sie können Leistungsindikatoren sammeln, durch Ausführen eines PowerShell-Befehls auf dem Computer, der Ihre Datenbanken hostet. DMA bietet Ihnen eine Kopie dieses PowerShell-Datei, aber Sie können auch eine eigene Methode verwenden, um die Leistungsindikatoren auf Ihrem Computer zu aufzeichnen.

Sie müssen sich nicht zum Ausführen dieser Aufgabe für jede Datenbank einzeln. Auf einem Computer erfassten Leistungsindikatoren können verwendet werden, empfehlen die SKU für alle Datenbanken auf dem Computer gehostet wird.

> [!IMPORTANT]
> Der Computer, auf dem Sie diesen Befehl ausführen, erfordert Administratorberechtigungen auf dem Computer, auf dem Ihre Datenbanken gehostet.

1. Stellen Sie sicher, dass die PowerShell-Datei erforderlich, um das Erfassen der Leistungsindikatoren im Ordner "DMA" installiert ist.

    ![PowerShell-Datei, die im Ordner "DMA" angezeigt](../dma/media/dma-sku-recommend-data-collection-file.png)

2. Führen Sie das PowerShell-Skript mit den folgenden Argumenten:
    - **ComputerName**: der Name des Computers, der die Datenbanken hostet.
    - **OutputFilePath**: Pfad der Ausgabedatei um die erfassten Leistungsindikatoren zu speichern.
    - **CollectionTimeInSeconds**: die Zeitspanne, in dem Sie Leistungsindikatordaten sammeln möchten.
      Erfassen von Leistungsindikatoren für mindestens 40 Minuten, um eine sinnvolle Empfehlung zu erhalten. Je länger die Dauer der Erfassung, desto genauer sind die empfohlen werden.
    - **DbConnectionString**: die Verbindungszeichenfolge, die auf die master-Datenbank gehostet wird, auf dem Computer, von dem Sie Leistungsindikatordaten sammeln.
     
    Hier ist ein Beispielaufruf aus:

    ```
    .\SkuRecommendationDataCollectionScript.ps1
     -ComputerName Foobar1
     -OutputFilePath D:\counters2.csv
     -CollectionTimeInSeconds 10
     -DbConnectionString "Server=localhost;Initial Catalog=master;Integrated Security=SSPI;"
    ```
    
    Nachdem der Befehl ausgeführt wurde, gibt der Vorgang eine Datei mit Leistungsindikatoren in den Speicherort, die Sie angegeben haben. Diese Datei kann als Eingabe für den SKU-Empfehlungen-Befehl im nächsten Abschnitt verwendet werden.

## <a name="use-the-dma-cli-to-get-sku-recommendations"></a>Verwenden der DMA-CLI zum Abrufen von SKU-Empfehlungen

Verwenden Sie die Leistung Leistungsindikatoren-Ausgabedatei aus dem vorherigen Schritt als Eingabe für diesen Schritt. DMA gibt Empfehlungen für Azure SQL-Datenbank Ihnen Tarif, der computeebene, und die maximale Datengröße für jede Datenbank auf Ihrem Computer. DMA wird auch Sie die geschätzten monatlichen Kosten für jede Datenbank bereitstellen.

Führen Sie die dmacmd.exe mit den folgenden Argumenten:

- **/ Action = SkuRecommendation**: Geben Sie dieses Argument zum Ausführen von SKU-Bewertungen.
- **/ SkuRecommendationInputDataFilePath**: der Pfad zur Leistungsindikatordatei erfasst, im vorherigen Abschnitt.
- **/ SkuRecommendationTsvOutputResultsFilePath**: der Pfad zu die Ausgeben von Ergebnissen im TSV-Format zu schreiben.
- **/ SkuRecommendationJsonOutputResultsFilePath**: der Pfad zu die Ausgabeergebnisse im JSON-Format zu schreiben.
- **/ SkuRecommendationHtmlResultsFilePath**: Pfad, in den Ausgabeergebnissen im HTML-Format geschrieben.

Darüber hinaus müssen Sie eines der folgenden Argumente auswählen:
- Zu verhindern, dass Price-Aktualisierung
    - **/ SkuRecommendationPreventPriceRefresh**: verhindert, dass die Preis-Aktualisierung auftreten. Verwenden Sie, wenn im offline-Modus ausgeführt wird.
- Die aktuellen Preisen zu erhalten 
    - **/ SkuRecommendationCurrencyCode**: die Währung, in dem Preise angezeigt werden (z.B.) "US").
    - **/ SkuRecommendationOfferName**: das Angebot benennen (z.B.) "MS-AZR - 0003P"). Weitere Informationen finden Sie unter den [Microsoft Azure-Angebotsdetails](https://azure.microsoft.com/support/legal/offer-details/) Seite.
    - **/ SkuRecommendationRegionName**: Benennen Sie die Region (z.B.) "USA, Westen").
    - **/ SkuRecommendationSubscriptionId**: die Abonnement-ID.
    - **/ AzureAuthenticationTenantId**: die Authentication-Mandant.
    - **/ AzureAuthenticationClientId**: die Client-ID der AAD-app für die Authentifizierung verwendet.
    - Eine der folgenden Authentifizierungsoptionen:
        - Interaktiv
            - **AzureAuthenticationInteractiveAuthentication**: auf "true" für ein Popupfenster Authentifizierung festgelegt ist.
        - Zertifikatbasiert
            - **AzureAuthenticationCertificateStoreLocation**: Legen Sie auf den Speicherort des Zertifikatspeichers (z.B.) "CurrentUser").
            - **AzureAuthenticationCertificateThumbprint**: Legen Sie auf den Fingerabdruck des Zertifikats.
        - Token-basierte
            - **AzureAuthenticationToken**: auf das Zertifikatstoken festlegen.

Hier sind einige Beispiel-Aufrufe:

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

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true
```

Die TSV-Ausgabedatei enthält die Spalten in der folgenden Abbildung gezeigt:

   ![PowerShell-Datei, die im Ordner "DMA" angezeigt](../dma/media/dma-tsv-file-column.png)

Folgt eine Beschreibung der einzelnen Spalten.

- **DatabaseName** – der Name der Datenbank.
- **"Metricname"** –, und zwar unabhängig davon, ob eine Metrik ausgeführt wurde.
- **MetricType** -Tarif von Azure SQL-Datenbank empfohlen.
- **MetricValue** -SKU für Azure SQL-Datenbank empfohlen.
- **SQLMiEquivalentCores** – Wenn Sie auswählen, um für verwaltete Instanzen in Azure SQL-Datenbank zu wechseln, können Sie diesen Wert verwenden, für die Anzahl von Kernen.
- **IsTierRecommended** – Wir stellen eine minimale SKU-Empfehlung für jede Ebene. Klicken Sie dann Heuristiken, um zu bestimmen, den richtigen Tarif für Ihre Datenbank angewendet. 
- **ExclusionReasons** -dieser Wert ist leer, wenn eine Ebene empfohlen wird. Für jede Ebene, die nicht empfohlen wird, bieten wir die Gründe, warum er nicht ausgewählt wurde.
- **AppliedRules** – eine kurze Notation der Regeln, die angewendet wurden.

Beachten Sie, dass der empfohlene Wert die Mindest-SKU für Ihre Abfragen zum Ausführen in Azure mit einer Erfolgsrate ähnlich wie Ihre lokalen Datenbanken erforderlich ist. Beispielsweise wird ist die empfohlene Mindest-SKU S4 beim Tarif "standard" und dann auf S3 auswählen oder unter dazu führen, dass Abfragen zu einem Timeout oder nicht ausgeführt.

Die HTML-Datei enthält diese Informationen in einem grafischen Format. Sie können die HTML-Datei verwenden, geben Sie die Informationen des Azure-Abonnement, Auswählen des Tarifs, compute-Ebene und die maximale Größe der Daten für Ihre Datenbanken und generiert ein Skript zum Bereitstellen Ihrer Datenbanken. Dieses Skript kann mithilfe von PowerShell ausgeführt werden.

## <a name="provision-your-databases-to-azure"></a>Die Datenbanken in Azure bereitstellen
Mit nur wenigen Klicks können Sie die Empfehlungen aus dem vorherigen Schritt zum Bereitstellen von Zieldatenbanken in Azure verwenden, zu denen Sie Ihre Datenbanken migrieren können. Sie können auch Änderungen der empfehlungs-vornehmen, indem Sie die HTML-Datei wie folgt aktualisieren.

1. Öffnen Sie die HTML-Datei, und geben Sie die folgende Informationen:
    - **Abonnement-ID** – die Abonnement-ID des Azure-Abonnements, die Sie Datenbanken bereitstellen möchten.
    - **Region** – die Region, in dem Datenbanken bereitstellen. Stellen Sie sicher, dass Ihr Abonnement die Eintrag Region unterstützt.
    - **Ressourcengruppe** : die Ressourcengruppe, zu dem Sie die Datenbanken bereitstellen möchten. Geben Sie eine Ressourcengruppe, die vorhanden ist.
    - **Servername** – Azure SQL-Datenbank-Server an, die Datenbanken, die bereitgestellt werden sollen. Wenn Sie einen Servernamen, der nicht vorhanden ist eingeben, wird sie erstellt.
    - **Admin Username\Password** – den Server-Administratorbenutzernamen und das Kennwort.

2. Empfehlungen für jede Datenbank, und ändern Sie den Tarif, compute-Ebene und die maximale Datengröße je nach Bedarf. Achten Sie darauf, dass Sie alle Datenbanken deaktivieren, die nicht derzeit bereitgestellt werden sollen.

3. Wählen Sie **Bereitstellung Skript generieren**, speichern Sie das Skript, und führen Sie ihn dann in PowerShell.

    Dieser Prozess sollte alle Datenbanken erstellen, die Sie in der HTML-Seite ausgewählt.

Können Sie alle Schritte in diesem Prozess auf einem einzelnen Computer ausführen, oder Sie können diese ausführen, auf mehreren Computern, um zu bestimmen, die SKU-Empfehlungen nach Maß. DMA können sie eine einfache und skalierbare benutzererfahrung durch die Unterstützung von all diese Schritte über die Befehlszeilenschnittstelle. In diesem Fall ist Unterstützung für dieses Feature über die Benutzeroberfläche des DMA später in diesem Jahr verfügbar.

## <a name="next-steps"></a>Nächste Schritte
- Herunterladen der neuesten Version von [Data Migration Assistant](https://aka.ms/get-dma).
- Finden Sie im Artikel [ausführen Data Migration Assistant über die Befehlszeile](https://docs.microsoft.com/sql/dma/dma-commandline?view=sql-server-2017) für eine vollständige Liste der Befehle für die Ausführung von DMA über die Befehlszeilenschnittstelle.
