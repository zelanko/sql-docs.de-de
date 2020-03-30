---
title: 'Python und T-SQL: Entwickeln eines Modells'
description: Informieren Sie sich, wie Sie Python-Code in gespeicherte Prozeduren von SQL Server und T-SQL-Funktionen einbetten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3bafc3a524ec854dc9bf1669660827d5a6bc80f7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "74901893"
---
# <a name="tutorial-python-data-analytics-for-sql-developers"></a>Tutorial: Python-Datenanalysen für SQL-Entwickler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Tutorial für SQL-Programmierer erfahren Sie, wie Sie Python durch Erstellen und Bereitstellen einer Python-basierten Machine Learning-Lösung mithilfe der Datenbank [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) in SQL Server integrieren. Sie verwenden T-SQL, SQL Server Management Studio und eine Datenbank-Engine-Instanz mit [Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) und Unterstützung der Python-Programmiersprache.

Dieses Tutorial bietet eine Einführung in Python-Funktionen, die in einem Workflow für Datenmodellierung verwendet werden. Dies beinhaltet das Durchsuchen von Daten, das Entwickeln und Trainieren eines binären Klassifizierungsmodells sowie die Modellimplementierung. Sie verwenden Beispieldaten der New York City Taxi and Limosine Commission, und das von Ihnen erstellte Modell sagt basierend auf der Tageszeit, der zurückgelegten Distanz und dem Startpunkt vorher, ob für die Fahrt ein Trinkgeld gezahlt wird. 

Der gesamte in diesem Tutorial verwendete Python-Code wird in gespeicherte Prozeduren eingebunden, die Sie in Management Studio erstellen und ausführen.

> [!NOTE]
> Dieses Tutorial ist sowohl in R als auch in Python verfügbar. Weitere Informationen zur R-Version finden Sie unter [Datenbankinterne Analysen für R-Entwickler](sqldev-in-database-r-for-sql-developers.md).

## <a name="overview"></a>Übersicht

Der Erstellungsprozess einer Machine Learning-Lösung ist komplex und kann den Einsatz mehrerer Tools sowie die phasenübergreifende Koordinierung von Experten bei folgenden Schritten erfordern:

+ Abrufen und Bereinigen von Daten
+ Untersuchen der Daten und Entwickeln von Modellierungsfunktionen
+ Trainieren und Optimieren des Modells
+ Bereitstellen in der Produktion

Die Entwicklung und das Testen des eigentlichen Codes werden am besten in einer dedizierten Entwicklungsumgebung durchgeführt. Nachdem das Skript vollständig getestet wurde, können Sie es jedoch problemlos in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozeduren in der vertrauten Umgebung von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] bereitstellen. Das Umbrechen von externem Code in gespeicherten Prozeduren ist der primäre Mechanismus zum Operationalisieren von Code in SQL Server.

Egal, ob Sie ein SQL-Programmierer sind, der noch nicht mit Python vertraut ist, oder ein Python-Entwickler, für den SQL neu ist: In diesem mehrteiligen Tutorial wird ein typischer Workflow für die Durchführung von datenbankinternen Analysen mit Python und SQL Server vorgestellt. 

+ [Lektion 1: Durchsuchen und Visualisieren der Daten mithilfe von Python](sqldev-py3-explore-and-visualize-the-data.md)

+ [Lektion 2: Erstellen neuer Datenfunktionen mit benutzerdefinierten SQL-Funktionen](sqldev-py4-create-data-features-using-t-sql.md)

+ [Lektion 3: Trainieren und Speichern eines Python-Modells mit T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

+ [Lektion 4: Vorhersagen potenzieller Ergebnisse mithilfe eines Python-Modells in einer gespeicherten Prozedur](sqldev-py6-operationalize-the-model.md)

Nach dem Speichern des Modells in der Datenbank für Vorhersagen können Sie es aus [!INCLUDE[tsql](../../includes/tsql-md.md)] mithilfe von gespeicherten Prozeduren aufrufen.

## <a name="prerequisites"></a>Voraussetzungen

+ [SQL Server Machine Learning Services mit Python](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Berechtigungen](../security/user-permission.md)

+ [Demodatenbank für Taxifahrten in New York City](demo-data-nyctaxi-in-sql.md)

Alle Aufgaben können mithilfe von gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozeduren in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ausgeführt werden.

Für dieses Tutorial sollten Sie sich mit grundlegenden Datenbankvorgängen auskennen, wie z. B. dem Erstellen von Datenbanken und Tabellen, dem Importieren von Daten und dem Schreiben von SQL-Abfragen. Es wird nicht davon ausgegangen, dass Sie Python kennen. Daher wird der gesamte Python-Code bereitgestellt. 

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Durchsuchen und Visualisieren der Daten mithilfe von Python](sqldev-py3-explore-and-visualize-the-data.md)
