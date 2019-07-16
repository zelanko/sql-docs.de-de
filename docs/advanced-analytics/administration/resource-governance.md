---
title: Ressourcenkontrolle für die skriptausführung R- und Python - SQL Server-Machine Learning
description: Ordnen Sie Arbeitsspeicher, CPU und e/a-RAM für R und Python-Workloads in SQL Server-Datenbank-Engine-Instanz an.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: e6063f8367e5b91e7e935d6f92515a6dd452dc56
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963138"
---
# <a name="resource-governance-for-machine-learning-in-sql-server"></a>Ressourcenkontrolle für Machine Learning in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Data Science und Machine learning-Algorithmen sind rechenintensiv. Je nach den Prioritäten bei der arbeitsauslastung müssen Sie möglicherweise die für Data Science verfügbaren Ressourcen zu erhöhen oder verringern, die Ressourcen, wenn Sie R und Python Execution Script verwendungsdatensammlungssystem, die Leistung anderer Dienste, die gleichzeitig ausgeführt werden. 

Wenn Sie die Verteilung von Ressourcen für mehrere Workloads ausgleichen möchten, können Sie [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) Zuweisen von CPU, physische e/a und Speicherressourcen, die von externen Laufzeiten für R und Python genutzt. Wenn Sie Ressourcen verschieben, denken Sie daran, dass Sie möglicherweise auch die reservierten Umfang an Arbeitsspeicher für andere arbeitsauslastungen und Dienste zu reduzieren. 

> [!NOTE] 
> Resource Governor ist eine Funktion der Enterprise Edition.

## <a name="default-allocations"></a>Standardzuordnungen

Standardmäßig sind die externen Skript-Laufzeiten für Machine Learning auf nicht mehr als 20 % des gesamten Arbeitsspeichers beschränkt. Es hängt von Ihrem System, aber im Allgemeinen möglicherweise dieses Limit nicht schwerwiegenden Machine Learning-Aufgaben wie das Trainieren eines Modells oder das Vorhersagen von vielen Zeilen mit Daten. 

## <a name="use-resource-governor-to-control-resourcing"></a>Verwenden der Ressourcenkontrolle zum Steuern der enthaltenen
 
Externe Prozesse verwenden standardmäßig bis zu 20 % des gesamten Speicher auf dem lokalen Server. Sie können ändern, dass den standardressourcenpool, um serverweite Änderungen mit R und Python-Prozesse, die beliebige Kapazität nutzen Sie die externe Prozesse zur Verfügung stellen.

Sie können auch benutzerdefinierte erstellen *externe Ressourcenpools*mit zugehörigen Arbeitsauslastungsgruppen und Klassifizierer, ressourcenzuweisung für Zugriffsanfragen von bestimmten Programme, Hosts oder anderen Kriterien zu ermitteln, Sie bieten. Ein externer Ressourcenpool ist ein Typ des Ressourcenpools, die in eingeführt [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] zur Verwaltung von R und Python Prozesse, die außerhalb der Datenbank-Engine.

1. [Aktivieren der Ressourcenkontrolle](https://docs.microsoft.com/sql/relational-databases/resource-governor/enable-resource-governor) (es ist standardmäßig deaktiviert).

2. Führen Sie [CREATE EXTERNAL RESOURCE POOL](https://docs.microsoft.com/sql/t-sql/statements/create-external-resource-pool-transact-sql) zum Erstellen und konfigurieren den Ressourcenpool, gefolgt von [ALTER RESOURCE GOVERNOR](https://docs.microsoft.com/sql/t-sql/statements/alter-resource-governor-transact-sql) für die Implementierung.

3. Erstellen Sie eine Arbeitsauslastungsgruppe für eine präzise Zuordnungen, z. B. zwischen Trainings- und Bewertung.

4. Erstellen Sie eine Klassifizierung zum Abfangen von Aufrufe zur externen Verarbeitung.

5. Ausführen von Abfragen und Prozeduren, die mithilfe der Objekte, die Sie erstellt haben.

Eine exemplarische Vorgehensweise finden Sie unter [Gewusst wie: Erstellen eines Ressourcenpools für externe R und Python-Skripts](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md) schrittweise Anweisungen.

Eine Einführung in die Terminologie und allgemeinen Konzepte, finden Sie unter [Resource Governor Resource Pool](../../relational-databases/resource-governor/resource-governor-resource-pool.md).

## <a name="processes-under-resource-governance"></a>Prozesse unter Ressourcenkontrolle
  
 Sie können eine *externen Ressourcenpool* zum Verwalten der Ressourcen, die von der folgenden Programme auf einer Datenbank-Engine-Instanz verwendet:

+ Rterm.exe beim aufgerufenen lokal von SQL Server oder Remote mit SQL Server als dem entfernten computekontext aufgerufene
+ Python.exe beim aufgerufenen lokal von SQL Server oder Remote mit SQL Server als dem entfernten computekontext aufgerufene
+ BxlServer.exe und Satellitenprozesse
+ Satellitenprozesse, die von Launchpad, z. B. PythonLauncher.dll gestartet werden
  
> [!NOTE]
> Direkte Verwaltung des Launchpad-Diensts mithilfe von Resource Governor wird nicht unterstützt. Launchpad handelt es sich um ein vertrauenswürdiger Dienst, der nur Host-startfeldern von Microsoft bereitgestellt werden können. Vertrauenswürdige Startprogramme sind explizit konfiguriert, um zu vermeiden, übermäßigen Ressourcenverbrauch.
  
## <a name="see-also"></a>Siehe auch

+ [Verwalten von Machine Learning-integration](../r/managing-and-monitoring-r-solutions.md)
+ [Erstellen eines Ressourcenpools für Machine Learning](../r/how-to-create-a-resource-pool-for-r.md)
+ [Ressourcenpools der Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
