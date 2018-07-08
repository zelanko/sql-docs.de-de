---
title: Migrieren von SQL Server-Anmeldungen mit den Data Migration Assistant | Microsoft-Dokumentation
description: Informationen Sie zum Migrieren von SQL Server-Anmeldungen mit den Data Migration Assistant
ms.custom: ''
ms.date: 08/31/2017
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, login migration
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: bb5dec6babc17ad8be5d0531b463f230e719c73d
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2018
ms.locfileid: "37783161"
---
# <a name="migrate-sql-server-logins-with-data-migration-assistant"></a>Migrieren von SQL Server-Anmeldungen mit den Data Migration Assistant

Dieser Artikel enthält einen Überblick über die Migration von SQL Server-Anmeldungen, die mithilfe von Data Migration Assistant. 

## <a name="which-logins-are-migrated"></a>Welche Anmeldungen werden migriert.

- Sie können die Anmeldungen auf Grundlage eines Windows-Prinzipals (z. B. ein Domänenbenutzer oder eine Windows-Domänengruppe) migrieren. Sie können auch basierend auf SQL Server-Anmeldungen so genannte SQL-Authentifizierung erstellte Anmeldungen migrieren.

- Data Migration Assistant unterstützt derzeit keine Anmeldungen verknüpft, die mit einem eigenständigen Sicherheitszertifikat (Anmeldungen, Zertifikat zugeordnet ist), einem eigenständigen asymmetrischen Schlüssel (Anmeldungen zugeordnet zu asymmetrischem Schlüssel) und Anmeldungen, die Anmeldeinformationen zugeordnet ist.

- Data Migration Assistant nicht verschieben der **sa** Prinzipien von Anmelde- und Server mit Namen, die von doppelten Nummernzeichen eingeschlossen (\#\#), für die interne Verwendung vorgesehen sind.

- Standardmäßig wählt Data Migration Assistant alle qualifizierten Anmeldungen zu migrieren. Optional können Sie bestimmte Anmeldungen zum Migrieren auswählen. Wenn Data Migration Assistant alle qualifizierte Benutzernamen migriert, bleiben die Zuordnung für die Anmeldung für Benutzer in den Datenbanken, die migriert werden. 

  Wenn Sie bestimmte Anmeldungen migrieren möchten, stellen Sie sicher, dass die Anmeldungen aktivieren, die einen oder mehrere Benutzer in den für die Migration ausgewählten Datenbanken zugeordnet sind.

- Im Rahmen der Migration von Benutzernamen Data Migration Assistant außerdem verschiebt eine benutzerdefinierte Serverrollen und -Berechtigungen auf Serverebene, die den benutzerdefinierten Serverrollen hinzugefügt. Der Besitzer der Rolle festgelegt **sa** Prinzipal.

## <a name="during-and-after-migration"></a>Während und nach der Migration

- Im Rahmen der Migration von Benutzernamen weist Data Migration Assistant die Berechtigungen zu sicherungsfähigen Elementen, auf dem SQL-Zielserver wie sie auf dem SQL-Quellserver vorhanden sind. 

  Wenn die Anmeldung auf dem SQL Server-Ziel bereits vorhanden ist, Data Migration Assistant nur die Berechtigungen für sicherungsfähige Elemente migriert und die gesamte Anmeldung nicht neu erstellt wird.

- Data Migration Assistant macht die bestmöglich versuchen soll, die Anmeldung für Datenbankbenutzer zuzuordnen, wenn die Anmeldung auf dem Zielserver bereits vorhanden ist.

- Es wird empfohlen, führt die Migration, um den allgemeinen Status der Migration von Benutzernamen und empfohlenen Aktionen in der nach der Migration zu verstehen, zu überprüfen.

## <a name="resources"></a>Ressourcen

[Data Migration Assistant (DMA)](../dma/dma-overview.md)

[Data Migration Assistant: Konfigurationseinstellungen für](../dma/dma-configurationsettings.md)
