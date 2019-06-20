---
title: Entdecken Sie Azure SQL-Ressourcen mit Azure-Ressourcen-Explorer
titleSuffix: Azure Data Studio
description: Erfahren Sie, wie Sie untersuchen und Verwalten von Azure SQL-Server, Azure SQL-Datenbank und Azure verwaltete SQL-Instanz über Azure-Ressourcen-Explorer.
ms.custom: seodec18
author: yanancai
ms.author: yanacai
manager: jroth
ms.date: 09/24/2018
ms.topic: quickstart
ms.prod: sql
ms.technology: azure-data-studio
ms.openlocfilehash: 91e766fae5dca7a3d9e2dec56af17161d684e145
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66789216"
---
# <a name="explore-and-manage-azure-sql-resources-with-azure-resource-explorer"></a>Untersuchen und Verwalten von Azure SQL-Ressourcen mit Azure-Ressourcen-Explorer

In diesem Dokument erfahren Sie, wie Sie untersuchen und Verwalten von Azure SQL-Server, Azure SQL-Datenbank und verwaltete Azure SQL-Instanz-Ressourcen über das Azure-Ressourcen-Explorer in [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)].

>[!NOTE]
>Der Azure-Ressourcen-Explorer wird in der Vorschau von SQL Server-2019 im Oktober unterstützt. Danach können Sie die vorschauerweiterung über die installieren [Erweiterungs-Manager](extensions.md) oder über **Datei** > **Installieren eines Pakets aus der VSIX-Paket**.


## <a name="connect-to-azure"></a>Verbinden mit Azure

Nach der Installation der SQL-Vorschau-Plug-in wird Sie ein Azure-Symbol in der linken Menüleiste angezeigt. Klicken Sie auf das Symbol, um die Azure-Ressourcen-Explorer zu öffnen. Wenn Sie das Azure-Symbol nicht sehen, klicken Sie mit der rechten Maustaste auf der linken Menüleiste, und wählen **Azure-Ressourcen-Explorer**.

### <a name="add-an-azure-account"></a>Azure-Konto hinzufügen

Um die SQL-Ressourcen, die mit einem Azure-Konto verknüpfte anzuzeigen, müssen Sie zunächst das Konto hinzufügen [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)].

1. Open **verknüpfte Konten** Dialogfeld über das Konto-Management-Symbol auf der linken unteren oder über einen **melden Sie sich beim Azure...**  Link im Azure-Ressourcen-Explorer.

    ![Melden Sie sich beim Azure](media/azure-resource-explorer/sign-in-to-azure.png)

2. In der **verknüpfte Konten** Dialogfeld klicken Sie auf **Hinzufügen eines Kontos**.

    ![Azure-Konto hinzufügen](media/azure-resource-explorer/add-an-azure-account.png)

3. Klicken Sie auf **kopieren und öffnen Sie** , öffnen Sie den Browser für die Authentifizierung.

    ![Offene Authentifizierung-Seite im browser](media/azure-resource-explorer/open-authentication-in-browser.png)

4. Fügen Sie der **Benutzercode** in der Webseite und auf **Weiter** authentifizieren.

    ![Im Browser authentifizieren](media/azure-resource-explorer/authenticate-in-browser.png)

5. In [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)] sollte jetzt finden Sie die protokollierten im Azure-Konto in **verknüpfte Konten** Dialogfeld.

    ![Angemeldeten Azure-Konto](media/azure-resource-explorer/signed-in-azure-account.png)

### <a name="add-more-azure-accounts"></a>Fügen Sie weitere Azure-Konten

Mehrere Azure-Konten werden in unterstützt [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)]. Um mehr über Azure-Konten hinzuzufügen, klicken Sie auf die Schaltfläche rechts oben **verknüpfte Konten** Dialogfeld, und führen Sie dieselben Schritte mit fügen Sie einen Azure-Konto-Abschnitt, um weitere Azure-Konten hinzuzufügen.

![Weitere Azure-Konto hinzufügen](media/azure-resource-explorer/add-more-azure-account.png)

### <a name="remove-an-azure-account"></a>Entfernen Sie ein Azure-Konto

So entfernen Sie ein vorhandenes Azure-Konto angemeldet

1. Open **verknüpfte Konten** Dialogfeld über das Konto-Management-Symbol in der linken unteren.
2. Klicken Sie auf die **X** Schalfläche rechts neben dem Azure-Konto, um ihn zu entfernen.

    ![Azure-Konto entfernen](media/azure-resource-explorer/remove-azure-account.png)

## <a name="filter-subscription"></a>Abonnements filtern

Nach der Anmeldung mit einem Azure-Konto zugeordnet ist alle Abonnements im Azure-Ressourcen-Explorer, Azure-Konto in angezeigt. Sie können Abonnements für jede Azure-Konto filtern.

1. Klicken Sie auf die **Select Subscription** Schaltfläche auf der rechten Seite des Azure-Kontos.

   ![Abonnements filtern](media/azure-resource-explorer/filter-subscription.png)

2. Wählen Sie die Kontrollkästchen für die Kontoabonnements, die Sie verwenden möchten, navigieren Sie aus, und klicken Sie dann auf **OK**.

   ![Auswählen des Abonnements](media/azure-resource-explorer/select-subscription.png)

## <a name="explore-azure-sql-resources"></a>Entdecken Sie Azure SQL-Ressourcen

Um eine Azure SQL-Ressource im Azure-Ressourcen-Explorer zu navigieren, erweitern Sie in der Azure-Konten und die Ressourcengruppe aus, geben.

Azure-Ressourcen-Explorer unterstützt derzeit bei Azure SQL-Server, Azure SQL-Datenbank und verwaltete Azure SQL-Instanz.

## <a name="connect-to-azure-sql-resources"></a>Eine Verbindung mit Azure SQL-Ressourcen

Azure-Ressourcen-Explorer ermöglichen den schnellen Zugriff, der Sie für SQL Server-Instanzen und Datenbanken für Abfrage und die Verwaltung von verbinden kann. 

1. Erkunden Sie die SQL-Ressource, die Sie in der Strukturansicht eine Verbindung mit herstellen möchten.
2. Klicken Sie mit der rechten Maustaste auf die Ressource, und wählen Sie **Connect**, finden Sie auch die Schaltfläche "Verbinden" auf der rechten Seite der Ressource.

   ![Verbinden Sie mit Azure SQL-Ressource](media/azure-resource-explorer/connect-to-azure-sql-resource.png)

3. Im geöffneten **Verbindung** Dialogfeld Geben Sie Ihr Kennwort ein, und klicken Sie auf **Connect**.

   ![Dialogfeld "SQL-Verbindung"](media/azure-resource-explorer/sql-connection-dialog.png)
4. Die **Server** Fenster wird automatisch die neue verbundene SQL Server/Datenbank geöffnet, nachdem die Verbindung erfolgreich hergestellt wurde.

## <a name="next-steps"></a>Nächste Schritte

- [Verwendung [!INCLUDE[Azure Data Studio](../includes/name-sos-short.md)] zum Verbinden und Abfragen von Azure SQL-Datenbank](quickstart-sql-database.md)
- [Verwendung [!INCLUDE[Azure Data Studio](../includes/name-sos-short.md)] zum Verbinden und Abfragen von Daten in Azure SQL Data Warehouse](quickstart-sql-dw.md)