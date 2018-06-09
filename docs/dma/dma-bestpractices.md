---
title: Bewährte Methoden für das Data Migration Assistant (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Best Practices
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 8a1b184a6a280b328df35ea04a1ab6caf996c7c8
ms.sourcegitcommit: 6fe7b5e8818bd0d94fce693c560d63cc6883d76f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34758110"
---
# <a name="best-practices-for-running-data-migration-assistant"></a>Bewährte Methoden für die Ausführung von Data-Migrations-Assistent
Dieser Artikel enthält die folgenden best Practice-Informationen für die Installation, Bewertung und Migration.

## <a name="installation"></a>Installation
Installieren Sie und führen Sie des Migrations-Assistenten für Daten direkt auf dem SQL Server-Hostcomputer aus nicht.

## <a name="assessment"></a>Bewertung
- Führen Sie Bewertungen für Produktionsdatenbanken während Zeiten geringer Netzwerkverwendung.
- Führen Sie die **Kompatibilitätsprobleme** und **neue Funktion Empfehlungen** Bewertungen für die Reduzierung der Dauer Assessment einzeln.

## <a name="migration"></a>Migration
- Migrieren eines Servers während Zeiten geringer Netzwerkverwendung.
- Beim Migrieren einer Datenbank geben Sie einen einzelnen Netzwerkfreigabe, die durch den Quellserver und Zielserver zugegriffen werden kann, und eines Kopiervorgangs vermeiden Sie nach Möglichkeit. Ein Vorgang zum Kopieren kann basierend auf der Größe der Sicherungsdatei Verzögerung führen. Der Kopiervorgang auch steigt die Wahrscheinlichkeit, die eine Migration aufgrund ein zusätzlicher Schritt fehl. Bei ein zentralen Ort bereitgestellt wird, umgeht Data Migration Assistant den Kopiervorgang.
 
    Darüber hinaus, achten Sie darauf, geben Sie die korrekten Berechtigungen für den freigegebenen Ordner, um Migrationsfehler zu vermeiden. Die richtigen Berechtigungen werden im Tool angegeben. Wenn SQL Server-Instanz unter Network Service Anmeldeinformationen ausgeführt wird, geben Sie die richtigen Berechtigungen für den freigegebenen Ordner auf das Computerkonto für den SQL Server-Instanz.

- Verbindung verschlüsseln aktivieren, bei der Verbindung von Quell-und Ziel. Verwendung von SSL-Verschlüsselung erhöht die Sicherheit der Daten, die netzwerkübergreifend zwischen Data Migration Assistant und SQL Server-Instanz, die nützlich ist, insbesondere bei der Migration von SQL-Anmeldungen. Wenn keine SSL-Verschlüsselung verwendet wird, und das Netzwerk von einem Angreifer gefährdet ist, wird die SQL-Anmeldungen, die zu migrierenden konnte abgefangen abrufen und/oder auf dynamisch von der Angreifer geändert.

    Wenn sich aber der gesamte Zugriff innerhalb einer sicheren Intranetkonfiguration abspielt, ist eine Verschlüsselung möglicherweise nicht erforderlich. Aktivieren der Verschlüsselung durch die Leistung, da der Mehraufwand zu vermeiden, die zum Verschlüsseln und Entschlüsseln von Paketen erforderlich ist. Weitere Informationen finden Sie auf [Verschlüsseln von Verbindungen zu SQL Server](https://go.microsoft.com/fwlink/?linkid=832513).
