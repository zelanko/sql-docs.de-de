---
title: Bewährte Methoden für den Data Migration Assistant (SQL Server) | Microsoft-Dokumentation
description: Erlernen Sie bewährte Methoden für die Migration von SQL Server-Datenbanken mit Data Migration Assistant
ms.custom: ''
ms.date: 10/20/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Best Practices
ms.assetid: ''
author: pochiraju
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 79eade425e87da3784221686b7ccdc99e85b96bc
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49643828"
---
# <a name="best-practices-for-running-data-migration-assistant"></a>Bewährte Methoden für die Ausführung von Data Migration Assistant
Dieser Artikel enthält einige Informationen zu bewährten Methoden für die Installation, Bewertung und Migration.

## <a name="installation"></a>Installation
Nicht installieren Sie, und führen Sie den Data Migration Assistant, direkt auf dem SQL Server-Hostcomputer.

## <a name="assessment"></a>Bewertung
- Führen Sie Bewertungen für Produktionsdatenbanken Zeiten außerhalb der Spitzenzeiten.
- Führen Sie die **Kompatibilitätsprobleme** und **neuen featureempfehlungen** Bewertungen separat durchführen, um die Dauer für die Bewertung zu reduzieren.

## <a name="migration"></a>Migration
- Migrieren eines Servers Zeiten außerhalb der Spitzenzeiten.

- Beim Migrieren einer Datenbank geben Sie einen einzelnen Netzwerkfreigabe, die durch den Quellserver und Zielserver zugegriffen werden kann, und vermeiden Sie ein Kopiervorgangs nach Möglichkeit. Ein Kopiervorgang kann basierend auf der Größe der Sicherungsdatei Verzögerung führen. Der Kopiervorgang erhöht sich auch die Wahrscheinlichkeit, die eine Migration aufgrund ein zusätzlicher Schritt fehlschlägt. Bei einem zentralen Ort angegeben wird, umgeht Data Migration Assistant den Kopiervorgang.
 
    Darüber hinaus stellen Sie sicher, dass, geben Sie die erforderlichen Berechtigungen für den freigegebenen Ordner zum Migrationsfehler zu vermeiden. Die richtigen Berechtigungen werden im Tool angegeben. Wenn eine SQL Server-Instanz unter Network Service-Anmeldeinformationen ausgeführt wird, geben Sie die richtigen Berechtigungen für den freigegebenen Ordner, um das Computerkonto für den SQL Server-Instanz.

- Verbindung verschlüsseln aktivieren, bei der Verbindung von Quell-und Ziel. Mithilfe von SSL-Verschlüsselung erhöht die Sicherheit der Daten, die netzwerkübergreifend zwischen Data Migration Assistant und SQL Server-Instanz, die von Vorteil ist insbesondere bei der Migration von SQL-Anmeldungen. Wenn SSL-Verschlüsselung wird nicht verwendet, und das Netzwerk von einem Angreifer gefährdet ist, wird die SQL-Anmeldungen, die zu migrierenden abgefangen abrufen konnte bzw. auf dynamisch durch den Angreifer geändert.

    Wenn sich aber der gesamte Zugriff innerhalb einer sicheren Intranetkonfiguration abspielt, ist eine Verschlüsselung möglicherweise nicht erforderlich. Aktivieren der Verschlüsselung beeinträchtigen die Leistung, da es sich bei den Mehraufwand, der zum Verschlüsseln und Entschlüsseln von Paketen erforderlich ist. Weitere Informationen finden Sie in [Verschlüsseln von Verbindungen zu SQL Server](https://go.microsoft.com/fwlink/?linkid=832513).
