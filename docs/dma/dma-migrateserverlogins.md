---
title: Migrieren SQL Server Anmeldungen mit Datenmigrations-Assistent
description: Erfahren Sie, wie Sie SQL Server Anmeldungen mit Datenmigrations-Assistent migrieren.
ms.date: 10/22/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, login migration
ms.assetid: ''
author: rajeshsetlem
ms.author: rajpo
ms.custom: seo-lt-2019
ms.openlocfilehash: f721800de13d11eefa1cabdd2f23fda838db9396
ms.sourcegitcommit: fb1430aedbb91b55b92f07934e9b9bdfbbd2b0c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82885787"
---
# <a name="migrate-sql-server-logins-with-data-migration-assistant"></a>Migrieren SQL Server Anmeldungen mit Datenmigrations-Assistent

Dieser Artikel bietet eine Übersicht über das Migrieren von SQL Server Anmeldungen mithilfe von Datenmigrations-Assistent.

> [!IMPORTANT]
> Dieses Thema bezieht sich auf Szenarien, in denen SQL Server Upgrades auf spätere Versionen des lokalen Produkts oder auf Azure Virtual Machines SQL Server werden.

## <a name="which-logins-are-migrated"></a>Migrierte Anmeldungen

- Sie können die Anmeldungen auf Grundlage eines Windows-Prinzipals (z. b. einem Domänen Benutzer oder einer Windows-Domänen Gruppe) migrieren. Sie können auch Anmeldungen migrieren, die auf der Grundlage der SQL-Authentifizierung erstellt wurden, auch als SQL Server Anmeldungen bezeichnet.

- Datenmigrations-Assistent unterstützt derzeit keine Anmeldungen, die einem eigenständigen Sicherheitszertifikat (Anmeldungen, die dem Zertifikat zugeordnet sind) zugeordnet sind, einem eigenständigen asymmetrischen Schlüssel (Anmeldungen, der dem asymmetrischen Schlüssel zugeordnet ist) und Anmeldungen, die Anmelde Informationen zugeordnet sind.

- Datenmigrations-Assistent verschiebt den **sa** -Anmelde Namen und die Server Prinzipien nicht mit den Namen, die von doppelten Hash Zeichen ( \# \# ) eingeschlossen werden, die nur zur internen Verwendung dienen.

- Standardmäßig wählt Datenmigrations-Assistent alle qualifizierten Anmeldungen aus, die migriert werden sollen. Optional können Sie bestimmte Anmeldungen für die Migration auswählen. Wenn Datenmigrations-Assistent alle qualifizierten Anmeldungen migriert, bleibt die Anmeldungs Benutzer Zuordnung in den migrierten Datenbanken erhalten.

  Wenn Sie beabsichtigen, bestimmte Anmeldungen zu migrieren, stellen Sie sicher, dass Sie die Anmeldungen auswählen, die einem oder mehreren Benutzern in den für die Migration ausgewählten Datenbanken zugeordnet sind.

- Im Rahmen der Migration von Anmelde Informationen verschiebt Datenmigrations-Assistent auch benutzerdefinierte Server Rollen und fügt den benutzerdefinierten Server Rollen Berechtigungen auf Serverebene hinzu. Der Besitzer der Rolle wird auf den **sa** -Prinzipal festgelegt.

## <a name="during-and-after-migration"></a>Während und nach der Migration

- Im Rahmen der Anmeldung bei der Anmeldung weist Datenmigrations-Assistent Sicherungs fähigen Elementen auf dem Ziel SQL Server die Berechtigungen zu, die auf der Quell SQL Server vorhanden sind.

  Wenn die Anmeldung bereits auf dem Ziel SQL Server vorhanden ist, migriert Datenmigrations-Assistent nur die Berechtigungen, die Sicherungs fähigen Elementen zugewiesen sind, und erstellt die gesamte Anmeldung nicht neu.

- Mit Datenmigrations-Assistent wird empfohlen, den Anmelde Namen den Datenbankbenutzern zuzuordnen, wenn die Anmeldung bereits auf dem Zielserver vorhanden ist.

- Es wird empfohlen, dass Sie die Migrations Ergebnisse überprüfen, um den Gesamtstatus der Anmelde Migration und alle empfohlenen Aktionen nach der Migration zu verstehen.

## <a name="resources"></a>Ressourcen

[Datenmigrations-Assistent (DMA)](../dma/dma-overview.md)

[Datenmigrations-Assistent: Konfigurationseinstellungen](../dma/dma-configurationsettings.md)
