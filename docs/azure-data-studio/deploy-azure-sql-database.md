---
title: Bereitstellen von Azure SQL Database mithilfe eines Notebooks
description: In diesem Tutorial erfahren Sie, wie Sie eine Azure SQL-Datenbank erstellen können.
author: ninarn
ms.author: ninarn
ms.reviewer: alayu, maghan
ms.topic: tutorial
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 10/14/2020
ms.openlocfilehash: 88bb9fd980da21b20f0faf6f699147d26abe65b9
ms.sourcegitcommit: 76ab3b57718341c6057613c9bd38cf82fb17786e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92060887"
---
# <a name="create-an-azure-sql-database-using-azure-data-studio"></a>Erstellen einer Azure SQL-Datenbank mithilfe von Azure Data Studio

Sie können eine Azure SQL-Datenbank mithilfe von Azure Data Studio über den Bereitstellungs-Assistenten und Notebooks erstellen.

## <a name="pre-requisites"></a>Voraussetzungen

 - [Azure Data Studio](download-azure-data-studio.md) ist installiert
 - Ein aktives Azure-Konto und ein Azure-Abonnement. Falls Sie nicht über ein Abonnement verfügen, können Sie ein [kostenloses Konto erstellen](https://azure.microsoft.com/free/).

## <a name="use-the-deployment-wizard"></a>Verwenden des Bereitstellungs-Assistenten

Führen Sie die folgenden Schritte aus, um den Bereitstellungs-Assistenten zu verwenden, der Sie mit einer einfachen Benutzeroberfläche durch die erforderlichen Einstellungen führt.

Suchen Sie zuerst Azure SQL-Datenbank im Bereitstellungs-Assistenten, und wählen Sie es aus.

 1. Wählen Sie in Azure Data Studio das Viewlet „Verbindungen“ im Navigationsbereich auf der linken Seite aus.
 2. Wählen Sie oben im Bereich „Verbindungen“ die Schaltfläche mit den drei Auslassungspunkten **...** und dann **Neue Bereitstellung...** aus.
 3. Wählen Sie im Bereitstellungs-Assistenten die Kachel **Azure SQL-Datenbank** aus, und aktivieren Sie das Kontrollkästchen zum Akzeptieren der Bedingungen.
 4. Wählen Sie in der Dropdownliste der Ressourcentypen aus, was Sie erstellen möchten: eine Datenbank, einen Datenbankserver oder einen Pool für elastische Datenbanken. Wenn Sie nicht über SQL-Datenbanken in Azure verfügen, empfehlen wir Ihnen, mit dem Erstellen einer Datenbank anzufangen.
 5. Wählen Sie **Im Azure-Portal erstellen** aus.

Geben Sie als nächstes alle bevorzugten Einstellungen zum Erstellen Ihrer Datenbank, Ihres Servers oder Ihres Pools ein. Einige Anleitungen zum Konfigurieren dieser Einstellungen finden Sie in der [Azure SQL-Dokumentation](https://docs.microsoft.com/azure/azure-sql/database/single-database-create-quickstart?tabs=azure-portal).

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Ihre Datenbank, Ihren Server oder Ihren Pool erstellt haben, können Sie zu Ihrer Datenbank in Azure Data Studio [eine Verbindung herstellen und sie abfragen](quickstart-sql-database.md).
