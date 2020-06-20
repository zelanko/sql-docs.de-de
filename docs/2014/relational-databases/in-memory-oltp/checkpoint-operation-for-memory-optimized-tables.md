---
title: Prüfpunktvorgang für speicheroptimierte Tabellen
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 47975bd5-373f-43cd-946a-da8e8088b610
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 07560ea0bf147198fb759f6769ae1c6d5c68a71e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050311"
---
# <a name="checkpoint-operation-for-memory-optimized-tables"></a>Prüfpunktvorgang für speicheroptimierte Tabellen
  Für speicheroptimierte Daten in Daten- und Änderungsdateien muss in regelmäßigen Abständen ein Prüfpunkt erstellt werden, um den aktiven Teil des Transaktionsprotokolls fortzuführen. Der Prüfpunkt ermöglicht die Wiederherstellung speicheroptimierter Tabellen am letzten erfolgreichen Prüfpunkt. Anschließend wird der aktive Teil des Transaktionsprotokolls angewendet, um die speicheroptimierten Tabellen zu aktualisieren und die Wiederherstellung abzuschließen. Bei den Prüfpunktvorgängen für datenträgerbasierte und speicheroptimierte Tabellen handelt es sich um unterschiedliche Vorgänge. Im Folgenden werden verschiedene Szenarien und das Prüfpunktverhalten für datenträgerbasierte und speicheroptimierte Tabellen beschrieben:  
  
## <a name="manual-checkpoint"></a>Manueller Prüfpunkt  
 Bei Ausgabe eines manuellen Prüfpunkts wird der Prüfpunkt sowohl für datenträgerbasierte als auch für speicheroptimierte Tabellen geschlossen. Die aktive Datendatei wird geschlossen, obwohl sie möglicherweise teilweise gefüllt ist.  
  
## <a name="automatic-checkpoint"></a>Automatischer Prüfpunkt  
 Automatische Prüfpunkte werden für datenträgerbasierte und speicheroptimierte Tabellen unterschiedlich implementiert, da die Beibehaltung der Daten sich bei diesen beiden Tabellentypen unterscheidet.  
  
 Für datenträgerbasierte Tabellen wird ein automatischer Prüfpunkt basierend auf der Konfigurationsoption Wiederherstellungsintervall erstellt. (Weitere Informationen finden Sie unter [Ändern der Zielwiederherstellungszeit einer Datenbank &#40;SQL Server&#41;](../logs/change-the-target-recovery-time-of-a-database-sql-server.md).)  
  
 Bei Speicher optimierten Tabellen wird ein automatischer Prüfpunkt erstellt, wenn die Transaktionsprotokoll Datei seit dem letzten Prüfpunkt größer als 512 MB ist. 512 MB enthält Transaktionsprotokoll-Datensätze sowohl für Datenträger basierte als auch für Speicher optimierte Tabellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen und Verwalten von Speicher für speicheroptimierte Objekte](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
