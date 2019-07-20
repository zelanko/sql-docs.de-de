---
title: Ressourcenkontrolle für die Skriptausführung von R und python
description: Zuweisen von RAM-Arbeitsspeicher, CPU und e/a für R-und python-Workloads auf SQL Server Datenbank-Engine-Instanz.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 1a665fd92f630b46351ef96cc203c9bbf71f54a2
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345138"
---
# <a name="resource-governance-for-machine-learning-in-sql-server"></a>Ressourcenkontrolle für Machine Learning in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Data Science-und Machine Learning-Algorithmen sind Rechen intensiv. Abhängig von den Prioritäten der Arbeitsauslastung müssen Sie möglicherweise die für Data Science verfügbaren Ressourcen erhöhen oder die ausgewähltem Ressourcen verringern, wenn die Ausführung von R-und python-Skripts die Leistung anderer gleichzeitig ausgeführten Dienste untergräbt. 

Wenn Sie die Verteilung der Systemressourcen auf mehrere Arbeits Auslastungen zurücksetzen müssen, können Sie mit [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) CPU, physische e/a und Arbeitsspeicher Ressourcen zuordnen, die von den externen Laufzeiten für R und python beansprucht werden. Wenn Sie Ressourcen Zuordnungen verschieben, denken Sie daran, dass Sie möglicherweise auch die Menge an Arbeitsspeicher reduzieren müssen, die für andere Workloads und Dienste reserviert ist. 

> [!NOTE] 
> Resource Governor ist eine Funktion der Enterprise Edition.

## <a name="default-allocations"></a>Standard Zuordnungen

Standardmäßig sind die externen Skript Laufzeiten für Machine Learning auf nicht mehr als 20% des gesamten Computer Arbeitsspeichers beschränkt. Das hängt von Ihrem System ab, aber im Allgemeinen ist diese Beschränkung für schwerwiegende Machine Learning-Aufgaben unzureichend, wie z. b. das Trainieren eines Modells oder das Vorhersagen von vielen Daten Zeilen. 

## <a name="use-resource-governor-to-control-resourcing"></a>Verwenden von Resource Governor zum Steuern der ausgewähltem Ressourcen
 
Standardmäßig verwenden externe Prozesse bis zu 20% des gesamten Host Arbeitsspeichers auf dem lokalen Server. Sie können den Standard Ressourcenpool so ändern, dass Server weite Änderungen vorgenommen werden, wobei R-und python-Prozesse die für externe Prozesse verfügbare Kapazität nutzen.

Alternativ können Sie benutzerdefinierte *externe Ressourcenpools*mit zugeordneten Arbeits Auslastungs Gruppen und Klassifizierungen erstellen, um die Ressourcenzuweisung für Anforderungen zu bestimmen, die von bestimmten Programmen, Hosts oder anderen von Ihnen bereitgestellten Kriterien stammen. Ein externer Ressourcenpool ist ein Typ von Ressourcenpool, der [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] in eingeführt wurde, um die Verwaltung von R-und python-Prozessen außerhalb der Datenbank-Engine zu unterstützen.

1. [Aktivieren der Ressourcen](https://docs.microsoft.com/sql/relational-databases/resource-governor/enable-resource-governor) Kontrolle (standardmäßig deaktiviert).

2. Führen Sie [externen Ressourcenpool erstellen](https://docs.microsoft.com/sql/t-sql/statements/create-external-resource-pool-transact-sql) aus, um den Ressourcenpool zu erstellen und zu konfigurieren, gefolgt von [Alter Resource Governor](https://docs.microsoft.com/sql/t-sql/statements/alter-resource-governor-transact-sql) , um ihn zu implementieren.

3. Erstellen Sie eine Arbeits Auslastungs Gruppe für präzise Zuordnungen, z. b. zwischen Training und Bewertung.

4. Erstellen Sie einen Klassifizierer, um Aufrufe für die externe Verarbeitung abzufangen.

5. Führen Sie Abfragen und Prozeduren mit den von Ihnen erstellten Objekten aus.

Eine exemplarische Vorgehensweise finden [Sie unter Erstellen eines Ressourcenpools für externe R-und python-Skripts](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md) .

Eine Einführung in die Terminologie und allgemeine Konzepte finden Sie unter [Resource Governor Ressourcenpools](../../relational-databases/resource-governor/resource-governor-resource-pool.md).

## <a name="processes-under-resource-governance"></a>Prozesse unter ressourcengovernance
  
 Sie können einen *externen Ressourcenpool* verwenden, um die Ressourcen zu verwalten, die von den folgenden ausführbaren Dateien auf einer Datenbank-Engine-Instanz verwendet werden:

+ RTERM. exe, wenn Sie lokal von SQL Server aufgerufen oder Remote mit SQL Server als remotecomputekontext aufgerufen wird.
+ "Python. exe", wenn Sie lokal von SQL Server aufgerufen oder Remote mit SQL Server als remotecomputekontext aufgerufen wird
+ BxlServer.exe und Satellitenprozesse
+ Vom Launchpad gestartete Satelliten Prozesse, z. b. "pythonlauncher. dll"
  
> [!NOTE]
> Die direkte Verwaltung des Launchpad-Dienstanbieter mithilfe von Resource Governor wird nicht unterstützt. Launchpad ist ein vertrauenswürdiger Dienst, der nur von Microsoft bereitgestellte Launcher hosten kann. Vertrauenswürdige Launcher werden explizit konfiguriert, um zu vermeiden, dass übermäßig viele Ressourcen beansprucht werden
  
## <a name="see-also"></a>Siehe auch

+ [Verwalten der Machine Learning-Integration](../r/managing-and-monitoring-r-solutions.md)
+ [Erstellen eines Ressourcenpools für Machine Learning](../r/how-to-create-a-resource-pool-for-r.md)
+ [Resource Governor von Ressourcenpools](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
