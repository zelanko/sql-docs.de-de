---
title: Bewährte Methoden für den Datenmigrations-Assistenten
description: Erfahren Sie mehr über bewährte Methoden zum Migrieren von SQL Server-Datenbanken mit dem Datenmigrationsassistenten
ms.custom: seo-lt-2019
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Best Practices
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.openlocfilehash: f2bfbb79a8a4803bb56e3dce85f575e8cf257b4a
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388150"
---
# <a name="best-practices-for-running-data-migration-assistant"></a>Bewährte Methoden für die Ausführung des Datenmigrations-Assistenten
Dieser Artikel enthält einige Informationen zu bewährten Vorgehensweisen für die Installation, Bewertung und Migration.

## <a name="installation"></a>Installation
Installieren und führen Sie den Datenmigrations-Assistenten nicht direkt auf dem SQL Server-Hostcomputer aus.

## <a name="assessment"></a>Bewertung
- Führen Sie Bewertungen für Produktionsdatenbanken während nicht-Spitzenzeiten aus.
- Führen Sie die **Kompatibilitätsprobleme** und die Bewertungen **neuer Feature-Empfehlungen** separat durch, um die Bewertungsdauer zu reduzieren.

## <a name="migration"></a>Migration
- Migrieren Sie einen Server während nicht-Spitzenzeiten.

- Stellen Sie beim Migrieren einer Datenbank einen einzelnen Freigabespeicherort bereit, auf den der Quellserver und der Zielserver zugreifen können, und vermeiden Sie nach Möglichkeit einen Kopiervorgang. Ein Kopiervorgang kann aufgrund der Größe der Sicherungsdatei zu Verzögerungen führen. Der Kopiervorgang erhöht auch die Wahrscheinlichkeit, dass eine Migration aufgrund eines zusätzlichen Schritts fehlschlägt. Wenn ein einzelner Speicherort bereitgestellt wird, umgeht der Datenmigrationsassistent den Kopiervorgang.
 
    Stellen Sie außerdem sicher, dass Sie die richtigen Berechtigungen für den freigegebenen Ordner bereitstellen, um Migrationsfehler zu vermeiden. Die richtigen Berechtigungen werden im Tool angegeben. Wenn eine SQL Server-Instanz unter Netzwerkdienstanmeldeinformationen ausgeführt wird, erteilen Sie dem Computerkonto für die SQL Server-Instanz die richtigen Berechtigungen für den freigegebenen Ordner.

- Aktivieren Sie die Verschlüsselungsverbindung, wenn Sie eine Verbindung mit den Quell- und Zielservern herstellen. Die Verwendung der TLS-Verschlüsselung erhöht die Sicherheit der Über die Netzwerke zwischen dem Datenmigrationsassistenten und der SQL Server-Instanz übertragenen Daten, was insbesondere bei der Migration von SQL-Anmeldungen von Vorteil ist. Wenn die TLS-Verschlüsselung nicht verwendet wird und das Netzwerk von einem Angreifer kompromittiert wird, können die migrierten SQL-Anmeldungen vom Angreifer abgefangen und/oder geändert werden.

    Wenn sich aber der gesamte Zugriff innerhalb einer sicheren Intranetkonfiguration abspielt, ist eine Verschlüsselung möglicherweise nicht erforderlich. Das Aktivieren der Verschlüsselung verlangsamt die Leistung, da der zusätzliche Overhead, der zum Ver- und Entschlüsseln von Paketen erforderlich ist, erforderlich ist. Weitere Informationen finden Sie unter [Verschlüsseln von Verbindungen zu SQL Server](https://go.microsoft.com/fwlink/?linkid=832513).
    
- Überprüfen Sie, ob nicht vertrauenswürdige Einschränkungen sowohl für die Quelldatenbank als auch für die Zieldatenbank vorhanden sind, bevor Sie Daten migrieren. Analysieren Sie nach der Migration erneut die Zieldatenbank, um festzustellen, ob Einschränkungen im Rahmen der Datenverschiebung nicht vertrauenswürdig sind. Beheben Sie nicht vertrauenswürdige Einschränkungen nach Bedarf. Wenn Sie die Einschränkungen nicht vertrauenswürdig lassen, kann dies zu schlechten Ausführungsplänen führen und die Leistung beeinträchtigen.
