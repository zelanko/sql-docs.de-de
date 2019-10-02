---
title: Verwalten von Python-und R-Workloads mit Resource Governor
description: Erfahren Sie, wie Sie mit Resource Governor CPU, physische e/a und Speicherressourcen Zuordnung für python-und R-Arbeits Auslastungen in SQL Server Machine Learning Services verwalten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/01/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: eec3d2762366252fbc170c2a6c4176fe0283edce
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714314"
---
# <a name="manage-python-and-r-workloads-with-resource-governor-in-sql-server-machine-learning-services"></a>Verwalten von Python-und R-Arbeits Auslastungen mit Resource Governor in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Erfahren Sie, wie Sie mit [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) CPU, physische e/a und Speicherressourcen Zuordnung für python-und R-Arbeits Auslastungen in SQL Server Machine Learning Services verwalten.

Machine Learning-Algorithmen in Python und R sind in der Regel Rechen intensiv. Abhängig von den Prioritäten der Arbeitsauslastung müssen Sie möglicherweise die für Machine Learning Services verfügbaren Ressourcen erhöhen oder verringern.

Weitere allgemeine Informationen finden Sie unter [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).

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
  
## <a name="next-steps"></a>Nächste Schritte

+ [Erstellen eines Ressourcenpools für Machine Learning](create-external-resource-pool.md)
+ [Resource Governor von Ressourcenpools](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
