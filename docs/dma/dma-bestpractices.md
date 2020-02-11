---
title: Bewährte Methoden für den Datenmigrations-Assistenten
description: Informieren Sie sich über bewährte Methoden zum Migrieren von SQL Server-Daten Datenmigrations-Assistent Banken
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
ms.openlocfilehash: e0f81a49af551836881ca71b49ff6a15d22a9897
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "76162621"
---
# <a name="best-practices-for-running-data-migration-assistant"></a>Bewährte Methoden für die Ausführung des Datenmigrations-Assistenten
Dieser Artikel enthält Informationen zu bewährten Methoden für die Installation, Bewertung und Migration.

## <a name="installation"></a>Installation
Installieren Sie die Datenmigrations-Assistent nicht direkt auf dem SQL Server Host Computer, und führen Sie Sie nicht aus.

## <a name="assessment"></a>Bewertung
- Führen Sie Bewertungen für Produktionsdatenbanken außerhalb der Spitzenzeiten aus.
- Führen Sie die **Kompatibilitätsprobleme** und **neuen Bewertungs Empfehlungen** separat aus, um die Bewertungs Dauer zu verringern.

## <a name="migration"></a>Migration
- Migrieren eines Servers außerhalb der Spitzenzeiten.

- Geben Sie beim Migrieren einer Datenbank einen einzelnen Freigabe Speicherort an, der für den Quell Server und den Zielserver zugänglich ist, und vermeiden Sie, wenn möglich, einen Kopiervorgang. Ein Kopiervorgang kann je nach Größe der Sicherungsdatei zu einer Verzögerung führen. Der Kopiervorgang erhöht außerdem die Wahrscheinlichkeit, dass eine Migration aufgrund eines zusätzlichen Schritts fehlschlägt. Wenn ein einzelner Speicherort bereitgestellt wird, wird Datenmigrations-Assistent den Kopiervorgang umgangen.
 
    Stellen Sie außerdem sicher, dass Sie die richtigen Berechtigungen für den freigegebenen Ordner bereitstellen, um Migrations Fehler zu vermeiden. Die richtigen Berechtigungen werden im Tool angegeben. Wenn eine SQL Server Instanz unter den Anmelde Informationen des Netzwerk Dienstanbieter ausgeführt wird, müssen Sie dem Computer Konto für die SQL Server Instanz die richtigen Berechtigungen für den freigegebenen Ordner erteilt haben.

- Aktivieren Sie Verbindung verschlüsseln, wenn eine Verbindung mit den Quell-und Ziel Servern hergestellt wird. Die Verwendung der SSL-Verschlüsselung erhöht die Sicherheit von Daten, die über die Netzwerke zwischen Datenmigrations-Assistent und der SQL Server Instanz übertragen werden. Dies ist insbesondere bei der Migration von SQL-Anmeldungen vorteilhaft. Wenn die SSL-Verschlüsselung nicht verwendet wird und das Netzwerk von einem Angreifer kompromittiert wird, können die migrierten SQL-Anmeldungen ggf. vom Angreifer abgefangen und/oder geändert werden.

    Wenn sich aber der gesamte Zugriff innerhalb einer sicheren Intranetkonfiguration abspielt, ist eine Verschlüsselung möglicherweise nicht erforderlich. Das Aktivieren der Verschlüsselung verlangsamt die Leistung, da der zusätzliche Aufwand zum Verschlüsseln und Entschlüsseln von Paketen erforderlich ist. Weitere Informationen finden Sie unter Verschlüsseln von [Verbindungen mit SQL Server](https://go.microsoft.com/fwlink/?linkid=832513).
    
- Überprüfen Sie vor dem Migrieren von Daten, ob die Quelldatenbank und die Zieldatenbank nicht vertrauenswürdig sind. Analysieren Sie die Zieldatenbank nach der Migration erneut, um festzustellen, ob Einschränkungen im Rahmen der Daten Verschiebung als nicht vertrauenswürdig eingestuft wurden. Korrigieren Sie nach Bedarf nicht vertrauenswürdige Einschränkungen. Wenn die Einschränkungen nicht vertrauenswürdig sind, kann dies zu schlechten Ausführungsplänen führen, was sich auf die Leistung auswirken kann.
