---
title: Die DACPAC-Erweiterung für SQL Server
titleSuffix: Azure Data Studio
description: Installieren und Verwenden der DACPAC-Erweiterung für SQL Server für Azure Data Studio
ms.custom: seodec18
ms.date: 11/04/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: d33f43f4232e7a9a62365c5bb438c91339f4fd47
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "73532418"
---
# <a name="sql-server-dacpac-extension"></a>Die DACPAC-Erweiterung für SQL Server

**Der Datenschichtanwendungs-Assistent**  macht die Bereitstellung und Extrahierung von DACPAC-Dateien und das Importieren und Exportieren von BACPAC-Dateien einfach.


## <a name="features"></a>Features

* Bereitstellen eines DACPACs in einer SQL Server-Instanz
* Extrahieren einer SQL Server-Instanz in ein DACPAC
* Erstellen einer Datenbank aus einem BACPAC
* Exportieren von Schemas und Daten in ein BACPAC

![GIF einer DACPAC-Erweiterungsdemo](media/extensions/sql-server-dacpac-extension/dacpac-extension-demo.gif)


## <a name="why-would-i-use-the-data-tier-application-wizard"></a>Warum sollte ich den Datenschichtanwendungs-Assistenten verwenden?

Der Assistent erleichtert die Verwaltung von DACPAC- und BACPAC-Dateien, die die Entwicklung und Bereitstellung von Datenschichtelementen zur Unterstützung Ihrer Anwendung vereinfachen. Weitere Informationen zur Verwendung von Datenschichtanwendungen finden Sie in der zugehörigen [Dokumentation](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017).


## <a name="install-the-extension"></a>Installieren der Erweiterung

1. Klicken Sie auf das Symbol „Erweiterungen“, um die verfügbaren Erweiterungen anzuzeigen.

    ![Erweiterungs-Manager-Symbol](media/extensions/extension-manager-icon.png)

2. Suchen Sie nach der Erweiterung **SQL Server-DACPAC**, und wählen Sie sie aus, um die Details anzuzeigen. Klicken Sie auf **Installieren**, um die Erweiterung hinzuzufügen.

3. Klicken Sie nach der Installation auf **Erneut laden**, um die Erweiterung in Azure Data Studio zu aktivieren (nur bei der ersten Installation einer Erweiterung erforderlich).


## <a name="launch-the-data-tier-application-wizard"></a>Starten des Datenschichtanwendungs-Assistenten

Klicken Sie zum Starten des Assistenten mit der rechten Maustaste auf den Ordner „Datenbanken“, oder klicken Sie im Objekt-Explorer mit der rechten Maustaste auf eine bestimmte Datenbank. Klicken Sie dann auf **Datenschichtanwendungs-Assistent**.

![Startmenü der DACPAC-Erweiterung](media/extensions/sql-server-dacpac-extension/dacpac-extension-launch.png)


## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu DACPACs finden Sie in der zugehörigen [Dokumentation](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017).
Probleme und Featureanforderungen können Sie [hier](https://github.com/microsoft/azuredatastudio/issues) mitteilen.